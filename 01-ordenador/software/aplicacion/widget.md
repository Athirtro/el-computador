---
titulo: "Widget"
slug: widget
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [ventana]
conduce_a: []
alias: ["control gráfico", "widget"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Widget

## Idea central
Un widget es un control gráfico (widget): el elemento individual con el que la persona actúa dentro de una ventana, como un botón o un campo de texto. Es el peldaño que va de la ventana como espacio de trabajo a cada una de las piezas que permiten intervenir sobre ese trabajo.

## Antes de empezar
- [[ventana]]: la región delimitada de la pantalla dentro de la que se muestra el contenido y los controles de una aplicación (definición en una línea, sin enlace: nota aún pendiente, ver nota al orquestador).
- [[aplicacion-grafica]]: qué es una aplicación gráfica y cómo se presenta el trabajo mediante ventanas y controles.

## Explicación
Desde [[aplicacion-grafica]] se sabe que una aplicación gráfica presenta su trabajo en una ventana, dentro de la cual aparecen menús con listas de acciones, botones que ejecutan una acción al activarlos, campos donde se introduce información y zonas donde se muestra el resultado. Un widget es cada uno de esos elementos individuales. Si la ventana es el espacio de trabajo, el widget es la pieza concreta sobre la que la persona actúa: el botón que se pulsa, el campo donde se escribe, la casilla que se marca o la lista que se despliega.

Cada widget reúne dos aspectos inseparables. Por un lado, tiene una apariencia visible, su dibujo en pantalla, que indica qué es y en qué estado se encuentra: un botón se distingue de un campo de texto porque su forma y su contenido sugieren acciones distintas. Por otro lado, tiene una función, lo que ocurre cuando la persona actúa sobre él: al pulsar un botón se ejecuta una acción, al escribir en un campo se introduce un dato, al marcar una casilla se elige una opción. Esa unión de aspecto y función es lo que lo hace un control y no un simple dibujo: no basta con que se vea, ha de poder usarse.

Los widgets se diferencian por el tipo de actuación que admiten. Unos sirven para ejecutar una acción inmediata, como los botones de guardar o cancelar. Otros sirven para introducir o elegir datos, como los campos de texto, las casillas o las listas desplegables, en las que la actuación consiste en escribir o en seleccionar entre opciones presentadas. Otros, por último, sirven para mostrar información sin admitir actuación directa, como las etiquetas de texto o las zonas de resultado, aunque el sistema puede actualizar su contenido. Casi toda ventana de una aplicación gráfica se compone combinando widgets de estos tipos, y cada combinación corresponde a una tarea concreta.

Un ejemplo aclara la composición. En una ventana de diálogo de un editor de texto, un campo de texto muestra el nombre del archivo, lo que lo hace un widget de introducción de datos. Junto a él, dos botones, aceptar y cancelar, son widgets de ejecución de acción: pulsarlos confirma o descarta lo escrito. Una etiqueta indica qué debe escribirse en el campo, y es un widget de presentación. Ninguna de esas piezas es la ventana misma, pero sin ellas la ventana sería un espacio vacío: son los widgets los que la convierten en un lugar donde se puede actuar.

## Cómo se conecta con lo anterior y lo siguiente
Desde la ventana, que en esta nota se define en una línea porque su nota está pendiente, se desciende a los elementos que la componen: si la ventana es el espacio de trabajo de la aplicación, el widget es cada control individual que permite actuar dentro de ese espacio. Esta nota no abre un peldaño siguiente en la cola, porque el detalle de qué ocurre cuando se pulsa o se escribe sobre un control, los eventos que se generan y cómo se procesan, queda fuera de este peldaño y pertenece a una nota posterior.

## Límites de esta explicación
Esta nota no desarrolla cómo se generan ni cómo se procesan los eventos asociados a cada actuación sobre un widget; ese detalle corresponde a la nota pendiente de eventos de interfaz, aún no enlazable. Tampoco trata cómo el sistema operativo dibuja los widgets ni gestiona los dispositivos de entrada, que pertenecen al [[software-de-sistema]], ni las aplicaciones concretas que los combinan, que se tratan en [[aplicacion-grafica]] y en sus casos particulares.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau): respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre widgets, ventanas o controles gráficos.
- FTE-0002 (Modern Operating Systems, Tanenbaum y Bos): respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre widgets, ventanas o controles gráficos.
