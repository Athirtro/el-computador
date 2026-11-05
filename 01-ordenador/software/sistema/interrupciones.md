---
titulo: "Interrupciones"
slug: interrupciones
rama: software
categoria: sistema
nivel: 7
prerequisitos: [llamadas-al-sistema]
conduce_a: []
alias: ["interrupt"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Interrupciones

## Idea central
Una interrupción es una señal del hardware que obliga al procesador a suspender lo que hace y entregar el control al núcleo, para volver a su tarea cuando termina el servicio. Es el mecanismo físico con el que el núcleo recupera el control sin que el programa que ejecuta le ceda la palabra.

## Antes de empezar
- [[llamadas-al-sistema]]: la petición ordenada con que un programa solicita un servicio al núcleo y le entrega el control de forma prevista.

## Explicación
En [[llamadas-al-sistema]] la entrega del control parte del propio programa: este solicita un servicio y el núcleo lo atiende. La interrupción invierte esa iniciativa. Quien la provoca no es el programa en ejecución, sino el hardware: un dispositivo que necesita atención o un temporizador que ha cumplido su plazo. El procesador no puede ignorarla sin dejar de cumplir su función, porque el acontecimiento que la origina es ajeno a la secuencia de instrucciones que estaría ejecutando.

El mecanismo de entrega funciona así. Cuando llega la señal, el procesador interrumpe la ejecución en curso, guarda el estado necesario para poder reanudarla después, y transfiere el control a una rutina del núcleo preparada para atender ese tipo concreto de acontecimiento. Esa rutina atiende la causa —recoge los datos de un dispositivo, por ejemplo— y, al terminar, el procesador recupera el estado guardado y continúa donde estaba. La interrupción no crea un programa nuevo ni sustituye al que se ejecutaba: lo suspende temporalmente y lo reanuda.

Dos orígenes cubren los casos esenciales. La interrupción por dispositivo la emite un periférico cuando tiene algo que comunicar: un teclado con una tecla pulsada, una tarjeta de red con datos recibidos o un disco que ha terminado de leer. Sin ella, el procesador tendría que preguntar continuamente si el dispositivo tiene algo nuevo, desperdiciando su trabajo; con ella, el dispositivo avisa solo cuando hace falta. La interrupción por temporizador la emite un reloj interno a intervalos fijados por el núcleo. Gracias a ella el núcleo recupera periódicamente el control aunque el programa en ejecución no se lo ceda, lo que permite repartir el procesador entre varios programas en lugar de dejarlo en manos de uno solo.

La interrupción se distingue de la llamada al sistema en tres rasgos. Es asíncrona: no ocurre en un punto previsto del programa, sino en el momento en que el hardware lo decide. Es externa en su origen: la provoca un dispositivo o un temporizador, no el programa. Y no la solicita quien ejecuta: el procesador la obedece porque el hardware la impone. Precisamente por eso la llamada al sistema necesita apoyarse en ella: la petición de un programa utiliza el mismo camino de entrega del control que el hardware reserva para los acontecimientos urgentes.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[llamadas-al-sistema]] se sabe que el programa entrega el control al [[nucleo-kernel]] de forma ordenada para pedirle un servicio. Esta nota muestra el mecanismo hardware que hace posible esa entrega: el procesador suspende su trabajo, cede el control al núcleo y lo recupera al terminar. La misma vía sirve para los acontecimientos que nadie ha solicitado: el aviso de un dispositivo o el plazo de un temporizador vienen por ella, y por eso el núcleo puede vigilar los recursos de forma continua en [[gestion-de-recursos]]. No hay peldaño siguiente asignado: esta nota cierra el recorrido de la entrega del control.

## Límites de esta explicación
Esta nota no detalla qué registros guarda el procesador al suspender su trabajo ni cómo se organiza internamente la transferencia del control; eso pertenece a la capa de procesador y se trata en [[registros-y-unidad-de-control]]. Tampoco explica cómo el núcleo decide qué programa recibe el procesador tras una interrupción por temporizador; eso se trata en [[gestion-de-recursos]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
