---
titulo: "Cambio de contexto"
slug: cambio-de-contexto
rama: software
categoria: sistema
nivel: 8
prerequisitos: [proceso]
conduce_a: []
alias: ["cambio de contexto", "context switch"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Cambio de contexto

## Idea central
El cambio de contexto es la operación por la que el [[nucleo-kernel]] retira un [[proceso]] del [[procesador]] y pone otro en su lugar, guardando el estado de ejecución del primero y cargando el del segundo. Gracias a él, varios procesos parecen avanzar a la vez aunque solo haya una ejecución en curso en cada instante, y cada uno puede reanudarse después exactamente donde quedó.

## Antes de empezar
- [[proceso]]: un programa en ejecución con estado propio —posición de ejecución, valores acumulados, memoria asignada y recursos abiertos— que puede interrumpirse y reanudarse sin perder dónde estaba.

## Explicación
Un [[proceso]] no puede estar presente en el [[procesador]] de forma continua sin los demás, porque el procesador solo ejecuta una secuencia de instrucciones a la vez en cada núcleo. El estado que define esa secuencia vive en gran parte dentro del procesador: en los [[registros-y-unidad-de-control]], es decir, en las celdas internas que conservan, entre otros datos, la dirección de la próxima instrucción que hay que ejecutar. Si el núcleo simplemente dejara de ejecutar un proceso y empezara a ejecutar otro sin guardar esos datos, el primero perdería su posición y sus valores al volver, y la reanudación sería imposible.

El cambio de contexto resuelve eso tratando el paso de un proceso a otro como dos operaciones encadenadas. Primero, el núcleo salva el contexto del proceso que se retira: la dirección de la próxima instrucción, los registros generales y de estado, y el puntero que señala la cima de su [[pila]], la zona de memoria donde guarda las llamadas pendientes. Esa información no se copia en su totalidad desde la memoria del proceso, sino que se transfiere desde el procesador a las estructuras del núcleo asociadas a ese proceso, donde queda conservada mientras el proceso espera. Después, el núcleo carga el contexto guardado del proceso que entra: restaura sus registros y su puntero de pila y ordena al procesador continuar desde la dirección que ese proceso dejó pendiente.

Este mecanismo no guarda todo lo que pertenece al proceso. El código del programa, los datos de su memoria asignada y los recursos abiertos, como archivos o conexiones, no se copian ni se pierden al cambiar de contexto; permanecen donde están y siguen gestionados por el núcleo. Lo que cambia es únicamente la ejecución visible en el procesador: qué instrucciones se ejecutan ahora y con qué valores de registros. Cuando el procesador pasa de un espacio de memoria a otro, además, puede necesitar cambiar la base de traducción de direcciones visible, pero qué significa ese espacio de direcciones y cómo se reparte la memoria corresponden a [[memoria-virtual]] y no a esta operación en sí.

El cambio puede producirse de forma voluntaria, cuando el proceso que se ejecuta cede el procesador porque queda a la espera de algo, o de forma involuntaria, cuando el núcleo lo retira al acabarse su turno o al producirse una interrupción. En ambos casos el procedimiento de guardar y cargar es el mismo; lo que cambia es la circunstancia que lo provoca. Durante la operación el núcleo actúa en el modo privilegiado del sistema y protege la secuencia frente a nuevas interrupciones, para que ningún proceso a medio salvar o a medio cargar quede en un estado incoherente.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[proceso]] se sabía que cada ejecución posee un estado propio, guardable, que permite interrumpirla y reanudarla. Esta nota explica el mecanismo concreto por el que ese estado se retira del [[procesador]] y se sustituye por otro: salvar el contexto saliente y cargar el contexto entrante. La decisión de a qué proceso corresponde el turno siguiente —qué criterio se usa y en qué orden se atiende a los que esperan— no forma parte de este mecanismo; la toma quien ordena los turnos, tratado en [[planificador]], que invoca el cambio de contexto cuando actúa. Por eso esta nota no tiene un `conduce_a` propio: es el mecanismo que hace posible el turno que el planificador decide.

## Límites de esta explicación
Esta nota no explica qué política sigue el núcleo para elegir el siguiente proceso ni durante cuánto tiempo le concede el procesador; eso se trata en [[planificador]]. Tampoco explica cómo se provocan los cambios involuntarios ni qué ocurre con las interrupciones del procesador, que corresponden a [[interrupciones]] y a [[llamadas-al-sistema]]. No detalla el contenido interno de los registros del procesador, lo cual corresponde a [[registros-y-unidad-de-control]], ni el reparto de la memoria entre procesos, que corresponde a [[gestor-de-memoria]] y a [[memoria-virtual]]. Tampoco trata cómo se crea el contexto inicial de un proceso nuevo al nacer, que queda para [[cargadores]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
