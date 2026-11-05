---
titulo: "Dirección web"
slug: direccion-web
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [protocolos-de-la-web]
conduce_a: []
alias: ["dirección web", "URL", "uniform resource locator"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Dirección web

## Idea central
Una dirección web es el texto con el que el [[navegador-web]] indica a un [[servidor]] qué recurso se quiere pedir. Identifica un recurso concreto dentro del conjunto de recursos que ofrece ese servidor, de modo que programas de fabricantes distintos pueden referirse a la misma página o al mismo archivo sin conocerse previamente.

## Antes de empezar
- [[protocolos-de-la-web]]: las reglas de petición y respuesta con las que el navegador pide un recurso a un servidor, y la idea de que cada petición lleva un método, un identificador del recurso, cabeceras y, en su caso, un cuerpo.

## Explicación
En [[protocolos-de-la-web]] se vio que el [[navegador-web]] actúa como cliente dentro del modelo [[cliente-servidor]] y pide a un [[servidor]] un recurso identificado por una dirección. Esta nota explica qué información lleva ese identificador y cómo se lee, sin describir el detalle del protocolo con el que se intercambian los mensajes, que pertenece a [[protocolos-de-la-web]].

Una dirección web es un texto con estructura que combina tres piezas. La primera indica el protocolo, es decir, el código que el programa cliente acepta para hablar con el servidor; al escribirlo, la persona que navega ya está suponiendo un protocolo concreto antes de que se envíe ninguna petición. La segunda pieza indica el servidor, mediante un nombre legible para las personas que se traduce a la dirección numérica de la máquina en la [[red-de-computadores]]. La tercera pieza indica el recurso dentro de ese servidor, normalmente mediante una ruta que describe su posición dentro del conjunto de recursos que el servidor publica.

En su forma más habitual en el libro, la dirección web se escribe como localizador uniforme de recursos (Uniform Resource Locator, URL): el término en inglés va entre paréntesis solo en esta primera aparición. Esa forma permite distinguir dos usos que a menudo se confunden. Por un lado, la dirección sirve para localizar, es decir, para decirle al navegador en qué servidor está un recurso y con qué ruta se lo puede pedir. Por otro, la dirección no contiene el recurso en sí: la página, la imagen o el dato llegan después, como cuerpo de la respuesta del servidor. La dirección nombra el recurso; el protocolo transporta su contenido.

Algunas direcciones añaden piezas opcionales junto a la ruta. Una parte de consulta permite añadir datos breves junto a la petición, por ejemplo valores que el servidor necesita para filtrar o seleccionar. Una parte de fragmento señala una posición dentro del recurso ya descargado, como un apartado concreto de una página larga, sin cambiar lo que se pide al servidor. Ambas piezas forman parte del identificador, pero no cambian su función central: seguir nombrando un único recurso en un único servidor.

La dirección web tampoco identifica a la persona que la usa ni garantiza que el recurso siga disponible. Dos personas pueden usar la misma dirección desde ordenadores distintos, y un mismo servidor puede dejar de publicar un recurso o cambiar su ruta, con lo que la dirección deja de conducir a contenido. Por eso la dirección es un identificador dentro de un sistema de publicación mantenido por el servidor, no una promesa de permanencia ni una prueba de identidad.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[protocolos-de-la-web]] se desciende a este peldaño porque una petición web necesita un identificador del recurso antes de poder formularse: sin dirección, no hay petición que enviar ni respuesta que interpretar. Esta nota describe cómo se lee ese identificador —protocolo, servidor, ruta y piezas opcionales— sin describir cómo se intercambian los mensajes ni cómo el navegador presenta el documento recibido. Con ello se cierra esta rama: al no tener continuidad asignada, no conduce a ningún concepto posterior del libro.

## Límites de esta explicación
Esta nota no desarrolla el detalle del protocolo de transferencia de hipertexto (Hypertext Transfer Protocol, HTTP), sus métodos, sus cabeceras o sus códigos de estado, que se trata en [[protocolos-de-la-web]]. Tampoco desarrolla el lenguaje con el que se describen los documentos web, que pertenece a [[lenguaje-de-descripcion-de-documentos]], ni la forma en que el navegador los dibuja. La traducción del nombre del servidor a su dirección numérica en la red y el funcionamiento interno del servidor quedan fuera de este peldaño.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre direcciones web, URL, rutas de recursos o partes de consulta y fragmento.
