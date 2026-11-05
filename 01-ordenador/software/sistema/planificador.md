---
titulo: "Planificador"
slug: planificador
rama: software
categoria: sistema
nivel: 8
prerequisitos: [proceso]
conduce_a: []
alias: ["planificador", "scheduler"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Planificador

## Idea central
El planificador es la parte del [[nucleo-kernel]] que, entre los [[proceso|procesos]] listos para ejecutarse, decide cuál recibe el [[procesador]] a continuación y durante cuánto tiempo. Su importancia está en el reparto: sin una política de ordenación de turnos, el procesador atendería a los procesos de forma arbitraria y algunos podrían quedar indefinidamente sin ejecutarse.

## Antes de empezar
- [[proceso]]: programa en ejecución con estado propio interrumible y reanudable, que recibe turnos de [[procesador]].

## Explicación
El planificador no crea procesos ni los ejecuta; trabaja sobre procesos ya existentes y listos, es decir, en espera de recibir el [[procesador]]. Su trabajo consiste en mantener una cola de procesos listos y aplicar sobre ella una política de ordenación: una regla que indica qué proceso sale de la cola el siguiente, en qué orden salen los demás y qué ocurre con el que ha terminado su turno. A esa regla se la llama algoritmo de planificador.

La decisión no es trivial porque los objetivos entran en tensión. Un reparto muy eficiente del [[procesador]] puede no ser justo, y un reparto muy justo puede hacer esperar demasiado a un proceso interactivo que necesita respuesta inmediata. Por eso el planificador debe elegir entre objetivos como aprovechar al máximo el [[procesador]], atender con rapidez a los procesos que acaban de llegar, no dejar a ningún proceso listo sin turno durante un tiempo excesivo y respetar prioridades cuando el sistema las define.

Para ello, el planificador divide el uso del [[procesador]] en turnos limitados. Un turno es el tiempo que un proceso concreto puede estar en ejecución antes de que el núcleo pueda retirarlo y dar paso al siguiente; en los planificadores por turno rotativo ese límite recibe el nombre de cuanto de tiempo. La existencia de un límite, y no de una ejecución hasta que el proceso quiera ceder, es lo que permite a un solo [[procesador]] servir a muchos procesos: cada uno avanza en turnos alternos y conserva su estado entre turno y turno.

Las políticas clásicas se diferencian en cómo ordenan la cola de listos. La política de primero en llegar, primero en servirse atiende a cada proceso en el orden de llegada y le deja ejecutar su turno completo; es sencilla, pero un proceso largo que llega primero puede retrasar mucho a los que vienen detrás. La política de trabajo más corto primero elige, entre los listos, al que necesita menos tiempo estimado para terminar; reduce el tiempo medio de espera, pero exige estimar ese tiempo y puede perjudicar a los procesos largos, que podrían no llegar a ejecutarse nunca si siempre aparecen procesos cortos.

La política de turno rotativo ordena la cola por llegada, pero concede a cada proceso un cuanto de tiempo y, al agotarse, lo pasa al final de la cola y atiende al siguiente; así todos los listos avanzan por turnos y ninguno monopoliza el [[procesador]] durante un turno entero. La política por prioridades ordena la cola según el valor de prioridad asignado a cada proceso y atiende primero a los de mayor prioridad; permite proteger a procesos críticos, pero, si las prioridades no se ajustan con el tiempo, los procesos de baja prioridad pueden quedar pospuestos indefinidamente. De ahí que muchos sistemas combinen políticas: por ejemplo, varias colas, una por nivel de prioridad, con turno rotativo dentro de cada nivel.

En la práctica, el planificador de un sistema concreto no es una sola de estas políticas puras, sino una combinación ajustada a su tipo de carga: sistemas interactivos valoran la rapidez de respuesta, sistemas de lote valoran el rendimiento total y sistemas de tiempo real valoran el cumplimiento de plazos. El núcleo actualiza la cola con cada llegada, cada salida y cada fin de turno, y la política es la que convierte ese conjunto de procesos listos en una secuencia concreta de turnos.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[proceso]] se define el objeto que recibe turnos: una ejecución con estado propio que puede interrumpirse y reanudarse. Esta nota da el siguiente paso: quién ordena esos turnos y con qué criterio, el planificador, que aplica una política sobre la cola de procesos listos para decidir cuál se ejecuta el siguiente y durante cuánto tiempo. Queda fuera de esta nota cómo se guarda físicamente el estado al retirar un proceso del [[procesador]] y cómo se carga el del siguiente.

## Límites de esta explicación
Esta nota no explica cómo se guarda y se restaura el estado de un proceso al cambiar de un turno a otro; eso se trata en [[cambio-de-contexto]]. Tampoco trata la creación de procesos, que corresponde a [[gestor-de-procesos]], ni el reparto de la [[memoria-ram]] entre procesos —eso corresponde a [[gestor-de-memoria]] y a [[memoria-virtual]]—, ni la estructura interna de las colas que el planificador mantiene, que se estudia en [[estructuras-de-datos]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
