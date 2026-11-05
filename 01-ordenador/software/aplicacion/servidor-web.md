---
titulo: "Servidor web"
slug: servidor-web
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [servidor]
conduce_a: []
alias: ["servidor web", "web server"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Servidor web

## Idea central
Un servidor web es el [[servidor]] especializado en atender solicitudes web: recibe peticiones de [[navegador-web]] y responde con documentos y recursos. Es la parte remota de una [[aplicacion-web]], un [[proceso]] permanente que escucha, atiende y responde.

## Antes de empezar
- [[servidor]]: equipo y programa que escucha solicitudes, las atiende como procesos y responde con datos o avisos de error. Esta nota especializa ese papel sin cambiar su lógica.

## Explicación
Desde [[servidor]] se sabe que el servidor no existe para uso directo de una persona delante de un equipo, sino para que otros equipos le pidan algo por la red y él responda. El servidor web aplica ese mismo esquema a la web: en un lado actúa el [[navegador-web]], que recoge lo que escribe la persona y lo presenta; en el otro, el servidor web, que espera de forma continua en un punto de contacto conocido y atiende cada solicitud como una tarea concreta.

La especialización está en qué recibe y qué devuelve. Cuando una [[aplicacion-web]] se usa desde un navegador, la solicitud llega como petición de un recurso identificable —un documento, una imagen, un dato— y la respuesta entrega ese recurso acompañado de una indicación sobre el resultado. El servidor web desglosa la petición, localiza lo pedido en su propio almacenamiento mediante su [[sistema-de-archivos]] o lo obtiene de la aplicación asociada, y devuelve la respuesta por la misma vía por la que llegó. Si el recurso no existe o la petición no puede cumplirse, devuelve un aviso de error en lugar del recurso.

Según el tipo de solicitud, el servidor web actúa de dos maneras que conviven. En unos casos se limita a entregar documentos ya guardados, tal como están almacenados, lo cual es rápido y sencillo. En otros, no entrega un archivo listo, sino que activa el programa que acompaña al servidor para que produzca la respuesta en ese momento a partir de datos guardados, de la petición recibida o de su combinación. Ambas maneras comparten el esquema de [[servidor]]: escucha permanente, atención de cada petición como un [[proceso]] y respuesta con el dato o con el aviso de error.

El servidor web no es, por tanto, un servidor distinto en naturaleza. Es un servidor instalado y configurado para la web: permanece encendido, atiende solo peticiones con formato web, entrega documentos o respuestas producidas al instante y deja de responder si deja de escuchar. Por eso el mismo ordenador puede actuar como cliente de otro servicio y, a la vez, como servidor web de muchos navegadores: son papeles, no naturalezas fijas.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[servidor]] a esta nota consiste en fijar un destino concreto para ese esquema general —escuchar, atender, responder—: cuando el cliente es un [[navegador-web]], el servidor que responde es un servidor web. La nota no tiene `conduce_a` posterior: queda como rama terminal de la cadena [[aplicacion-con-red]] → [[cliente-servidor]] → [[servidor]] → servidor web, y a partir de ella se iría hacia el detalle de cómo se formulan las peticiones y las respuestas, que pertenece a una nota de protocolo distinta.

## Límites de esta explicación
Esta nota no desarrolla las reglas que permiten a navegador y servidor entenderse —es decir, el protocolo web—: el detalle del formato de peticiones y respuestas, de sus campos y de sus estados queda fuera deliberadamente. Tampoco desarrolla el contenido concreto de los documentos web, ni la programación de la aplicación que produce las respuestas dinámicas, ni la seguridad de la conversación, que corresponde a [[seguridad-aplicacion-con-red]].

## Referencias
- [FTE-0001, FTE-0002]: ambos textos describen la organización de los sistemas en que un programa permanente atiende peticiones como procesos, escucha conexiones de red y responde; respaldan el esquema general de servidor aplicado aquí a la web. No contienen una descripción específica del servidor web, por lo que las afirmaciones web de esta nota deberán contrastarse con una fuente primaria adicional antes de darla por revisada.
