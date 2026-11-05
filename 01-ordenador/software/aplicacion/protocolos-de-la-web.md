---
titulo: "Protocolos de la web"
slug: protocolos-de-la-web
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [navegador-web]
conduce_a: []
alias: ["protocolos de la web", "web protocols"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Protocolos de la web

## Idea central
Los protocolos de la web son las reglas que permiten que el [[navegador-web]] pida un recurso a un [[servidor]] y entienda su respuesta. Definen cómo se formula una petición, cómo se describe lo que se envía y cómo se anuncia el resultado, de modo que programas de fabricantes distintos pueden comunicarse sin conocerse previamente.

## Antes de empezar
- [[navegador-web]]: qué es el navegador como cliente visible de una aplicación web, cómo interpreta y presenta el documento recibido, y cómo vuelve a pedir cuando la persona pulsa un enlace o envía un formulario.

## Explicación
Toda comunicación en una [[red-de-computadores]] se rige por un [[protocolo-de-red]], es decir, un conjunto de reglas compartidas para intercambiar datos. En la web ese intercambio sigue el modelo [[cliente-servidor]]: el navegador actúa como cliente, el programa que guarda la información y atiende las peticiones actúa como [[servidor]], y ambos hablan el mismo idioma de mensajes. El protocolo principal de la web es el protocolo de transferencia de hipertexto (Hypertext Transfer Protocol, HTTP): el conjunto de reglas con las que un cliente pide un recurso identificado por una dirección —una dirección web es un texto que indica qué recurso se quiere y en qué servidor se encuentra— y con las que el servidor responde.

Una petición web tiene tres partes esenciales. La primera es el método, la indicación de lo que se quiere hacer: pedir un recurso para mostrarlo, enviar datos mediante un formulario o crear, modificar o eliminar algo en el servidor. La segunda es el identificador del recurso pedido, junto con las cabeceras, que son líneas breves de texto que describen el mensaje —por ejemplo, el formato del contenido que el cliente acepta o los datos que lo acompañan—. La tercera, cuando se envían datos, es el cuerpo de la petición, el contenido que viaja del cliente al servidor. El servidor, por su parte, responde siempre con un código de estado, un número que resume el resultado de forma normalizada, y con sus propias cabeceras y, si procede, con el cuerpo de la respuesta, que contiene el recurso pedido.

Ese cuerpo es el puente entre el protocolo y lo que ve la persona. La respuesta no llega ya presentada en pantalla: llega como datos descritos según el formato indicado en las cabeceras, y el navegador los interpreta para construir la página visible. La mayoría de las respuestas web se enmarcan en este esquema de petición y respuesta, y el mismo esquema se reutiliza cada vez que la página necesita un recurso adicional —una imagen, un estilo, un dato actualizado—: cada recurso es una petición independiente con su propia respuesta. Así, navegar, pulsar enlaces o enviar formularios no son operaciones distintas desde el punto de vista del protocolo, sino peticiones sucesivas que comparten las mismas reglas.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[navegador-web]] se desciende a este peldaño por el ciclo de petición y respuesta: el navegador no obtiene el contenido de la página de un programa local, sino que lo pide a un servidor en cada ocasión. Esta nota describe las reglas que hacen posible ese ciclo —método, identificador, cabeceras, cuerpo y código de estado— sin entrar en cómo el navegador presenta el documento recibido ni en cómo el servidor decide qué responder. Con ello se cierra esta rama: al no tener continuidad asignada, no conduce a ningún concepto posterior del libro.

## Límites de esta explicación
Esta nota no desarrolla el lenguaje concreto con el que se describen los documentos web ni la forma en que el navegador los dibuja, que pertenecen a notas propias de presentación y quedan excluidos de este peldaño. Tampoco desarrolla la seguridad de las comunicaciones —la autenticación o el cifrado en tránsito—, que se trata en [[seguridad-aplicacion-con-red]]. El funcionamiento interno del servidor y el transporte de los datos por debajo del protocolo web tampoco forman parte de esta explicación.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre la web, el navegador, sus protocolos de petición y respuesta o sus códigos de estado.
