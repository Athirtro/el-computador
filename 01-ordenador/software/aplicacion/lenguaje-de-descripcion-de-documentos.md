---
titulo: "Lenguaje de descripción de documentos"
slug: lenguaje-de-descripcion-de-documentos
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [navegador-web]
conduce_a: []
alias: ["lenguaje de marcado", "markup language"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Lenguaje de descripción de documentos

## Idea central
El lenguaje de descripción de documentos (markup language) es el texto estructurado que el servidor envía al navegador para decir qué es cada parte de una página: qué es título, qué es párrafo y qué es enlace. El navegador no recibe una imagen ya dibujada, sino esa descripción, y la interpreta para construir la página visible. Sin ese paso intermedio, no habría forma de separar el contenido de un documento de la pantalla concreta en la que se presenta.

## Antes de empezar
- [[navegador-web]]: qué es el navegador web, su papel de cliente que solicita documentos al servidor y su tarea de interpretarlos para presentarlos en pantalla.

## Explicación
Desde [[navegador-web]] se sabe que el navegador solicita y presenta, pero no queda claro qué es exactamente lo que recibe. El servidor no envía píxeles ni el aspecto final de la página; envía un documento descrito en un lenguaje propio, un texto en el que cada fragmento lleva marcado su papel dentro del conjunto. El navegador lee esas marcas y, a partir de ellas, decide qué dibujar y dónde. Así, la página visible es una interpretación de la descripción, no la descripción misma.

La idea de marcar es el centro de este peldaño. Marcar significa distinguir el texto que el lector debe leer de la información que indica cómo debe tratarse ese texto. Un título no se presenta igual que un párrafo porque la descripción declara su diferencia de función: el título anuncia y ordena, el párrafo desarrolla el contenido. Un enlace, por su parte, se marca como una referencia a otro recurso que la persona puede activar para pedirlo; al pulsarlo, el navegador inicia un nuevo ciclo de petición, como ya se vio en el navegador web. De este modo, la descripción permite construir un documento navegable sin que quien la escribe tenga que describir la pantalla, la ventana o los píxeles concretos.

Esa separación entre descripción y presentación es lo que hace reutilizable al documento. El mismo texto descrito puede presentarse en una ventana de escritorio, en una pantalla pequeña o en un lector de pantalla que lo lea en voz alta, porque la descripción dice qué es cada parte y la presentación decide cómo mostrarla o enunciarla en cada caso. El lenguaje de descripción no describe el aspecto acabado, sino la estructura y la función de cada elemento. Por eso el navegador puede interpretarlo y por eso los documentos pueden viajar entre ordenadores distintos sin perder su organización.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[navegador-web]] se desciende un peldaño hasta aquí: si el navegador interpreta y presenta lo que recibe del servidor, este artículo explica en qué forma recibe ese contenido, como un documento descrito por su estructura. La nota anterior dejaba abierto qué era ese contenido descrito; esta la cierra sin entrar en cómo viaja por la red ni en la forma concreta de cada lenguaje. Al no tener continuidad asignada, no conduce a ningún concepto posterior del libro.

## Límites de esta explicación
Esta nota no desarrolla los protocolos web, es decir, el conjunto de reglas que ordenan el intercambio entre cliente y servidor, ni la sintaxis concreta de ningún lenguaje de descripción, esto es, las reglas exactas para escribir sus marcas y los nombres que cada lenguaje usa. Tampoco desarrolla el aspecto visual detallado de la página, como colores o fuentes, ni los programas que una página puede ejecutar en el cliente. Esos temas corresponden a peldaños propios y quedan excluidos de esta explicación.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre el lenguaje de descripción de documentos, los protocolos web o la estructura de las páginas.
