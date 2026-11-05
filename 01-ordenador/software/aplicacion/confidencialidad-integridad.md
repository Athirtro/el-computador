---
titulo: "Confidencialidad e integridad"
slug: confidencialidad-integridad
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [criptografia-clave]
conduce_a: []
alias: ["confidencialidad de los datos", "integridad de los datos"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Confidencialidad e integridad

## Idea central
La confidencialidad es la propiedad de que solo el destinatario pueda leer el contenido de un mensaje, y la integridad es la propiedad de que nadie pueda alterarlo sin que el destinatario lo detecte. Son dos exigencias distintas sobre el mismo mensaje: una protege frente a la lectura y la otra frente a la modificación, y una aplicación que envía datos por la red necesita ambas para confiar en lo que recibe.

## Antes de empezar
- El prerequisito de esta nota es la noción de clave criptográfica: un valor secreto compartido entre el emisor y el destinatario, con el que se transforman los datos para que quien no lo conoce no pueda leerlos ni alterarlos de forma indetectable. El detalle de cómo se generan, se negocian y se protegen las claves queda fuera de esta nota.

## Explicación
En [[seguridad-aplicacion-con-red]] la aplicación con red ya no se limita a su propio equipo: envía mensajes a otro equipo y acepta los que recibe. Una vez decidida la comunicación, queda una pregunta previa a mostrar cualquier resultado: ¿puede alguien distinto del destinatario leer ese mensaje, y puede alguien cambiarlo en el trayecto sin que se note? Confidencialidad e integridad responden a cada una de esas dos preguntas por separado.

La confidencialidad se refiere a la lectura. Un mensaje tiene confidencialidad cuando su contenido solo es accesible para quien está autorizado a leerlo; cualquier tercero que lo intercepte obtiene una forma ilegible, no el contenido. Su fracaso es silencioso: el destinatario legítimo sigue recibiendo el mensaje, pero una copia de su contenido ya ha quedado expuesta. En una [[aplicacion-con-red]] eso significa que, sin confidencialidad, los datos personales, las credenciales o cualquier información sensible que viajan en el mensaje dejan de ser privados aunque el intercambio parezca funcionar con normalidad.

La integridad se refiere a la alteración. Un mensaje tiene integridad cuando cualquier cambio introducido durante el trayecto —modificar un importe, sustituir un destinatario, añadir o quitar datos— es detectable por el destinatario, que puede entonces rechazar el mensaje en lugar de aceptarlo como válido. Su fracaso también es silencioso, pero de otro modo: el mensaje se lee bien, solo que ya no dice lo que el emisor envió. Por eso la integridad no consiste en que nadie pueda tocar los datos, algo imposible de garantizar en una red, sino en que nadie pueda tocarlos sin que el destinatario se entere.

Que ambas propiedades sean distintas se ve en sus fracasos. Un mensaje puede ser confidencial e inseguro en integridad: solo el destinatario puede leerlo, pero un tercero puede modificarlo sin que el destinatario lo note, y la aplicación actuaría sobre datos falsos creyéndolos auténticos. Y puede ocurrir lo contrario: un mensaje puede llegar intacto, fiel a lo que se envió, pero haber sido leído por terceros durante el trayecto. Conseguir una no consigue la otra, por lo que una aplicación que necesita proteger un intercambio debe exigir las dos a la vez: que solo el destinatario lea y que cualquier alteración se detecte.

En el trabajo de la aplicación ambas se comprueban antes de entregar el resultado a la persona. Si el contenido recibido no supera la comprobación de integridad, la aplicación lo descarta en lugar de mostrarlo; si el mensaje saliente debe viajar con confidencialidad, la aplicación lo transforma con la clave compartida con su interlocutor antes de enviarlo. Así, confidencialidad e integridad convierten un mensaje recibido en algo en lo que se puede confiar: ilegible para terceros y fiel al original.

## Cómo se conecta con lo anterior y lo siguiente
Desde la clave criptográfica, el prerequisito de esta nota, se desciende a las dos propiedades que la aplicación exige de los mensajes que envía y recibe: qué garantiza exactamente la transformación con clave frente a la lectura y frente a la alteración, y por qué son exigencias separadas. Esta nota cierra el recorrido iniciado en [[seguridad-aplicacion-con-red]], donde ambas propiedades se introdujeron juntas como parte de la seguridad del intercambio; aquí se separan y se definen con precisión, sin asignarles un `conduce_a` posterior.

## Límites de esta explicación
Esta nota no desarrolla los mecanismos criptográficos concretos que proporcionan ambas propiedades, ni cómo se generan, acuerdan o custodian las claves; eso pertenece al prerequisito sobre criptografía con clave. Tampoco trata cómo se acredita la identidad del interlocutor, que corresponde a la [[autenticacion]] dentro de la [[sesion]], ni la disponibilidad de la información, que es una propiedad distinta de estas dos.

## Referencias
- [FTE-0001] *Operating Systems: Three Easy Pieces*: respaldo general de que las propiedades de protección de un sistema se definen frente a usuarios no autorizados, como marco de la distinción entre leer y alterar.
- [FTE-0002] *Modern Operating Systems*: respaldo general de que la aplicación depende de los servicios del equipo y de la red para entregar datos que la persona puede usar, como contexto del intercambio protegido.
