---
titulo: "Estado de proceso"
slug: estado-de-proceso
rama: software
categoria: sistema
nivel: 7
prerequisitos: [proceso]
conduce_a: []
alias: ["estado de proceso", "process state"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Estado de proceso

## Idea central
El estado de proceso es la situación en que se encuentra un [[proceso]] respecto del [[procesador]] en cada instante: listo para ejecutarse, ejecutándose en ese momento o bloqueado a la espera de algo ajeno a la ejecución. Sin esta distinción, el [[nucleo-kernel]] no podría repartir el [[procesador]] entre varios procesos ni suspender y reanudar cada uno en el punto exacto en que lo dejó.

## Antes de empezar
- [[proceso]]: programa en ejecución con estado propio, que puede interrumpirse y reanudarse sin perder dónde estaba.

## Explicación
Un proceso no puede estar siempre ocupando el [[procesador]]. Con varios procesos conviviendo, cada uno está en una sola situación en cada instante, y de esa situación depende lo que el [[nucleo-kernel]] puede hacer con él. Por eso el núcleo mantiene, para cada proceso, un estado que resume su relación con el [[procesador]] y con el resto del sistema: si puede recibir el [[procesador]] ahora, si lo está usando, o si debe esperar hasta que ocurra algo que no controla por sí mismo.

El estado de listo describe a un proceso creado y preparado para ejecutarse, pero que todavía no tiene el [[procesador]] asignado. Está esperando su turno, con todo lo necesario para empezar en cuanto el núcleo se lo conceda. El estado de ejecución describe a un proceso que en ese instante sí está usando el [[procesador]] y avanzando en sus instrucciones. En un mismo [[procesador]] solo puede haber un proceso en este estado a la vez; los demás procesos que quieren ejecutarse deben estar en listo.

El estado de bloqueado describe a un proceso que no podría avanzar aunque recibiera el [[procesador]], porque espera algo externo a la ejecución. El caso típico es esperar el resultado de una petición al núcleo, como leer datos de un dispositivo o de un archivo, o esperar la terminación de otro proceso. Mientras el proceso está bloqueado, el núcleo no tiene sentido en darle el [[procesador]]: lo mantiene fuera de la cola de candidatos y solo lo devuelve a listo cuando llega el acontecimiento que estaba esperando.

Los tres estados se suceden por transiciones. Un proceso pasa de listo a ejecución cuando el núcleo le asigna el [[procesador]]; de ejecución a listo cuando termina su turno y lo suspende, conservando su estado propio para reanudarlo después; de ejecución a bloqueado cuando hace una petición que no puede resolver de inmediato y debe esperar; y de bloqueado a listo cuando llega el acontecimiento esperado, volviendo a competir por el [[procesador]]. El estado no es una propiedad del programa guardado, sino de la ejecución concreta: dos procesos del mismo programa pueden estar en estados distintos a la vez, y el mismo proceso cambia de estado a lo largo de su vida.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[proceso]] se define el objeto que recibe turnos de [[procesador]]: un programa en ejecución con estado propio, interrumpible y reanudable. Esta nota da el paso siguiente: explica en qué situación puede estar ese objeto en cada instante y qué significa cada situación para el núcleo. Por eso el estado se guarda en la ficha del proceso, descrita en [[bloque-de-control-de-proceso]], y es el dato que el núcleo consulta al decidir qué hacer con cada proceso. Quien decide cuándo asignar el [[procesador]] y según qué criterio es el [[planificador]], y cómo se conserva el resto del estado al pasar de un proceso a otro es el [[cambio-de-contexto]]; ninguno de los dos forma parte de esta nota.

## Límites de esta explicación
Esta nota no explica qué criterio usa el núcleo para elegir el siguiente proceso entre los que están en listo, ni en qué orden los atiende; eso se trata en [[planificador]]. Tampoco explica cómo se guarda físicamente el estado al retirar un proceso del [[procesador]] y cómo se carga el del siguiente; eso se trata en [[cambio-de-contexto]]. No trata la estructura de la ficha donde se registra el estado; eso corresponde a [[bloque-de-control-de-proceso]]. Las situaciones de creación y de terminación de un proceso quedan fuera del alcance asignado a esta nota y no se desarrollan aquí.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): estados de listo, ejecución y bloqueo y sus transiciones.
- FTE-0002 (Modern Operating Systems, 4.ª ed., Tanenbaum): estados de listo, ejecución y bloqueo y sus transiciones.
