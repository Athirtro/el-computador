---
titulo: "Modelo de objetos del documento"
slug: modelo-de-objetos-del-documento
rama: software
categoria: aplicacion
nivel: 8
prerequisitos: [javascript]
conduce_a: []
alias: ["modelo de objetos del documento", "document object model", "DOM"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Modelo de objetos del documento

## Idea central
El modelo de objetos del documento es la representación viva de una página en forma de árbol de objetos que el navegador mantiene en memoria mientras la página está abierta. Esa representación es la que el código de la aplicación web manipula para cambiar lo que se ve sin pedir de nuevo el documento al servidor. Sin el modelo de objetos, [[lenguaje-de-programacion-web]] podría ejecutar instrucciones pero no tendría nada concreto sobre lo que actuar.

## Antes de empezar
- [[javascript]]: el lenguaje que el navegador ejecuta en el lado del cliente y que accede al modelo de objetos para leerlo y modificarlo.

## Explicación
El navegador no muestra el texto de una página tal y como llega del servidor. Al recibir el documento descrito con [[lenguaje-de-descripcion-de-documentos]], lo interpreta y construye primero una representación interna de su estructura. Esa representación tiene forma de [[arbol]]: cada parte del documento, como un título, un párrafo o un botón figurado como [[widget]], es un nodo con un padre, hijos y hermanos, ordenados en el mismo orden en que aparecen en la página. El modelo de objetos del documento es, precisamente, esa estructura de nodos expuesta al programador como objetos manipulables dentro de [[navegador-web]].

La diferencia decisiva respecto a la descripción original es que la representación está viva. La descripción es texto que se lee una vez para construir la página; la representación que crea el navegador se mantiene en memoria y cambia cuando se modifica. Cuando el código modifica un nodo, por ejemplo, al cambiar su texto, su posición o su presencia en la página, el navegador actualiza la presentación para reflejar esa modificación, sin necesidad de volver a descargar el documento completo del servidor. De este modo, la página deja de ser un resultado cerrado y se convierte en un estado que el programa puede consultar antes de actuar y cuyo estado posterior a la acción puede también consultarse.

Ese acceso se produce en el contexto de [[aplicacion-web]] ejecutada en el cliente. El código no actúa sobre el documento como una cadena de texto, ni sobre archivos del ordenador del usuario, sino sobre estos objetos que representan la página misma. Por eso el modelo acota lo que el código puede hacer: puede reorganizar, mostrar u ocultar y reescribir los nodos de la página actual, y puede registrar un [[manejador-de-eventos]] para que la estructura se adapte cuando la persona actúa, pero no convierte al navegador en un acceso directo al sistema. La exposición de la página como objetos es, a la vez, lo que hace posible la interactividad y lo que mantiene esa actividad confinada a la sesión de navegación.

Finalmente, la estructura en árbol también explica cómo se propagan los cambios. Al ser un [[arbol]], actuar sobre un nodo afecta a su posición en la jerarquía y a la manera en que se presentan sus descendientes, y un [[eventos-de-interfaz]] dirigido a un nodo puede alcanzar a sus antepasados a través de la [[propagacion-de-eventos]] propia de esa jerarquía. El modelo no es, por tanto, un simple inventario de partes: es el medio por el que el navegador sabe qué es cada cosa, dónde está respecto a las demás y qué ocurre cuando cambia.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[lenguaje-de-programacion-web]] se desciende un peldaño hasta aquí: si la nota anterior explicaba que la página puede ejecutar código y comportarse, esta explica sobre qué representación actúa ese código. La descripción dice qué es cada parte del documento; el código puede programar su comportamiento; el modelo de objetos ofrece la estructura viva sobre la que ambos operan y que permite que el comportamiento se traduzca en un cambio visible. Al no tener continuidad asignada en el contrato, no conduce a ningún concepto posterior del libro.

## Límites de esta explicación
Esta nota no desarrolla la sintaxis de [[javascript]], esto es, las reglas exactas para escribir sus instrucciones, ni los detalles de la construcción interna por los que [[navegador-web]] dibuja los nodos modificados en pantalla. Tampoco desarrolla [[lenguaje-de-descripcion-de-documentos]], que ya se trata en su nota canónica. Esos temas corresponden a peldaños propios y quedan excluidos de esta explicación.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre el modelo de objetos del documento, la estructura en árbol de la página o la manipulación de nodos por código en el navegador.
