---
titulo: "Aplicación con red"
slug: aplicacion-con-red
rama: software
categoria: aplicacion
nivel: 3
prerequisitos: [software-de-aplicacion]
conduce_a: []
alias: ["aplicación en red", "aplicación de red", "network application"]
estado: borrador
fuentes: []
---

# Aplicación con red

## Idea central
Una aplicación con red es una aplicación que, además de trabajar con los datos de su propio ordenador, intercambia datos con otros ordenadores. Su valor está en que la tarea que realiza —consultar una página, enviar un mensaje, sincronizar un archivo— se completa aunque parte de la información esté en otro equipo.

## Antes de empezar
- [[software-de-aplicacion]]: qué es una aplicación y en qué se diferencia del software de sistema y del software de programación.

## Explicación
Desde [[software-de-aplicacion]] se sabe que una aplicación traduce una intención de la persona en operaciones que ejecuta el sistema. Una aplicación con red mantiene esa misma función, pero una parte de esas operaciones no ocurre en el ordenador local: consiste en enviar datos a otro ordenador y esperar la respuesta de ese otro ordenador. La red es el conjunto de ordenadores conectados que pueden intercambiar datos entre sí; esta nota la usa solo en ese sentido mínimo, sin desarrollar sus componentes físicos ni su organización.

La comunicación sigue dos pasos que conviene distinguir. Primero, la aplicación local solicita algo concreto: por ejemplo, el contenido de una página, un mensaje o un archivo. Segundo, otro programa, que actúa como servidor, es decir, como el equipo que atiende esas solicitudes, responde con los datos pedidos o con un aviso de error. A la aplicación que solicita y muestra el resultado se la llama cliente. Por eso se habla de relación cliente-servidor: no es una división en dos programas distintos por naturaleza, sino dos papeles que una misma aplicación puede adoptar según el momento.

Para hablar con otro equipo, la aplicación no puede limitarse a usar las funciones locales de su propio ordenador. Necesita decir a qué equipo quiere comunicarse, mediante una dirección que lo identifique en la red, y necesita una manera común de formular la solicitud y de interpretar la respuesta. Esa manera común es un protocolo de red, es decir, un conjunto acordado de reglas que ambas partes entienden. El sistema operativo se encarga de transmitir los datos por la red y de entregar la respuesta a la aplicación; la aplicación se ocupa de pedir lo que el usuario necesita y de presentar el resultado de forma comprensible.

Por eso una aplicación con red no es solo una aplicación con una pantalla distinta. Sigue siendo una aplicación en el sentido de [[software-de-aplicacion]], pero su trabajo se reparte entre varios ordenadores: el local, donde la persona actúa, y los remotos, donde se guarda o se procesa parte de la información. La diferencia visible está en que la tarea puede consultarse, enviarse o actualizarse a distancia, y en que el resultado depende de que el otro equipo responda correctamente.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-aplicacion]] se desciende a este peldaño por el modo de trabajo: si toda aplicación resuelve una tarea a partir de los datos disponibles, la aplicación con red es la que obtiene o entrega parte de esos datos por la red. El contrato de esta nota no le asigna un `conduce_a` posterior; queda como una rama cerrada del recorrido de aplicación. Cuestiones como las ventanas o los menús que muestra pertenecen a [[aplicacion-grafica]], de modo que lo gráfico y lo conectado se tratan por separado y solo coinciden cuando una misma aplicación reúne ambos aspectos.

## Límites de esta explicación
Esta nota no desarrolla cómo son las redes por dentro, qué aparatos las forman ni cómo viaja físicamente la señal; esos temas deben tratarse en notas propias de red. Tampoco desarrolla los protocolos concretos de la web ni la seguridad de las comunicaciones: la protección de datos en la red y la defensa frente a programas dañinos pertenecen a notas de seguridad y a [[software-malicioso]] y [[defensa-malware]], sin entrar aquí en el detalle técnico. Los archivos o mensajes concretos que una aplicación envía se tratan en [[formatos-de-archivos]] y en [[estructuras-de-datos]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
