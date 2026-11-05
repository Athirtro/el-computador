---
titulo: "Gestión de ventanas"
slug: gestion-de-ventanas
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [ventana]
conduce_a: []
alias: ["gestión de ventanas", "window management"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Gestión de ventanas

## Idea central
La gestión de ventanas es la función que ordena la presencia de varias ventanas a la vez en pantalla: decide cuál está delante, cuál está activa y cuáles quedan detrás o cerradas. Sin esa ordenación, las ventanas de varias aplicaciones se solaparían de forma incontrolada y el usuario no sabría qué está viendo ni dónde actuar.

## Antes de empezar
- [[aplicacion-grafica]]: qué es una aplicación gráfica y por qué trabaja mediante ventanas.
- La ventana es la región delimitada de la pantalla donde una aplicación muestra su contenido y sus controles.

## Explicación
Cuando varias aplicaciones gráficas están abiertas a la vez, cada una muestra su contenido en su propia ventana y esas ventanas comparten la misma pantalla, por lo que pueden solaparse. Alguien debe decidir el orden en que se dibujan y cuál de ellas recibe la entrada del usuario. Esa función la ejerce el sistema operativo a través de su gestor de ventanas (window manager), es decir, el componente del sistema que mantiene la lista ordenada de ventanas y dibuja en pantalla la que está delante. En esta nota se tratan solo las cuatro operaciones básicas de esa función.

La primera operación es apilar: mantener un orden de apilamiento u orden z (z-order), que indica qué ventana tapa a cuál. La ventana que está más delante se dibuja encima y oculta la parte de las demás que queda debajo; las que están detrás se dibujan pero quedan parcial o totalmente tapadas. Cambiar ese orden es elevar una ventana (subirla al frente) o bajarla (enviarla detrás de las demás), y es lo que ocurre, por ejemplo, cuando se hace clic en una ventana que antes no se veía: pasa a estar delante de las que la tapaban.

La segunda operación es mover: cambiar la posición de una ventana sobre la pantalla arrastrándola, normalmente desde su barra de título. Mover no cambia ni el contenido ni el tamaño de la ventana, solo el lugar donde se muestra, y el sistema vuelve a dibujarla en la nueva posición respetando el orden de apilamiento vigente.

La tercera operación es activar: señalar qué ventana es la activa, es decir, la que de momento recibe el teclado y los comandos del usuario. Normalmente la ventana activa es también la que está delante, y se distingue visualmente, por ejemplo, con la barra de título resaltada. Activar una ventana al hacer clic en ella es la forma habitual de pasar de trabajar en una aplicación a trabajar en otra sin cerrar ninguna.

La cuarta operación es cerrar: eliminar una ventana de la pantalla y de la lista de ventanas. Cerrar una ventana no siempre equivale a terminar la aplicación: en un editor, por ejemplo, puede cerrar solo el documento visible y dejar la aplicación abierta sin ventanas, o puede ser la aplicación entera la que termina. Por eso el sistema, antes de cerrar, puede pedir confirmación si hay cambios sin guardar, y al cerrar libera los recursos asociados a esa ventana, como la memoria que usaba su contenido. Que varias aplicaciones estén abiertas a la vez solo es posible porque el sistema operativo gestiona varios procesos en paralelo, cuyo reparto de procesador y memoria se trata en [[multitarea]] y [[gestion-de-recursos]].

## Cómo se conecta con lo anterior y lo siguiente
Desde la ventana —la región donde una aplicación muestra su contenido— se pasa a la gestión de ventanas: una sola ventana no necesita ordenación, pero en cuanto hay varias, el sistema debe apilarlas, moverlas, activarlas y cerrarlas, y esa es exactamente la función descrita aquí. Esta nota es una rama terminal, sin `conduce_a`: el detalle de cómo está construida una ventana por dentro queda fuera, y nada posterior depende de esta nota.

## Límites de esta explicación
Esta nota no trata el detalle de los controles que hay dentro de una ventana (botones, menús, campos), que pertenece a la nota de widget, pendiente. Tampoco trata otras operaciones sobre la ventana, como minimizarla (convertirla en un icono para dejar de verla) o maximizarla (hacerla ocupar toda la pantalla), ni el dibujo técnico de los píxeles, que pertenece al software de sistema. La gestión de los procesos que hay detrás de cada aplicación se trata en [[gestion-de-recursos]] y [[proceso]].

## Referencias
- [FTE-0001] — Operating Systems: Three Easy Pieces. Respalda la gestión de varios procesos en paralelo y el reparto de recursos que hace posible tener varias aplicaciones abiertas a la vez.
- [FTE-0002] — Modern Operating Systems, 4ª ed. Respalda que la gestión de ventanas es un servicio que el sistema operativo ofrece a las aplicaciones, y no una tarea de cada aplicación por separado.
