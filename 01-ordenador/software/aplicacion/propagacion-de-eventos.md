---
titulo: "Propagación de eventos"
slug: propagacion-de-eventos
rama: software
categoria: aplicacion
nivel: 8
prerequisitos: [eventos-de-interfaz]
conduce_a: []
alias: ["propagación del evento", "event bubbling"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Propagación de eventos

## Idea central
La propagación de eventos es el recorrido de un evento por la jerarquía de controles que contienen al widget que lo originó. Permite que un contenedor reaccione a lo que ocurre en sus elementos sin que cada elemento tenga que repetir esa reacción.

## Antes de empezar
- [[eventos-de-interfaz]] — notificación de que algo ha ocurrido sobre un widget y de que la aplicación debe atenderla. Sin el evento no hay nada que propagar.

## Explicación
Los widgets no aparecen sueltos en la pantalla. Un botón está dentro de un panel, el panel dentro de una [[ventana]] y, en interfaces más complejas, un widget puede contener a otros. Esa organización del contenedor y de lo contenido forma una jerarquía: una cadena de padre e hijo que va del control más interno a la ventana que lo contiene.

Cuando ocurre un evento, no se entrega solo al widget sobre el que el usuario actuó. Se ofrece primero a ese widget, que es su destino inicial. Si ese widget no tiene registrado un [[manejador-de-eventos]] para ese tipo de evento, o si su manejador decide no dar el evento por atendido, el evento sube al widget que lo contiene. Allí se le ofrece de nuevo y, si tampoco se atiende, vuelve a subir. Este ascenso paso a paso por la jerarquía es el burbujeo (*event bubbling*): el evento asciende como una burbuja desde el elemento más interno hasta los contenedores superiores.

El ascenso se detiene de dos maneras. La primera es que un manejador de alguno de los contenedores atienda el evento y lo marque como consumido; en ese momento ya no pasa al siguiente nivel. La segunda es que se alcance el nivel más alto, normalmente la ventana, y ningún manejador lo consuma. En ambos casos el evento deja de propagarse.

Este recorrido explica por qué una ventana puede reaccionar a un evento de cualquiera de sus controles sin que cada control repita el mismo código. Si un atajo de teclado debe funcionar esté el foco en el campo que esté, no hace falta registrarlo en cada campo: basta con registrarlo en un contenedor común y dejar que los eventos que los campos no consuman burbucheen hasta él. El orden en que se ofrece el evento sigue siempre la jerarquía, del widget originario hacia afuera.

## Cómo se conecta con lo anterior y lo siguiente
Los [[eventos-de-interfaz]] describen el mensaje y su origen: un [[widget]] concreto. La propagación es el paso siguiente: decide en qué orden se ofrece ese mensaje a los contenedores del widget originario y cuándo se detiene. Esta nota es terminal en el recorrido del libro: no conduce a un nuevo concepto enlazable.

## Límites de esta explicación
Esta nota no describe cómo se registra o se ejecuta un manejador, ni el orden entre varios manejadores sobre el mismo widget; eso pertenece a [[manejador-de-eventos]]. Tampoco trata de otros modelos de recorrido, como el descenso desde el contenedor hacia el elemento, ni del dibujo de los widgets, que pertenece a [[widget]] y a [[ventana]].

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces, Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau. Respalda únicamente el contexto general de programas interactivos que esperan y responden a notificaciones. No constituye respaldo específico del burbujeo por jerarquía de widgets.
- [FTE-0002] Modern Operating Systems, 4ª ed., Andrew S. Tanenbaum (con Herbert Bos). Respalda únicamente el contexto general de la interacción entre usuario y aplicación. No constituye respaldo específico de la propagación de eventos entre widgets.
