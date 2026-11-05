---
titulo: "Bloque de control de proceso"
slug: bloque-de-control-de-proceso
rama: software
categoria: sistema
nivel: 8
prerequisitos: [proceso, cambio-de-contexto]
conduce_a: []
alias: ["bloque de control de proceso", "process control block", "PCB"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Bloque de control de proceso

## Idea central
El bloque de control de proceso es la ficha que el [[nucleo-kernel]] mantiene para cada [[proceso]]: una estructura en memoria del núcleo que reúne su estado de ejecución guardable, su situación frente a los turnos y los punteros que lo relacionan con su memoria y sus recursos. Sin esa ficha, el núcleo no podría saber qué proceso está listo, dónde quedó cada uno al ser retirado del [[procesador]] ni cómo reanudarlo.

## Antes de empezar
- [[proceso]]: programa en ejecución con estado propio, que puede interrumpirse y reanudarse sin perder dónde estaba.
- [[cambio-de-contexto]]: operación de guardar el contexto del proceso que se retira del [[procesador]] y cargar el del que entra.

## Explicación
En [[proceso]] se definió qué es el estado propio de una ejecución y en [[cambio-de-contexto]] cómo se salva y se restaura al pasar de un proceso a otro. Quedaba sin explicar dónde vive ese estado guardado mientras el proceso no está en el [[procesador]]: no permanece en el procesador ni dentro de la memoria del propio proceso, sino en una ficha a cargo del núcleo. Esa ficha es el bloque de control de proceso (process control block, PCB), y existe una por cada proceso, desde su creación hasta su terminación. El núcleo la crea en memoria propia, en [[espacio-de-kernel]], y no en el espacio accesible al programa, de modo que el proceso no puede alterarla por error ni de forma intencionada.

La ficha reúne, de forma resumida, todo lo que el núcleo necesita para tratar al proceso como un objeto gestionable. Primero, su identidad y situación: los datos que permiten distinguirlo de los demás procesos y el estado en que se encuentra en cada momento, es decir, si está listo para ejecutarse, si está en ejecución o si espera a que ocurra algo. Segundo, el contexto de ejecución salvado, esto es, la posición en la que quedó su avance y los valores que conservaba al ser retirado: la dirección de la próxima instrucción, los [[registros-y-unidad-de-control]] que le correspondían y los datos de su [[pila]] que se transfirieron al cambiar de contexto. Es esta parte la que el cambio de contexto escribe al retirar un proceso y lee al reanudarlo. Tercero, los punteros que relacionan la ficha con lo demás: dónde está su memoria asignada en [[memoria-virtual]], qué recursos tiene abiertos, como archivos o conexiones, y los enlaces que lo insertan en las estructuras del núcleo, por ejemplo en una cola de procesos listos, que es un caso de [[cola-fifo]] organizada según las [[estructuras-de-datos]] registradas en el libro. Cuarto, la información de gestión, como la prioridad asignada y los datos de contabilidad del tiempo usado, que el núcleo consulta para administrar los turnos sin necesidad de recordarlos fuera de la ficha.

Así, el bloque de control no es el proceso mismo ni contiene su código y sus datos: es el descriptor externo que lo representa ante el núcleo. El código, la memoria del programa y los recursos siguen estando donde el núcleo los gestiona; la ficha solo apunta a ellos y guarda el estado que no cabe en el procesador cuando el proceso está detenido. Por eso el núcleo puede localizar en un instante a cualquier proceso, saber si puede recibir el [[procesador]] y restaurar su ejecución desde el punto exacto en que quedó, sin recorrer su memoria ni reabrir sus recursos.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[proceso]] se sabía que cada ejecución posee un estado propio guardable, y desde [[cambio-de-contexto]] cómo ese estado se retira del [[procesador]] y se sustituye por otro en cada cambio. Esta nota da el paso intermedio: dónde queda ese estado entre un turno y el siguiente, en el bloque de control de proceso, la ficha en memoria del núcleo a la que el cambio de contexto escribe y desde la que lee. La decisión de a qué proceso corresponde el turno siguiente, es decir, qué criterio se aplica sobre los procesos listos y en qué orden se los atiende, no forma parte de la ficha: la toma quien ordena los turnos, tratado en [[planificador]], que para ello consulta los datos de situación y prioridad guardados aquí. Por eso esta nota no tiene un `conduce_a` propio: es la estructura de datos que hace posible tanto el cambio de contexto como la planificación.

## Límites de esta explicación
Esta nota no explica qué política sigue el núcleo para elegir el siguiente proceso ni durante cuánto tiempo le concede el [[procesador]]; eso se trata en [[planificador]]. Tampoco explica cómo se crea la ficha al nacer un proceso o cómo se destruye al terminar, lo cual queda para [[gestor-de-procesos]] y para [[cargadores]]. No detalla el contenido interno de los registros del [[procesador]], que corresponde a [[registros-y-unidad-de-control]], ni cómo se reparte la [[memoria-ram]] entre procesos, que corresponde a [[gestor-de-memoria]] y a [[memoria-virtual]]. La organización interna de las colas de procesos se estudia en [[estructuras-de-datos]].

## Referencias
- FTE-0001, Operating Systems: Three Easy Pieces, Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau: capítulos sobre procesos y bloque de control de proceso.
- FTE-0002, Modern Operating Systems, Andrew S. Tanenbaum, 4.ª edición, con Herbert Bos: capítulo sobre procesos y su descriptor en el núcleo.
