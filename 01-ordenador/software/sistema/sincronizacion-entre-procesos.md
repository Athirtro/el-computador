---
titulo: "Sincronización entre procesos"
slug: sincronizacion-entre-procesos
rama: software
categoria: sistema
nivel: 10
prerequisitos: [sincronizacion-de-hilos]
conduce_a: []
alias: ["coordinación entre procesos", "interprocess synchronization"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Sincronización entre procesos

## Idea central
La sincronización entre procesos son las reglas que coordinan a procesos distintos, que no comparten memoria por defecto, cuando necesitan intercambiar datos o repartirse un recurso común. La diferencia clave respecto a los hilos es que el núcleo actúa como intermediario: ofrece los canales y los cerrojos, y garantiza que el acceso se produzca de forma ordenada.

## Antes de empezar
- [[sincronizacion-de-hilos]]: exclusión mutua, región crítica, cerrojo, semáforo y espera con aviso para hilos que comparten memoria dentro de un mismo [[proceso]].

## Explicación
Cada [[proceso]] dispone de su propio espacio de direcciones virtuales, aislado del de los demás, de modo que un proceso no puede leer ni escribir directamente la memoria de otro. Esa separación protege a los procesos entre sí, pero hace imposible la solución más simple de los hilos, donde todos tocan las mismas variables. Si dos procesos han de compartir un resultado, un contador o un archivo, la ordenación de sus accesos debe organizarse a través de un recurso que el núcleo administra para ambos.

De ahí nace el cambio de escala. Con hilos, el problema era que varios flujos intercalados accedieran a un dato común; con procesos, el problema es coordinar la actividad de programas completos y aislados que solo se relacionan mediante lo que el núcleo les permite compartir. Excluir sigue siendo necesario: si dos procesos escriben sin orden en el mismo canal compartido, el resultado depende de cuál acabe antes y puede corromperse igual que en el caso de los hilos. La región crítica ya no está en una variable compartida, sino en el recurso común mediado por el núcleo, pero la exigencia es idéntica, que solo un proceso acceda a él en cada momento.

Los mecanismos se apoyan en la misma idea que los cerrojos y semáforos de hilos, pero ejecutados por el núcleo y alcanzados mediante [[llamadas-al-sistema]]. El núcleo concede el acceso, bloquea al proceso que espera y lo despierta cuando el recurso queda libre u ocurre el hecho aguardado, como la llegada de datos producidos por otro proceso. Por eso la coordinación entre procesos también incluye ordenar el avance, no solo excluir el acceso simultáneo: un proceso que produce un resultado puede detenerse hasta que otro proceso lo consume, o esperar a que otro termine una tarea antes de continuar.

Conviene no confundir el cambio de contexto con sincronización. El [[planificador]] decide qué proceso usa la [[cpu]] en cada momento, pero no quién tiene derecho a acceder a un recurso compartido ni en qué orden deben producirse los intercambios. Coordinar es, precisamente, imponer ese orden por encima de la intercalación libre que la multitarea introduce.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sincronizacion-de-hilos]] se sabía cómo coordinar a quienes comparten memoria dentro de un mismo proceso, con el núcleo durmiendo y despertando a los hilos en espera. Esta nota da el paso a procesos distintos: al quedar aislados en espacios de memoria separados, el mismo objetivo, exclusión mutua y avance ordenado, debe alcanzarse a través de recursos que administra el núcleo y de peticiones explícitas a este. El peldaño cubre así la coordinación cuando la memoria compartida deja de ser directa y pasa a ser un canal mediado.

## Límites de esta explicación
Esta nota no detalla qué ocurre cuando los procesos que se coordinan se bloquean mutuamente esperando cada uno un recurso que tiene el otro, como tampoco detalla la implementación interna de los canales que el núcleo ofrece para compartir datos o de los cerrojos que administra entre procesos, ni la coordinación de procesos que se ejecutan en ordenadores distintos conectados por una red. Esos temas requieren notas propias posteriores.

## Referencias
- FTE-0001 (OSTEP): necesidad de exclusión mutua y mecanismos de cerrojo, semáforo y espera con aviso cuando varios flujos de ejecución comparten datos; el papel del sistema operativo como árbitro al bloquear y despertar a los que esperan.
- FTE-0002 (Tanenbaum, *Modern Operating Systems*): aislamiento entre procesos, coordinación entre procesos distintos a través del núcleo y uso de primitivas que el sistema ofrece para excluir y ordenar accesos a recursos compartidos.
