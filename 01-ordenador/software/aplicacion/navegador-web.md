---
titulo: "Navegador web"
slug: navegador-web
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-web]
conduce_a: []
alias: ["navegador web", "web browser"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Navegador web

## Idea central
El navegador web (web browser) es la aplicación por la que la persona usa una [[aplicacion-web]]: recibe los recursos que envía el servidor, los interpreta como un documento y los presenta en pantalla, permitiendo leer, pulsar y escribir sobre ellos como sobre cualquier ventana. Su valor está en ser el cliente visible que convierte datos de red en una superficie de trabajo familiar.

## Antes de empezar
- [[aplicacion-web]]: qué es una aplicación web, el papel del cliente y del servidor, y el ciclo de petición y respuesta.

## Explicación
Desde [[aplicacion-web]] se sabe que el navegador actúa como cliente: solicita algo al servidor y presenta lo que recibe. Un navegador web es, antes que nada, esa aplicación cliente llevada a su forma general. No es una aplicación web concreta —una tienda, un correo—, sino el programa que permite usar cualquier aplicación web desde el mismo lugar. Cuando la persona introduce una dirección, el navegador la traduce en una petición, espera la respuesta del servidor y presenta el documento recibido; cuando pulsa un enlace o envía un formulario, repite el mismo ciclo con la nueva petición. La lógica propia de la aplicación —qué datos guardar, cómo calcular un total— permanece en el servidor; el navegador solo interpreta y presenta.

Presentar significa construir la página visible a partir de lo recibido. El contenido llega descrito mediante un lenguaje de descripción de documentos —un texto estructurado que marca qué es título, qué es párrafo y qué es enlace—, y el navegador lo interpreta para dibujar texto, imágenes y controles (botones, campos de escritura, desplegables) en la posición y con el aspecto descritos. A partir de esa interpretación la persona puede interactuar: hacer clic para pedir otra página, escribir para rellenar un campo, desplazarse para ver el resto del documento. La presentación es, por tanto, un trabajo de traducción: de una descripción recibida por la red a una ventana que se puede mirar y manejar, como en cualquier [[aplicacion-grafica]], pero donde el contenido de la ventana no viene de un programa instalado localmente, sino del servidor en cada petición.

La ventana del navegador organiza ese trabajo. Contiene una zona de dirección, donde la persona escribe o ve el identificador del recurso pedido, y una zona principal donde se presenta el documento actual. Sobre esa base, el navegador permite abrir varias páginas a la vez en pestañas (cada pestaña, un documento independiente presentado en la misma ventana, entre los que se puede cambiar sin cerrar los demás) o en ventanas distintas, y moverse entre páginas ya visitadas mediante los botones de retroceso y avance. Todo ello es gestión de presentación: decidir qué documento se ve, en qué pestaña y en qué momento de su historial. El propio navegador, como cualquier aplicación, se ejecuta como un [[proceso]] protegido por el sistema operativo y depende de los servicios que este le ofrece para usar la memoria, los archivos y la red del ordenador.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-web]] se desciende a este peldaño por el papel del cliente: si una aplicación web reparte el trabajo entre un cliente visible y un servidor que guarda la información, el navegador web es el cliente convertido en programa general y reutilizable. Esta nota describe su función de interpretar y presentar el contenido recibido y su organización en ventanas y pestañas, y deja atrás el ciclo de petición y respuesta, ya explicado en el prerequisito. Con ello se cierra esta rama: al no tener continuidad asignada, no conduce a ningún concepto posterior del libro.

## Límites de esta explicación
Esta nota no desarrolla la lógica del servidor —cómo almacena datos o decide las respuestas—, que se describe en [[aplicacion-web]]. Tampoco desarrolla los protocolos concretos por los que viaja la petición, los lenguajes concretos con los que se describen los documentos o los programas que las páginas pueden ejecutar en el cliente, ni la autenticación o el cifrado de las comunicaciones; esos temas pertenecen a notas propias de red, de programación y de seguridad y quedan excluidos de este peldaño.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre la web, el navegador, sus ventanas o los protocolos de comunicación.
