---
titulo: "Aplicación web"
slug: aplicacion-web
rama: software
categoria: aplicacion
nivel: 4
prerequisitos: [software-de-aplicacion]
conduce_a: [navegador-web]
alias: ["aplicación web", "web application"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Aplicación web

## Idea central
Una aplicación web es una aplicación cuyo programa cliente se ejecuta dentro del navegador web del ordenador del usuario, sin necesidad de instalarse como aplicación local. Su valor está en que la misma aplicación puede usarse desde distintos ordenadores accediendo a su dirección en la red, manteniendo el trabajo repartido entre el cliente visible en pantalla y el servidor que guarda y procesa la información.

## Antes de empezar
- [[software-de-aplicacion]]: qué es el software de aplicación y en qué se diferencia del software de sistema y del software de programación.

## Explicación
Desde [[software-de-aplicacion]] se sabe que una aplicación traduce la intención de la persona en operaciones que el sistema ejecuta para resolver una tarea concreta. Una aplicación web sigue siendo una aplicación en ese sentido, pero cambia el lugar donde reside su parte visible: en lugar de ser un programa instalado en el disco local, es un conjunto de recursos que el servidor envía al navegador para que los presente y gestione en pantalla.

La base de este reparto es la relación cliente-servidor ya descrita en [[aplicacion-con-red]]: el cliente es el programa que solicita algo y muestra el resultado a la persona, y el servidor es el programa, en otro ordenador, que atiende la solicitud y responde con los datos pedidos. En una aplicación web el cliente es el navegador web, es decir, el programa que interpreta y presenta el contenido recibido, y el servidor mantiene los datos y la lógica principal. Cuando la persona pulsa un botón, escribe en un campo o envía un formulario, el navegador envía la solicitud al servidor, este procesa lo pedido y devuelve la respuesta, que el navegador actualiza en pantalla. Este ciclo de petición y respuesta se repite durante toda la sesión de uso.

Esto distingue a la aplicación web de la [[aplicacion-grafica]] y de la [[aplicacion-con-red]] tomada en su forma general. La aplicación gráfica es la que presenta su trabajo con ventanas y controles, y la aplicación web también lo hace, pero dentro de la ventana del navegador; la aplicación con red es cualquier aplicación que intercambia datos con otro equipo, y la aplicación web es el caso concreto en que ese intercambio ocurre entre navegador y servidor mediante la web, con la ventaja de no requerir instalación local y de centralizar el programa en el servidor. Para la persona, la tarea se realiza en el navegador como con cualquier otra aplicación; para el servidor, la aplicación se mantiene y se actualiza en un solo lugar. Cuando la aplicación web necesita leer o escribir datos, lo hace pidiendo servicios al sistema operativo de cada equipo, como cualquier otra aplicación.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-aplicacion]] se desciende a este peldaño por el modo de entrega: si toda aplicación resuelve una tarea para la persona, la aplicación web es la que se entrega y se ejecuta en el navegador, trabajando entre cliente y servidor en la red. Esta nota describe el reparto entre ambos papeles y el ciclo de petición y respuesta, y deja paso a [[navegador-web]], nota en la que se estudiará cómo el navegador interpreta y presenta el contenido recibido, que aquí se usa solo como cliente de la aplicación.

## Límites de esta explicación
Esta nota no desarrolla cómo el navegador interpreta los documentos, ejecuta sus programas internos ni gestiona sus ventanas y pestañas; ese detalle corresponde a [[navegador-web]]. Tampoco desarrolla el funcionamiento de la red subyacente, los protocolos concretos de la web ni la autenticación o el cifrado de las comunicaciones, que pertenecen a notas propias de red y de seguridad y quedan excluidos de este peldaño. Los archivos concretos que la aplicación lee o guarda no se detallan aquí; su representación se trata en [[formatos-de-archivos]].

## Referencias
- FTE-0001: respalda únicamente que una aplicación, también cuando se ejecuta en el cliente web, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre la web, el navegador o los protocolos de comunicación.
