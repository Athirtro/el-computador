---
titulo: "Manejo de interrupciones"
slug: manejo-de-interrupciones
rama: software
categoria: sistema
nivel: 8
prerequisitos: [interrupciones]
conduce_a: []
alias: ["manejador de interrupciones", "rutina de interrupción", "interrupt handler"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Manejo de interrupciones

## Idea central
El manejo de interrupciones es la ejecución en el [[nucleo-kernel]] de la rutina preparada para atender cada tipo de aviso del hardware, seguida de la restauración del trabajo suspendido. Permite que un acontecimiento urgente se atienda sin esperar a que el programa en curso ceda el control y sin que el procesador evalúe periódicamente si el dispositivo tiene novedades.

## Antes de empezar
- [[interrupciones]]: señal del hardware que obliga al procesador a suspender su trabajo y transferir el control al núcleo.

## Explicación
Cuando el procesador recibe una interrupción, deja de ejecutar el programa en curso, conserva el estado necesario para poder reanudarlo y pasa a [[modo-privilegiado]] para ejecutar la rutina de atención correspondiente. Esa rutina es un código del núcleo preparado antes para ese tipo concreto de acontecimiento: distingue qué dispositivo o qué temporizador originó el aviso, realiza el trabajo mínimo indispensable —leer o almacenar el dato de un dispositivo, liberar un temporizador cumplido, marcar un evento para su atención posterior— y devuelve el control con el estado guardado restaurado.

La rutina no se ejecuta como un programa normal. Un programa normal trabaja en [[modo-no-privilegiado]] y puede bloquearse esperando un recurso; la rutina que atiende una interrupción se ejecuta en privilegiado, no espera a que otro proceso ceda el procesador y debe actuar con rapidez. Por eso el núcleo suele limitar su trabajo: atiende lo urgente y deja el resto para una ejecución posterior. Si la rutina tardase o esperase, el procesador dejaría de atender los demás avisos en el momento en que ocurren y el sistema perdería la respuesta que justifica el mecanismo.

La prioridades ordenan cómo coexisten las rutinas. Cada tipo de interrupción tiene asignada una prioridad: las de mayor prioridad interrumpen a las de menor, y las de menor esperan a que las superiores terminen. Así, el aviso de un temporizador que reparte el procesador no se retrasa por una tarea menos urgente del núcleo, y una interrupción crítica no queda bloqueada detrás de otra rutinaria. El núcleo puede además enmascarar —inhibir temporalmente— las interrupciones de prioridad menor mientras ejecuta una sección que no debe ser interrumpida, y desenmascararlas al terminar. Las prioridades no cambian qué rutina se ejecutará ante cada aviso; determinan cuál se atiende primero cuando coinciden.

La restauración cierra el manejo. Una vez atendida la causa, el procesador recupera el estado conservado y continúa la ejecución suspendida. Si la interrupción provino de un temporizador, el núcleo puede en ese momento entregar el procesador a otro programa, lo que se trata en [[planificador]]. El resto de los dispositivos tiene sus rutinas dentro de sus [[controladores-drivers]], que son los componentes del núcleo encargados de atender cada hardware concreto.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[interrupciones]] se sabe que el hardware obliga al procesador a suspender su trabajo y ceder el control al núcleo. Esta nota explica qué ocurre después de esa cesión: se ejecuta en privilegiado la rutina preparada para el aviso, se respetan las prioridades entre rutinas y se restaura el trabajo suspendido. El mecanismo completa así la repetición con que el núcleo recupera el control sin depender de que los programas cooperen, que es la base de la respuesta continua de [[gestion-de-recursos]]. No hay peldaño siguiente asignado: esta nota cierra el recorrido de la entrega del control.

## Límites de esta explicación
Esta nota no detalla qué registros guarda el procesador al suspender su trabajo ni cómo se organiza internamente la transferencia del control. Tampoco explica cómo el núcleo decide qué programa recibe el procesador tras una interrupción por temporizador; eso se trata en [[planificador]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): interrupciones por dispositivo y por temporizador; atención mediante rutina del núcleo y recuperación del control.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): interrupciones, prioridades y atención en modo privilegiado con restauración del trabajo suspendido.
