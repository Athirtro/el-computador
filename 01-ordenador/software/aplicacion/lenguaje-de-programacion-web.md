---
titulo: "Lenguaje de programación web"
slug: lenguaje-de-programacion-web
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [lenguaje-de-descripcion-de-documentos]
conduce_a: []
alias: ["lenguaje para programar en el navegador", "web programming language"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Lenguaje de programación web

## Idea central
El lenguaje de programación web es el código ejecutable que viaja junto a la descripción de una página y que el navegador ejecuta en el ordenador del usuario, en lugar de limitarse a presentar el documento recibido. Con él, una página deja de ser un texto fijo para convertirse en un programa que responde a lo que hace la persona: modifica lo que se ve, reacciona a sus acciones y puede pedir nuevos datos sin abandonar la página. Sin este peldaño, [[navegador-web]] solo podría mostrar lo que el servidor le entregó; con él, puede comportarse.

## Antes de empezar
- [[lenguaje-de-descripcion-de-documentos]]: qué es describir un documento por su estructura y su función, y por qué el navegador interpreta esa descripción para construir la página visible.

## Explicación
Desde [[lenguaje-de-descripcion-de-documentos]] se sabe que el navegador construye la página a partir de una descripción, pero esa descripción, por sí sola, no actúa. Un párrafo descrito sigue siendo un párrafo, y un enlace descrito solo ofrece una referencia a otro recurso. El lenguaje de programación web añade un tipo de contenido distinto: instrucciones que el navegador no solo interpreta como forma, sino que ejecuta como programa dentro del propio cliente. Esas instrucciones llegan con el documento, como una parte más de lo que el servidor entrega, y quedan disponibles para el navegador en cuanto la página se carga.

El salto respecto a la descripción es que el programa puede cambiar la página mientras esta se está viendo. Cuando la persona mueve el puntero, pulsa una tecla o pulsa un [[widget]], el navegador no se limita a registrar un [[eventos-de-interfaz]]: puede entregar ese aviso a un [[manejador-de-eventos]], es decir, a la parte del programa preparada para responder a ese aviso concreto. La respuesta puede alterar el texto visible, mostrar u ocultar partes de la página o iniciar una petición nueva al servidor para obtener datos actualizados. De este modo, la página deja de ser una respuesta única del servidor y pasa a comportarse como una pequeña aplicación que se ejecuta en [[aplicacion-web]] del lado del cliente.

Esa ejecución ocurre en el [[navegador-web]], no en el ordenador que envió el documento. El código web es, por tanto, un programa dirigido a un entorno concreto: el navegador, con sus propias reglas de qué puede hacer y qué no puede hacer. No tiene acceso directo al sistema operativo ni a los archivos del usuario; solo puede actuar sobre la página que está presentando y sobre los recursos que el navegador le permite solicitar. Esa limitación es esencial: el mismo código que hace cómoda una página podría, si tuviera acceso libre, comprometer la seguridad del ordenador, y por eso el navegador lo confina a su propia sesión de navegación. El ejemplo más extendido de este tipo de lenguaje es JavaScript, el lenguaje que los navegadores ejecutan de forma nativa para estos fines.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[lenguaje-de-descripcion-de-documentos]] se desciende un peldaño hasta aquí: si la nota anterior explicaba cómo se describe una página para que el navegador la construya, esta explica cómo una página puede, además de describirse, comportarse. La descripción responde a qué es cada parte; el código ejecutable responde a qué debe ocurrir cuando la persona actúa sobre esas partes. Al no tener continuidad asignada, no conduce a ningún concepto posterior del libro.

## Límites de esta explicación
Esta nota no desarrolla [[lenguaje-de-descripcion-de-documentos]], que ya se trata en su nota canónica, ni la sintaxis concreta de ningún lenguaje de programación web, esto es, las reglas exactas para escribir sus instrucciones. Tampoco desarrolla cómo el navegador construye internamente la representación viva de la página que el código puede modificar, ni los lenguajes de programación que se ejecutan en el servidor. Esos temas corresponden a peldaños propios y quedan excluidos de esta explicación.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre el lenguaje de programación web, la ejecución en el navegador o la respuesta a eventos de interfaz.
