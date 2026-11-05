---
titulo: "Manejador de eventos"
slug: manejador-de-eventos
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [eventos-de-interfaz]
conduce_a: []
alias: ["manejador del evento", "respuesta", "callback"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Manejador de eventos

## Idea central
Un manejador de eventos es la función que la aplicación ejecuta cuando llega un evento de interfaz para el que estaba registrada. Sin manejadores, los [[eventos-de-interfaz]] se producirían pero nadie reaccionaría a ellos.

## Antes de empezar
- [[eventos-de-interfaz]] — notificación de que algo ha ocurrido en la pantalla o con los dispositivos de entrada y que la aplicación debe atender. Sin el evento no hay nada que responder.

## Explicación
El manejador es la respuesta concreta a un evento. Cuando la aplicación quiere reaccionar ante, por ejemplo, la pulsación de un botón, no espera pasivamente a que ocurra: registra de antemano qué función debe ejecutarse si ese evento concreto llega de ese widget concreto. Ese registro es lo que convierte un evento genérico en una reacción útil de la aplicación.

Al registrarlo, la aplicación asocia tres cosas: el origen del evento, normalmente un [[widget]], el tipo de evento que interesa, como una pulsación o la escritura de una tecla, y la función que debe ejecutarse. Esa función es el manejador, también llamado respuesta o callback. Mientras no llega nada, la aplicación sigue con el resto de su trabajo; cuando el evento llega, la función registrada se ejecuta y la aplicación reacciona, por ejemplo abriendo un menú, guardando un texto o cerrando una ventana.

El manejador recibe los datos que acompañan al evento, como el widget que lo ha originado y la posición o la tecla implicadas. Con esos datos decide qué hacer. Por eso el mismo manejador puede servir para varios widgets parecidos, y también puede haber manejadores distintos para eventos distintos sobre el mismo widget.

El registro tiene además un orden. Si varios manejadores están registrados para el mismo evento y el mismo origen, se ejecutan en el orden en que fueron registrados. Un manejador puede, por tanto, modificar el resultado del siguiente, así que registrar sin orden definido es una fuente de reacciones difíciles de prever. Por la misma razón, un registro puede cancelarse: una vez retirado, ese manejador deja de ejecutarse aunque el evento siga produciéndose.

Conviene no confundir el manejador de eventos con el [[manejo-de-interrupciones]]: aquel es una rutina de bajo nivel que atiende una señal del hardware, mientras que el manejador de eventos es una función de la aplicación que responde a una notificación ya expresada en términos de interfaz.

## Cómo se conecta con lo anterior y lo siguiente
Los [[eventos-de-interfaz]] describen el mensaje: qué ha pasado y sobre qué widget. El manejador de eventos es el paso siguiente: es la función registrada que se ejecuta al recibir ese mensaje y produce la reacción de la aplicación. Por ahora esta nota es terminal en el recorrido del libro: no conduce a un nuevo concepto enlazable, aunque el orden y la cancelación de registros ya apuntan a problemas que se tratarán cuando aparezcan las notas correspondientes.

## Límites de esta explicación
Esta nota no describe el interior de ningún widget ni cómo se dibuja en pantalla; eso pertenece a [[widget]]. Tampoco trata del mecanismo de bajo nivel con el que el sistema entrega los datos de entrada al programa; eso se trata en [[manejo-de-interrupciones]]. El orden de ejecución entre registros de distintas ventanas o de componentes superiores no se desarrolla aquí.

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces, Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau. Respalda la distinción entre notificaciones de dispositivos y mensajes dentro de la aplicación.
- [FTE-0002] Modern Operating Systems, 4ª ed., Andrew S. Tanenbaum. Respalda la idea de espera y respuesta ante eventos en programas interactivos.
