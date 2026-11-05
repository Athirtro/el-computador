---
titulo: "Protocolo HTTP"
slug: protocolo-http
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [protocolos-de-la-web]
conduce_a: []
alias: ["protocolo HTTP", "HTTP", "Hypertext Transfer Protocol"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Protocolo HTTP

## Idea central
El protocolo HTTP es el conjunto de reglas con las que un cliente pide un recurso a un servidor y el servidor anuncia el resultado. Estandariza qué se pide, cómo se describe el mensaje y cómo se resume su resultado, de modo que programas de fabricantes distintos puedan interaccionar sin coordinarse más allá de esas reglas.

## Antes de empezar
- [[protocolos-de-la-web]]: ciclo de petición y respuesta web entre el cliente visible y el servidor, con la existencia de método, identificador del recurso, cabeceras, cuerpo y código de estado.

## Explicación
HTTP describe intercambios en el modelo [[cliente-servidor]] que ya introduce [[protocolos-de-la-web]]: un programa cliente envía una única petición y el programa servidor responde con una única respuesta, sin que el intercambio dependa de un contexto previo compartido. Una dirección web es un texto que indica qué servidor atiende y qué recurso se quiere dentro de él; el detalle de su composición queda fuera de esta nota. Cada recurso es una petición independiente y completa.

La petición tiene tres partes esenciales. La primera es el método, la indicación de lo que se pretende hacer. El método de lectura pide el recurso sin modificar el estado del servidor. Los métodos de envío acompañan datos en el cuerpo de la petición para crear, sustituir o modificar algo en el servidor, o para pedir una operación cuyo efecto se informa en la respuesta. El método describe la intención, no el resultado: el resultado lo comunica el servidor.

La segunda parte es el identificador del recurso pedido junto con las cabeceras, que son líneas breves de texto del tipo nombre y valor que describen el mensaje. Las cabeceras de petición permiten al cliente declarar el formato del contenido que acepta, la codificación del texto o las credenciales que lo acompañan, y al servidor pedir a su vez información necesaria para responder. Las cabeceras no sustituyen al cuerpo: describen lo que acompaña o decodifica al cuerpo.

La tercera parte, cuando se envían datos, es el cuerpo de la petición, el contenido que viaja del cliente al servidor. Sin cuerpo, la intención del método es suficiente para muchas lecturas; con cuerpo, el método adquiere su efecto porque el servidor recibe los datos a los que debe aplicar la operación descrita.

La respuesta replica esta estructura en sentido contrario. Comienza con un código de estado, un número de tres cifras que resume el resultado de forma normalizada y que el cliente puede tratar de manera uniforme. Las familias de códigos agrupan resultados: la petición ha tenido éxito, requiere una acción adicional del cliente como autenticarse o seguir a otro recurso, indica un error atribuible a la petición, o indica un error en el servidor. Cada familia tiene un significado general y cada código concreto un significado particular, de modo que el cliente no tiene que leer el cuerpo para saber si la operación ha funcionado.

A continuación la respuesta incluye sus propias cabeceras, que describen el formato del cuerpo que contienen —técnicamente su tipo de medio—, su longitud y otros metadatos necesarios para interpretarlo. Por último, cuando procede, el cuerpo de la respuesta contiene el recurso pedido: el documento, el dato o el mensaje de confirmación. La misma respuesta puede carecer de cuerpo cuando no hay nada que devolver, como en una confirmación sin contenido o en un error que se queda solo con el código de estado.

La ausencia de contexto entre peticiones es consecuencia directa de este diseño. Como cada intercambio es completo en sí mismo, la continuación de una actividad sobre el mismo recurso necesita una petición nueva que vuelva a declarar su método, su identificador y sus cabeceras. Las aplicaciones web que simulan continuidad lo consiguen enviando en cada petición una información que permite al servidor reconocer al cliente y su actividad, aunque ese mecanismo queda fuera de esta nota.

## Cómo se conecta con lo anterior y lo siguiente
Este peldaño desarrolla el esqueleto anticipado en [[protocolos-de-la-web]] —método, identificador, cabeceras, cuerpo y código de estado— como un único protocolo concreto de petición y respuesta. No añade un paso hacia un concepto posterior asignado, por lo que `conduce_a` queda vacío y la nota cierra esta rama.

## Límites de esta explicación
Esta nota no desarrolla la estructura de una dirección web más allá de su función de identificador, ni la forma en que el navegador presenta el cuerpo de la respuesta, que pertenece a [[lenguaje-de-descripcion-de-documentos]] y a [[navegador-web]]. La protección de las comunicaciones y su autenticación se trata en [[seguridad-aplicacion-con-red]], y el transporte de los datos por debajo de HTTP queda fuera de este peldaño.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre HTTP, sus métodos, sus cabeceras o sus códigos de estado.
