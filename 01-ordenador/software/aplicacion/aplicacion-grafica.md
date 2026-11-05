---
titulo: "Aplicación gráfica"
slug: aplicacion-grafica
rama: software
categoria: aplicacion
nivel: 3
prerequisitos: [software-de-aplicacion]
conduce_a: []
alias: ["aplicación gráfica", "graphical application"]
estado: borrador
fuentes: []
---

# Aplicación gráfica

## Idea central
Una aplicación gráfica es un programa de aplicación en el que la persona interactúa principalmente con elementos visuales en pantalla, como ventanas y botones, en lugar de escribir comandos de texto. Su forma de presentación, no su tarea concreta, es lo que la distingue: un mismo trabajo, por ejemplo redactar un documento, se realiza con una interfaz visual en vez de con órdenes escritas.

## Antes de empezar
- [[software-de-aplicacion]]: qué es el software de aplicación y qué lo distingue del software de sistema y del software de programación.

## Explicación
Desde [[software-de-aplicacion]] se sabe que el software de aplicación existe para que una persona realice una tarea concreta y que se apoya en el [[software-de-sistema]] para acceder a los recursos del ordenador. La aplicación gráfica es una forma particular de cumplir esa función: presenta el trabajo sobre una superficie visual y recibe las decisiones del usuario mediante elementos que se pueden señalar y activar con un dispositivo de entrada.

El elemento básico de esa presentación es la interfaz gráfica de usuario (graphical user interface, GUI), es decir, el conjunto de elementos visuales con los que se muestran las opciones disponibles y el estado del trabajo. La ventana es la pieza central de esa interfaz: una región delimitada de la pantalla dentro de la cual se muestran el contenido y los controles de la aplicación. Dentro de una ventana aparecen, según el programa, menús con listas de acciones, botones que ejecutan una acción al activarlos, campos donde se introduce información y zonas donde se muestra el resultado. La ventana no es un adorno: es el espacio de trabajo que la aplicación ofrece a la persona y que el sistema mantiene visible, mueve o cierra cuando el usuario lo solicita.

Un ejemplo claro es un editor de texto. En un editor gráfico, el documento se ve en una ventana con su formato aplicado, las acciones de guardar o imprimir se eligen en menús o botones, y la persona comprueba al instante el efecto de cada cambio. El editor sigue siendo una aplicación en el sentido de [[software-de-aplicacion]]: su trabajo es redactar y preparar documentos, no gestionar recursos ni crear programas. Cuando necesita leer o guardar un archivo, o mostrar caracteres en pantalla, lo hace mediante los servicios del software de sistema, sin ocuparse de los detalles físicos de esas operaciones. Lo que lo hace gráfico es que la tarea se realiza señalando y activando elementos visuales, en lugar de escribir comandos de texto en una línea de comandos, que es la forma de interacción basada en órdenes escritas una tras otra.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-aplicacion]] se desciende a un tipo definido por su presentación: si el software de aplicación es el programa que se usa para una tarea, la aplicación gráfica es el que se usa mediante una interfaz visual de ventanas y controles. Esta nota no abre una cadena lineal hacia un siguiente peldaño, porque las aplicaciones gráficas forman un conjunto amplio, paralelizable, del que solo se ha mostrado aquí el rasgos común y un ejemplo.

## Límites de esta explicación
Esta nota no desarrolla cómo el sistema operativo dibuja las ventanas ni gestiona los dispositivos de entrada; eso pertenece al [[software-de-sistema]] y, en su momento, a [[sistema-operativo]]. Tampoco trata las aplicaciones cuya finalidad es comunicarse con otros equipos, como navegar por la web o enviar mensajes, que se tratan en [[aplicacion-con-red]]. Los archivos que un editor lee y guarda no se detallan aquí; su representación se trata en [[formatos-de-archivos]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
