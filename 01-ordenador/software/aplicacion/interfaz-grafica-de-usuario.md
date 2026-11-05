---
titulo: "Interfaz gráfica de usuario"
slug: interfaz-grafica-de-usuario
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-grafica]
conduce_a: [ventana]
alias: ["interfaz gráfica de usuario", "graphical user interface", "GUI"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Interfaz gráfica de usuario

## Idea central
La interfaz gráfica de usuario es el conjunto de elementos visuales con los que una aplicación gráfica muestra su contenido y recibe las instrucciones de la persona. Su función es traducir el trabajo de la aplicación a una presentación que se reconoce y se opera señalando, en lugar de escribir comandos de texto.

## Antes de empezar
- [[aplicacion-grafica]]: qué es una aplicación gráfica y por qué se distingue por su presentación visual y no por su tarea concreta.

## Explicación
Desde [[aplicacion-grafica]] se sabe que el trabajo se realiza sobre una superficie visual donde la persona señala y activa elementos. La interfaz gráfica de usuario es precisamente ese conjunto de elementos: todo lo que se ve en pantalla y con lo que se puede interactuar para expresar una decisión. No es una sola pieza, sino el conjunto ordenado de piezas que una aplicación presenta como su espacio de trabajo.

Cada elemento visual cumple una función precisa. Un botón es un elemento que al activarlo ordena una acción concreta. Un campo es un elemento donde la persona introduce información. Un menú es una lista de acciones disponibles. Un área de contenido muestra el resultado del trabajo, como el texto de un procesador de textos o los archivos listados por un gestor de archivos. Una ventana es una región delimitada de la pantalla dentro de la cual se muestran esos elementos y el contenido de la aplicación; es la pieza que delimita dónde ocurre la interacción.

Esta forma de interacción se apoya en un principio distinto al de la línea de comandos: la persona no necesita recordar ni escribir la orden exacta, sino reconocer entre las opciones visibles la que desea y activarla. La interfaz hace visibles el estado del trabajo y las acciones posibles en cada momento. Por eso el modo de presentación no es un dato menor: determina cómo la persona descubre qué puede hacer y comprueba el efecto de cada acción.

La aplicación no produce esa presentación en solitario. Se apoya en los servicios del [[software-de-sistema]] para acceder a los recursos del ordenador, entre ellos la presentación en pantalla y la recepción de las acciones del usuario sobre los elementos visibles [FTE-0001, FTE-0002]. Esos servicios pertenecen al entorno del [[sistema-operativo]]; esta nota se ocupa únicamente de qué presenta la interfaz gráfica de usuario y qué papel cumple cada uno de sus elementos como conjunto.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-grafica]] se pasa a su rasgo definitorio: si la aplicación gráfica es el programa que se usa mediante elementos visuales, la interfaz gráfica de usuario es el conjunto concreto de esos elementos y la lógica de presentación que los organiza. El siguiente peldaño es la ventana, la región delimitada donde ese conjunto se muestra y se opera como una unidad.

## Límites de esta explicación
Esta nota no desarrolla el detalle de cada elemento visual ni el funcionamiento interno de la ventana; la ventana como región delimitada se trata en `ventana` y sus componentes, como botones, menús y campos, quedan para sus notas específicas. Tampoco trata cómo el sistema operativo dibuja esos elementos ni gestiona los dispositivos de entrada, que pertenece al [[software-de-sistema]] y a [[sistema-operativo]]. Las aplicaciones cuya finalidad es comunicarse con otros equipos se tratan en [[aplicacion-con-red]], y la interacción mediante comandos de texto, en [[aplicacion-de-consola]] y [[terminal-de-texto]].

## Referencias
- [FTE-0001]: Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau. Respalda el papel del sistema operativo como proveedor de los servicios que la aplicación utiliza para presentarse y recibir acciones del usuario.
- [FTE-0002]: Modern Operating Systems (4ª ed.), Tanenbaum y Bos. Respalda la distinción entre el programa de aplicación y los servicios del sistema que le permiten operar sobre los recursos del ordenador.
