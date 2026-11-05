---
titulo: "Servidor web — detalle"
slug: servidor-web-detalle
rama: software
categoria: aplicacion
nivel: 8
prerequisitos: [servidor-web]
conduce_a: []
alias: ["servidor web estatico y dinamico", "static and dynamic web content"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Servidor web — detalle

## Idea central
Dentro de un [[servidor-web]] hay dos formas de responder: entregar un documento ya guardado tal como está, o generar la respuesta en ese momento. La primera es el contenido estático; la segunda, el contenido dinámico. Distinguirlas explica por qué un servidor web a veces solo lee archivos y a veces necesita el programa de una [[aplicacion-web]].

## Antes de empezar
- [[servidor-web]]: servidor especializado en atender solicitudes web recibidas de un [[navegador-web]], desglosarlas, localizar el recurso y responder con el recurso o con un aviso de error.

## Explicación
Desde [[servidor-web]] se sabe que el servidor web escucha de forma permanente y atiende cada solicitud como un [[proceso]] concreto. El detalle que añade esta nota es qué ocurre entre la escucha y la respuesta según el recurso pedido.

En el modo estático, el recurso existe ya como archivo en el [[sistema-de-archivos]] del equipo servidor: un documento descrito con un [[lenguaje-de-descripcion-de-documentos]], una imagen o un archivo descargable. El servidor web localiza ese archivo a partir de lo pedido, lo lee, y lo entrega sin modificarlo. La respuesta es, por tanto, la misma para cualquier [[navegador-web]] que pida el mismo recurso, y su coste es básicamente el de leer y enviar el archivo. No se ejecuta programa alguno de la aplicación asociada en cada petición.

En el modo dinámico, no hay un archivo terminado que entregar. Ante la solicitud, el servidor web activa el programa que acompaña a la [[aplicacion-web]]; ese programa combina los datos guardados con la información recibida en la solicitud y produce la respuesta en ese instante. Dos peticiones al mismo recurso pueden dar respuestas distintas, porque los datos o el contexto han cambiado. Aquí el coste ya no es solo leer un archivo: hay que ejecutar un programa, acceder a los datos y componer la respuesta, por lo que aparecen problemas nuevos, como mantener el estado entre peticiones relacionadas o proteger los datos que se muestran.

Ambos modos conviven en un mismo servidor web y comparten el esquema de [[servidor]]: escucha, atención de cada petición como [[proceso]] y respuesta con el dato o con el aviso de error. La diferencia está únicamente en si la respuesta se lee de un archivo ya existente o se fabrica al momento de pedirla.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[servidor-web]] consiste en abrir su caja negra: una vez establecido que el servidor web atiende peticiones y responde, esta nota distingue las dos clases de respuesta que puede dar, estática y dinámica, y qué exige cada una del equipo servidor. La nota no tiene `conduce_a` posterior: queda como rama terminal de la cadena [[aplicacion-con-red]] → [[cliente-servidor]] → [[servidor]] → [[servidor-web]] → servidor web — detalle, y a partir de ella se iría hacia el formato concreto de las peticiones y las respuestas, que pertenece a una nota de protocolo distinta.

## Límites de esta explicación
Esta nota no desarrolla las reglas que permiten a navegador y servidor entenderse —es decir, el protocolo web—: el detalle del formato de peticiones y respuestas, de sus campos y de sus estados queda fuera deliberadamente y se trata en [[protocolo-http]]. Tampoco desarrolla el contenido concreto de los documentos web, ni la programación de la aplicación que produce las respuestas dinámicas, ni la seguridad de la conversación, que corresponde a [[seguridad-aplicacion-con-red]].

## Referencias
- [FTE-0001, FTE-0002]: ambos textos describen la organización de los sistemas en que un programa permanente atiende peticiones como procesos, escucha conexiones de red y responde, y en que el sistema de archivos sirve de almacenamiento de los recursos; respaldan el esquema general de servidor, proceso y sistema de archivos aplicado aquí. No contienen una descripción específica de la distinción estático/dinámico en la web, por lo que las afirmaciones sobre esa distinción deberán contrastarse con una fuente primaria adicional antes de darla por revisada.
