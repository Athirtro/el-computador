---
titulo: "Protocolo HTTP — detalle"
slug: protocolo-http-detalle
rama: software
categoria: aplicacion
nivel: 8
prerequisitos: [protocolo-http]
conduce_a: []
alias: ["detalle del protocolo HTTP", "métodos, cabeceras y estados HTTP", "HTTP methods, headers and status codes"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Protocolo HTTP — detalle

## Idea central
Esta nota separa, dentro de [[protocolo-http]], los tres elementos que permiten leer cualquier intercambio HTTP: lo que se quiere hacer, cómo se describe el mensaje y cómo se resume el resultado. Su valor es práctico: distinguir intención, descripción y resultado evita confundir el efecto declarado con el efecto real en el servidor.

## Antes de empezar
- [[protocolo-http]]: estructura general de petición y respuesta, con método, identificador del recurso, cabeceras, cuerpo y código de estado.
- [[protocolos-de-la-web]]: ciclo de petición y respuesta web en el modelo [[cliente-servidor]].

## Explicación
El método es el verbo de la petición. Indica la operación que el cliente solicita al [[servidor-web]], sin describir todavía su resultado. La lectura es la familia que pide un recurso sin modificar el estado del servidor: el cliente envía la petición, el servidor localiza el identificador y responde con el contenido o con un error. La escritura es la familia que acompaña datos en el cuerpo para crear, sustituir o modificar un recurso, o para pedir una operación especial cuyo efecto se informa en la respuesta. El método por sí solo no garantiza el resultado; solo fija la intención que el servidor debe interpretar de forma uniforme.

Las cabeceras son líneas de nombre y valor que describen el mensaje sin sustituir al cuerpo. En la petición describen, por ejemplo, qué formato de contenido acepta el cliente, cómo interpreta el texto o qué credenciales lo acompañan. En la respuesta describen el formato del cuerpo contenido, su longitud y otros metadatos necesarios para interpretarlo. Por eso dos peticiones con el mismo método y el mismo identificador pueden diferenciarse en las cabeceras: no cambia lo que se pide, sino las condiciones en las que se pide o la forma de leer lo que vuelve. Las cabeceras tampoco crean datos nuevos por sí mismas; interpretan y acompañan al cuerpo.

El estado es el resumen normalizado de la respuesta: un número de tres cifras que el cliente puede tratar sin leer el cuerpo. Sus familias agrupan el resultado en éxito, redirección o solicitud de acción adicional, error atribuible a la petición y error del servidor. Dentro de cada familia, el código concreto precisa el caso, por lo que el cliente distingue, por ejemplo, un recurso no encontrado de un fallo interno del servidor. Este resumen no sustituye el cuerpo: una respuesta de éxito puede traer el recurso, una confirmación sin contenido o un mensaje breve, mientras que una respuesta de error puede traer o no un cuerpo explicativo. Leer el código primero y el cuerpo después es el orden correcto.

Los tres elementos se combinan en cada intercambio independiente: método para la intención, cabeceras para la descripción y estado para el resultado. Como cada petición vuelve a declararlos, no hay continuidad automática entre peticiones. El identificador del recurso sigue siendo solo una referencia opaca en esta nota; su composición se trata en [[direccion-web]].

## Cómo se conecta con lo anterior y lo siguiente
Este peldaño desciende desde [[protocolo-http]] separando sus tres piezas esenciales para que puedan leerse y tratarse por separado. No se ha asignado un paso posterior, por lo que `conduce_a` queda vacío y la nota cierra esta rama.

## Límites de esta explicación
Esta nota no desarrolla la composición de la dirección web, que pertenece a [[direccion-web]], ni el mecanismo de sesión que mantiene continuidad entre peticiones, ni la presentación del contenido en el navegador, que pertenece a [[navegador-web]] y a [[lenguaje-de-descripcion-de-documentos]].

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece. No constituye respaldo específico de métodos, cabeceras o códigos de estado HTTP.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre métodos, cabeceras o códigos de estado HTTP.
