---
titulo: "Gestor de procesos"
slug: gestor-de-procesos
rama: software
categoria: sistema
nivel: 6
prerequisitos: [gestion-de-recursos]
conduce_a: []
alias: ["gestor de procesos", "process scheduler"]
estado: borrador
fuentes: []
---

# Gestor de procesos

## Idea central
El gestor de procesos es la parte de la [[gestion-de-recursos]] que decide qué programa en ejecución recibe cada turno de [[procesador]] y en qué orden. Existe porque el procesador es un recurso que solo puede ejecutar una instrucción en cada instante y conviene repartirlo sin saltos, sin olvidos y sin que una tarea bloquee a las demás.

## Antes de empezar
- [[gestion-de-recursos]]: el ciclo de solicitud, concesión, espera, uso y recuperación con que el [[nucleo-kernel]] reparte los recursos limitados, y los criterios de prioridad con que resuelve conflictos.

## Explicación
Un proceso es un programa en ejecución tal como lo ve el núcleo. Cuando un programa se pone en marcha, el núcleo lo organiza como una unidad con su propio estado de avance, de modo que puede interrumpirlo, dejarlo en espera y retomarlo después sin que el programa tenga que gestionar ese reparto. Dicha organización es la que permite que varios programas compartan un único procesador como si cada uno tuviera el suyo.

El procesador es, además, un recurso típicamente no compartible en el instante concreto: mientras ejecuta a un proceso, no puede ejecutar a otro a la vez. Por eso el gestor de procesos trabaja por turnos. En cada turno, un proceso ejecuta durante un intervalo breve y luego cede el procesador para que el núcleo elija al siguiente. La duración y la medida de esos turnos importan: si fueran demasiado largas, los demás procesos esperarían demasiado; si fueran demasiado cortas, el propio cambio de contexto —la operación de guardar el estado del proceso que cede y cargar el del que entra— consumiría más tiempo del que se ahorra. El gestor equilibra ambos extremos.

El orden de los turnos no es el orden de llegada. Al igual que en la [[gestion-de-recursos]] general, el núcleo aplica prioridades, es decir, preferencias justificadas para adelantar o retrasar a un proceso frente a otro cuando hay varios esperando el procesador. La prioridad puede tener en cuenta la importancia declarada de la tarea, el tiempo que lleva esperando o la necesidad de que todas reciban servicio en algún momento. Un criterio mal aplicado puede producir el mismo efecto que ya se vio en general: si los procesos nuevos aventajan siempre a los antiguos, alguno podría esperar indefinidamente; si un proceso retiene el procesador sin avanzar, bloquea a quien sí podría hacerlo. El gestor debe, por tanto, garantizar a la vez aprovechamiento del procesador, respeto a la prioridad y ausencia de esperas eternas.

Cabe distinguir el proceso que está ejecutándose del que está esperando el procesador y del que está esperando por otra causa, como la llegada de datos de un dispositivo. El gestor de procesos solo reparte turnos entre los que están listos para ejecutar; el que espera por un dispositivo no compite por el procesador hasta que el núcleo lo vuelve a poner en la cola de listos. Esta separación evita que el procesador evalúe a procesos que, aunque lo quisieran, no podrían avanzar todavía.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[gestion-de-recursos]] se pasa de la idea general de repartir recursos con un ciclo común y criterios de prioridad a esta nota, que aplica ese esquema al caso concreto del procesador. La concreción consiste en organizar cada programa en ejecución como proceso, partir su uso del procesador en turnos y decidir el orden de esos turnos con reglas de prioridad que eviten esperas indefinidas. Desde aquí el camino continúa en la organización del espacio de memoria de cada proceso, que no forma parte de esta nota.

## Límites de esta explicación
Esta nota no trata cómo se reparte la memoria entre procesos ni cómo se amplía el espacio disponible para cada uno; eso corresponde a [[gestor-de-memoria]] y a [[memoria-virtual]]. Tampoco trata cómo el núcleo se comunica con cada dispositivo concreto, ni cómo se implementa en un sistema concreto el cambio de contexto entre turnos. Los nombres y abreviaturas inglesas de los mecanismos de planificación quedan fuera de esta nota.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
