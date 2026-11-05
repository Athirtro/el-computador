---
titulo: "Hilos y concurrencia"
slug: hilos-concurrencia
rama: software
categoria: sistema
nivel: 8
prerequisitos: [proceso]
conduce_a: []
alias: ["hilo", "thread", "concurrencia"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Hilos y concurrencia

## Idea central
Un hilo (thread) es una unidad de ejecución menor que un [[proceso]]: es un flujo de instrucciones con su propio avance, pero que vive dentro de un proceso y comparte con sus demás hilos el código, la [[memoria-ram]] asignada y los recursos abiertos. Un proceso con varios hilos permite que una sola ejecución avance por varios frentes a la vez, y eso es la ejecución concurrente dentro de un proceso.

## Antes de empezar
- [[proceso]]: programa en ejecución con estado propio, que puede interrumpirse y reanudarse sin perder dónde estaba, y que el núcleo reparte por turnos de [[procesador]].

## Explicación
El [[proceso]] descrito en la nota anterior es la unidad completa que el [[nucleo-kernel]] gestiona: código más estado. Dentro de un proceso puede haber, además, una división interna de la ejecución. En lugar de un único punto de avance, el proceso contiene varios hilos, cada uno con su propio punto de ejecución, su propio estado de avance —los valores que va acumulando y donde está dentro del código— y su propia [[pila]], donde guarda el historial de llamadas pendientes y sus variables locales.

Lo que los hilos de un mismo proceso comparten es justamente lo que define al proceso como contenedor: el mismo código, la misma zona de memoria asignada a esa ejecución y los mismos recursos ya abiertos, como archivos o conexiones. Por eso dos hilos del mismo proceso ven y pueden modificar los mismos datos en memoria, mientras que dos procesos distintos no comparten esa memoria por defecto. Cada hilo, en cambio, avanza por separado: puede estar en espera, listo o ejecutándose sin que su avance arrastre al de los demás hilos, aunque su compartición de memoria hace que lo que uno escribe pueda ser leído por otro.

El [[planificador]] trata entonces a cada hilo como una unidad ejecutable con la que alternar, y el mecanismo de [[cambio-de-contexto]] guarda y restaura el estado propio de cada hilo al pasar de uno a otro. Si hay un solo [[procesador]], la concurrencia es aparente: los hilos se intercalan por turnos tan rápido que se comportan como si avanzaran a la vez. Si hay varios procesadores, distintos hilos del mismo proceso pueden ejecutarse literalmente a la vez en procesadores distintos sin dejar de compartir la memoria del proceso. En ambos casos, la condición de que compartan memoria distingue a los hilos de los procesos: la concurrencia entre hilos es concurrencia dentro de un mismo contenedor.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[proceso]] se sabía que el núcleo interrumpe y reanuda ejecuciones con estado propio, repartiendo el [[procesador]] entre procesos. Esta nota da el paso siguiente hacia dentro: dentro de un único proceso pueden existir varias unidades de ejecución, los hilos, que comparten su memoria y recursos pero alternan turnos entre sí mediante [[planificador]] y [[cambio-de-contexto]]. Queda así definida la unidad menor de ejecución; qué se hace con varios procesos que compiten entre sí queda fuera de este peldaño.

## Límites de esta explicación
Esta nota no trata la concurrencia entre procesos distintos ni la organización general de varios programas a la vez; eso corresponde a [[multitarea]]. Tampoco explica cómo se resuelven los conflictos derivados de que los hilos compartan memoria y puedan pisarse el trabajo mutuamente, ni cómo se sincronizan entre sí, que es materia de una nota posterior. Y no detalla por qué criterio el [[planificador]] elige un hilo frente a otro; eso se trata en [[planificador]].

## Referencias
- FTE-0001 (OSTEP): modelo de hilos como flujos de ejecución dentro de un proceso, que comparten el espacio de direcciones, la memoria y los recursos del proceso, con pila y registros propios, y planificación e intercalado entre hilos.
- FTE-0002 (Tanenbaum, *Modern Operating Systems*): distinción entre proceso e hilo, uso compartido de memoria por los hilos de un proceso y concurrencia de hilos en uno o varios procesadores.
