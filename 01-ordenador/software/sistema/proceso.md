---
titulo: "Proceso"
slug: proceso
rama: software
categoria: sistema
nivel: 7
prerequisitos: [gestor-de-procesos]
conduce_a: [planificador, cambio-de-contexto]
alias: ["proceso", "process"]
estado: borrador
fuentes: []
---

# Proceso

## Idea central
Un proceso (process) es un programa en ejecución tal como lo ve y lo gestiona el [[nucleo-kernel]]: no es solo el código, sino el código junto con todo el estado que necesita para avanzar y poder interrumpirse y reanudarse sin perder dónde estaba. Sin esta separación entre código guardado y ejecución con estado propio, el [[gestor-de-procesos]] no podría repartir el [[procesador]] entre varios programas sin que se estorbaran.

## Antes de empezar
- [[gestor-de-procesos]]: la parte de la [[gestion-de-recursos]] que reparte turnos de [[procesador]] entre programas en ejecución, con prioridades y con la distinción entre proceso listo para ejecutar, ejecutándose y esperando por otra causa.

## Explicación
Un programa es un conjunto de instrucciones guardado, por ejemplo en un archivo, que todavía no hace nada por sí solo. Para que haga algo, el [[nucleo-kernel]] crea una instancia de ejecución de ese programa, es decir, un proceso. Esa instancia añade al código todo lo que el código necesita mientras avanza: el lugar exacto de la ejecución en que se encuentra, los valores que va acumulando, la zona de [[memoria-ram]] asignada a esa ejecución y los recursos que ya tiene abiertos, como archivos o conexiones. Cuando el proceso se interrumpe, ese conjunto de valores y de posiciones se conserva, y al reanudarse la ejecución continúa desde ahí en lugar de empezar de nuevo.

Ese estado propio es lo que hace posible la interrupción y la reanudación. Que el proceso sea interrumpible no significa que se interrumpa donde le dé la gana, sino que el núcleo puede detenerlo al terminar su turno, guardar su estado y dejarlo en espera, para después volver a darle el [[procesador]] y retomar la ejecución como si no hubiera pasado el tiempo. En ese intervalo, el código del programa no cambia; lo que cambia es el avance dentro de ese código. Por eso dos procesos nacidos del mismo programa son distintos: comparten el código de origen, pero cada uno tiene su propio avance, su propia [[memoria-ram]] asignada y sus valores acumulados, y avanzan de forma independiente.

La existencia de este estado propio obliga a distinguir lo que hace el proceso de lo que decide el núcleo sobre él. El proceso es la unidad que se ejecuta y se suspende; el núcleo es quien decide cuándo ejecutar, a cuál y durante cuánto tiempo. Dicha decisión no forma parte de la definición de proceso, aunque la hace posible: sin estado guardable no habría turnos ni reanudación limpia. Así, el proceso queda definido como el objeto gestionable, y el reparto concreto de turnos como una decisión posterior del núcleo sobre esos objetos.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[gestor-de-procesos]] se entendía el reparto de turnos de [[procesador]] entre programas en ejecución, con prioridades y con procesos listos y procesos en espera. Esta nota da el siguiente paso: define qué es exactamente eso que recibe turnos, el proceso, como programa en ejecución con estado propio que puede interrumpirse y reanudarse. Una vez definido el objeto, queda por explicar quién elige el turno siguiente y cómo se guarda y se restaura el estado al pasar de un proceso a otro; eso corresponde a [[planificador]] y a [[cambio-de-contexto]].

## Límites de esta explicación
Esta nota no explica qué criterio usa el núcleo para elegir el siguiente proceso ni en qué orden atiende a los que esperan; eso se trata en [[planificador]]. Tampoco explica cómo se guarda físicamente el estado al retirar un proceso del [[procesador]] y cómo se carga el del siguiente; eso se trata en [[cambio-de-contexto]]. No trata cómo se reparte la [[memoria-ram]] entre procesos —eso corresponde a [[gestor-de-memoria]] y a [[memoria-virtual]]— ni cómo se crea un proceso a partir de un programa concreto, lo cual queda para [[cargadores]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
