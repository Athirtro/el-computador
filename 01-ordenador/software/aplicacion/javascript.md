---
titulo: "JavaScript"
slug: javascript
rama: software
categoria: aplicacion
nivel: 8
prerequisitos: [lenguaje-de-programacion-web]
conduce_a: []
alias: ["JS"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# JavaScript

## Idea central
JavaScript es el lenguaje de programación web que los navegadores ejecutan de forma nativa dentro del cliente. Es el ejemplo concreto que convierte al [[lenguaje-de-programacion-web]] en un programa real: las instrucciones llegan con la página y el [[navegador-web]] las ejecuta en el ordenador del usuario para que esta reaccione, cambie y pida datos sin tener que recargarse por completo.

## Antes de empezar
- [[lenguaje-de-programacion-web]]: qué es el código ejecutable que viaja con la página y que el navegador ejecuta en lugar de limitarse a presentar el documento recibido.

## Explicación
El prerequisito deja planteada la distinción esencial: una descripción de documento dice qué es cada parte de la página, mientras que el código ejecutable decide qué debe ocurrir cuando la persona actúa sobre ella. JavaScript ocupa exactamente ese segundo papel. No es un lenguaje que se ejecute en el servidor que entrega la página ni un programa instalado en el sistema operativo; es el lenguaje que el navegador trae incorporado para interpretar y ejecutar, en la sesión de navegación del usuario, las instrucciones que acompañan al documento.

Su comportamiento se entiende a partir del entorno en el que corre. Al ejecutarse en el [[navegador-web]], JavaScript solo puede actuar sobre lo que el navegador le permite: la página que está presentando y los recursos que puede solicitar a través de los mecanismos del navegador. Cuando la persona produce un [[eventos-de-interfaz]] — mueve el puntero, pulsa una tecla o activa un control —, el programa puede entregar ese aviso a un [[manejador-de-eventos]] y responder alterando el contenido visible, mostrando u ocultando partes o iniciando una petición de datos actualizados. Es esa capacidad de respuesta la que distingue a una página con JavaScript de un documento fijo: la página deja de ser una respuesta única y se comporta como una pequeña aplicación que se ejecuta en el cliente, dentro de la [[aplicacion-web]].

Ese confinamiento explica también su límite. JavaScript heredado por el navegador no tiene acceso directo al sistema operativo ni a los archivos del usuario; cualquier acceso a los recursos del ordenador pasa por los servicios que el navegador ofrece como proceso protegido por el sistema. Por eso el mismo mecanismo que hace interactiva una página no puede, por sí solo, tratarla como un programa con privilegios de sistema: actúa como código huésped del navegador, no como aplicación independiente.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[lenguaje-de-programacion-web]] se desciende un peldaño hasta aquí: si la nota anterior explicaba qué tipo de código es el que se ejecuta en el cliente web, esta identifica su lenguaje concreto y nativo del navegador. No se enlaza todavía al siguiente peldaño porque el concepto hacia el que conduce, la representación viva de la página que el código puede modificar —es decir, la estructura de la página convertida en objetos sobre los que JavaScript puede leer y escribir—, aún no está en la cola de conceptos enlazables; quedará sin enlace hasta que el orquestador lo promueva.

## Límites de esta explicación
Esta nota no desarrolla la sintaxis concreta de JavaScript, esto es, las reglas exactas para escribir sus instrucciones, ni su tipado, sus funciones ni sus bibliotecas. Tampoco desarrolla el [[lenguaje-de-descripcion-de-documentos]], que ya se trata en su nota canónica, ni cómo el navegador construye internamente la representación viva y modificable de la página sobre la que actúa el código. Esos temas corresponden a peldaños propios y quedan excluidos de esta explicación.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre JavaScript, su ejecución en el navegador o la respuesta a eventos de interfaz.
