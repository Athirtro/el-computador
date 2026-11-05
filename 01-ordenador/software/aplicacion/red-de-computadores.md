---
titulo: "Red de computadores"
slug: red-de-computadores
rama: software
categoria: aplicacion
nivel: 4
prerequisitos: [aplicacion-con-red]
conduce_a: [protocolo-de-red]
alias: ["red de computadoras", "computer network"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Red de computadores

## Idea central
Una red de computadores es el conjunto de ordenadores conectados entre sí para poder intercambiar datos. Sin red, cada ordenador trabaja solo con lo que tiene en su propio almacenamiento; con red, una aplicación puede pedir datos a otro ordenador y recibirlos como si fueran suyos.

## Antes de empezar
- [[aplicacion-con-red]]: qué es una aplicación que intercambia datos con otros ordenadores y qué significan cliente y servidor en ese intercambio.

## Explicación
Desde [[aplicacion-con-red]] se sabe que una aplicación con red no resuelve su tarea solo en el ordenador local: necesita enviar una solicitud a otro equipo y esperar su respuesta. La red de computadores (computer network) es el paso que hace posible ese intercambio: es el conjunto de ordenadores unidos por conexiones que transportan datos entre ellos.

Cada ordenador conectado a la red se llama nodo. Dos nodos pueden intercambiar datos aunque estén en habitaciones distintas o en ciudades distintas, siempre que exista una conexión entre ellos a través de la red. El sistema operativo de cada nodo se encarga de entregar los datos a la red y de recoger los que llegan, mientras que la aplicación decide qué datos debe pedir y qué debe hacer con los recibidos.

La red no garantiza por sí sola que la solicitud se entienda. Para que dos ordenadores se comuniquen, ambos deben usar el mismo lenguaje de intercambio: a qué equipo van dirigidos los datos y con qué reglas se formulan. Esa parte —las reglas concretas del intercambio— es el peldaño siguiente y no se desarrolla aquí.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-con-red]] se desciende a este peldaño porque la aplicación con red presupone una red: sin ordenadores conectados no hay nadie a quien enviar la solicitud ni de quien recibir la respuesta. Esta nota explica solo qué es esa conexión entre ordenadores. El siguiente peldaño, [[protocolo-de-red]], explica las reglas que permiten que dos nodos se entiendan cuando intercambian datos.

## Límites de esta explicación
Esta nota no desarrolla las reglas concretas de comunicación entre ordenadores, que se tratan en [[protocolo-de-red]]. Tampoco desarrolla los aparatos físicos que forman la conexión, cómo viaja la señal por ellos ni la seguridad de los datos en tránsito; esos temas pertenecen a notas propias de hardware y de seguridad en red.

## Referencias
- [FTE-0001]: papel del sistema operativo en la gestión de la comunicación y los datos entre programas; base general de que es el sistema operativo, y no la aplicación, quien transmite los datos por la red.
- [FTE-0002]: visión de conjunto de los sistemas operativos como intermediarios entre los programas y los recursos del ordenador, incluido el intercambio de datos con otros equipos.
