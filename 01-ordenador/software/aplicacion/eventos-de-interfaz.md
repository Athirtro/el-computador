---
titulo: "Eventos de interfaz"
slug: eventos-de-interfaz
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [widget]
conduce_a: []
alias: ["evento de interfaz", "evento"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Eventos de interfaz

## Idea central
Un evento de interfaz es una notificación de que algo ha ocurrido en la pantalla o con los dispositivos de entrada, y que la aplicación debe atender. Sin eventos, la aplicación no sabría cuándo el usuario ha pulsado un botón, escrito una tecla o ha cambiado el tamaño de la ventana.

## Antes de empezar
- [[widget]] — elemento visual e interactivo de una aplicación (botón, campo de texto, menú, ventana). Sin este elemento no hay nada que pueda recibir una acción del usuario.

## Explicación
Un widget muestra información y ofrece una acción: pulsar, escribir, arrastrar o elegir. Pero mostrar no basta. La aplicación necesita enterarse de que el usuario ha actuado, y de qué ha hecho exactamente.

El evento es el mensaje que lleva esa información. Un clic sobre un botón no es solo un cambio de color en pantalla: es un evento que indica qué widget lo ha originado, qué botón se ha pulsado, en qué posición y en qué momento. Lo mismo ocurre con una tecla, un gesto táctil o el redibujado de una ventana tras moverla. Cada tipo de evento responde a una pregunta distinta: qué ha pasado y sobre qué widget.

La aplicación no recibe estos mensajes al azar. Los escucha. Escuchar significa registrar de antemano qué función debe ejecutarse cuando llegue un evento concreto de un widget concreto. Esa función es el manejador del evento, también llamado respuesta o *callback* en inglés. Mientras no llega nada, la aplicación espera; cuando llega el evento, se ejecuta la función registrada y la aplicación reacciona, por ejemplo abriendo un menú o guardando un texto.

Hay que distinguir el evento de interfaz de otros mecanismos de notificación. Una [[interrupciones|interrupción]] es una señal del hardware que suspende la ejecución para atender un dispositivo; el evento de interfaz es una notificación dentro de la aplicación, ya en el nivel del usuario. Una [[llamadas-al-sistema|llamada al sistema]] es una petición del programa al núcleo; el evento va en dirección contraria, desde la acción del usuario hacia la aplicación.

## Cómo se conecta con lo anterior y lo siguiente
El [[widget]] es el origen visible: sin él no hay acción posible. El evento es el paso siguiente: convierte la acción física del usuario en un mensaje que la aplicación puede tratar. A partir de aquí, la aplicación decide qué hacer, pero ese paso a un nuevo peldaño quedaría fuera de esta nota.

## Límites de esta explicación
Esta nota no describe el interior de cada widget ni cómo se dibuja en pantalla; eso pertenece a [[widget]]. Tampoco trata de los mecanismos de bajo nivel con los que el sistema entrega los datos de entrada al programa; esos se tratan en [[interrupciones]] y [[llamadas-al-sistema]].

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces, Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau. Respalda la distinción entre notificaciones de dispositivos y mensajes dentro de la aplicación.
- [FTE-0002] Modern Operating Systems, 4ª ed., Andrew S. Tanenbaum. Respalda la idea de espera y respuesta ante eventos en programas interactivos.
