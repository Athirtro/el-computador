---
titulo: "Interbloqueo"
slug: interbloqueo
rama: software
categoria: sistema
nivel: 10
prerequisitos: [sincronizacion-de-hilos]
conduce_a: []
alias: ["deadlock", "bloqueo mutuo"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Interbloqueo

## Idea central
El interbloqueo (deadlock) es una situación en la que dos o más hilos quedan bloqueados para siempre porque cada uno retiene un recurso que el otro necesita para poder liberar el suyo. No es una espera temporal: es un círculo de esperas del que ningún hilo puede salir por sí mismo.

## Antes de empezar
- [[sincronizacion-de-hilos]]: los hilos que comparten memoria necesitan exclusión mutua mediante cerrojos para no pisarse, y esos cerrojos dejan a quien los pide en espera hasta que otro los libera.

## Explicación
La sincronización introduce un riesgo nuevo. Cada cerrojo concede acceso a un solo hilo y hace esperar a los demás, lo cual es correcto cuando la espera es breve y termina. El problema aparece cuando un hilo retiene un cerrojo mientras solicita otro. Si dos hilos hacen eso en orden contrario, cada uno posee un recurso que el otro necesita, y ninguno puede avanzar: el primero no puede terminar porque espera el segundo cerrojo, y el segundo no puede terminar porque espera el primero. Los dos quedan detenidos aunque el procesador siga libre, porque no queda ningún hilo listo para ejecutarse en ese grupo.

A ese patrón se le llama espera circular: las dependencias de espera forman un ciclo, de modo que cada hilo espera al siguiente y el último espera al primero. La circularidad es la señal que distingue un interbloqueo de una espera normal. Un hilo que espera porque otro aún trabaja no está interbloqueado, porque el otro avanzará y lo liberará; el interbloqueo solo existe cuando toda la cadena de esperas se cierra sobre sí misma y no queda ningún hilo capaz de romperla.

Para que el círculo se forme hacen falta varias condiciones a la vez. Debe haber exclusión mutua, es decir, un recurso que solo admite un poseedor en cada momento; retención y espera, es decir, un hilo que conserva lo que tiene mientras pide más; y ausencia de expulsión, es decir, nadie puede quitarle a un hilo lo que retiene para entregárselo a otro. Si una sola de esas condiciones falla, el ciclo no puede cerrarse. Por eso el interbloqueo no se detecta mirando un hilo aislado, sino mirando cómo se enlazan las esperas de todos: si el grafo de dependencias contiene un ciclo, hay interbloqueo; si no lo contiene, las esperas terminarán tarde o temprano.

Conviene distinguirlo de otros fallos de concurrencia. A diferencia de la condición de carrera, que produce resultados incorrectos pero siempre avanza, aquí el sistema se detiene: no hay error de cálculo, hay ausencia total de progreso. Y a diferencia de un hilo que simplemente no llega a ejecutarse por falta de turnos, en el interbloqueo los hilos están bloqueados por sus propias dependencias, no por decisión del planificador.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sincronizacion-de-hilos]] se venía de que los cerrojos resuelven la exclusión mutua pero obligan a esperar. Esta nota da el paso siguiente: si las esperas se combinan en círculo, la sincronización deja de proteger y pasa a detener el sistema. Por eso el cerrojo, que era la solución, se convierte también en la causa del interbloqueo. La nota cierra esta rama: las estrategias para impedir que el círculo se forme o para romperlo cuando ya existe requieren tratamiento propio posterior.

## Límites de esta explicación
Esta nota no desarrolla los métodos para prevenir o detectar el interbloqueo, ni la recuperación cuando ya ha ocurrido; eso queda para notas posteriores. Tampoco repite los mecanismos generales de sincronización, que corresponden a [[sincronizacion-de-hilos]], ni trata el reparto de procesador entre procesos, que corresponde a [[multitarea]].

## Referencias
- FTE-0001 (OSTEP): definición de interbloqueo, condiciones necesarias y espera circular entre hilos que retienen recursos bloqueantes.
- FTE-0002 (Tanenbaum, *Modern Operating Systems*): caracterización del interbloqueo como bloqueo permanente por dependencias circulares de recursos.
