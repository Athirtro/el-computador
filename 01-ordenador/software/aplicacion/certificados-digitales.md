---
titulo: "Certificados digitales"
slug: certificados-digitales
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [seguridad-aplicacion-con-red]
conduce_a: [criptografia-clave]
alias: ["certificado digital", "digital certificate"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Certificados digitales

## Idea central
Un certificado digital es un documento firmado que une la identidad de un servidor con una clave pública, para que el cliente pueda comprobar que está hablando con quien dice ser antes de enviarle datos o fiarse de su respuesta. Resuelve la parte de identidad que la [[seguridad-aplicacion-con-red]] planteaba como problema, sin explicar aquí la criptografía que lo hace posible.

## Antes de empezar
- [[seguridad-aplicacion-con-red]]: la aplicación con red necesita autenticar al interlocutor remoto y proteger los datos en tránsito, porque la dirección por sí sola no garantiza la identidad.

## Explicación
En [[aplicacion-con-red]], el cliente pide información a un [[servidor]] y acepta su respuesta. La dirección del servidor, vista en [[direccion-web]], dice a qué equipo se conecta, pero no prueba que ese equipo sea el propietario legítimo de ese nombre: cualquier otro equipo podría responder en su lugar. El cliente necesita una forma de comprobar la identidad del servidor sin tener que confiar a ciegas en la primera respuesta que recibe. Ese hueco lo ocupa el certificado digital.

Un certificado digital es un documento que contiene, junto a otros datos de identificación, la identidad que se quiere acreditar —normalmente el nombre del servidor— y una clave pública. La clave pública es la parte de un par de claves que puede darse a conocer a cualquiera, mientras que la clave privada, su pareja, permanece secreta en poder del servidor y sirve para demostrar que es quien dice ser, como se verá en [[criptografia-clave]]. Quien posee la clave privada puede realizar operaciones que solo él puede hacer, y quien solo tiene la pública puede comprobarlas; el certificado permite al cliente iniciar esa comprobación sabiendo a qué identidad pertenece esa clave pública.

El problema siguiente es quién firma ese documento. Si el propio servidor pudiera firmarse su certificado y el cliente aceptara cualquier firma, la comprobación no aportaría nada: un impostor firmaría el suyo con la misma facilidad. Por eso existe una tercera parte, una autoridad certificadora, que es una organización de confianza que comprueba la identidad del solicitante y firma el certificado. El cliente, por ejemplo un [[navegador-web]], trae de fábrica una lista de autoridades en las que confía; cuando un certificado está firmado por una de ellas, el cliente acepta la unión entre nombre y clave pública que el documento afirma. Cuando no lo está, o está caducado, o el nombre no coincide con el servidor al que se conecta, el cliente debe sospechar y advertir, porque aceptar a ciegas ese certificado equivaldría a no comprobar nada.

Así, el uso habitual es el siguiente. El [[servidor-web]] presenta su certificado al cliente al comienzo de la comunicación, antes de intercambiar datos sensibles. El cliente verifica la firma de la autoridad, la vigencia y que la identidad del certificado es la esperada. Solo si la comprobación es satisfactoria, continúa y utiliza la clave pública del certificado para proteger la comunicación posterior. Si la comprobación falla, una aplicación bien diseñada no debe enviar sus datos ni tratar las respuestas como procedentes del servidor legítimo. El certificado, por tanto, no cifra por sí solo ni hace segura la aplicación: es la credencial que permite a la aplicación decidir a quién entrega su confianza.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[seguridad-aplicacion-con-red]] se desciende a este peldaño porque autenticar al interlocutor remoto exige algo más que pedir credenciales como en [[autenticacion]]: el cliente necesita una manera de verificar la identidad de un servidor al que no conoce de antemano, sin compartir un secreto previo con él. El certificado resuelve ese momento de presentación de la identidad. El paso siguiente, [[criptografia-clave]], desciende un nivel más y explica el mecanismo de claves públicas y privadas que hace posible firmar el certificado y comprobar esa firma.

## Límites de esta explicación
Esta nota no explica cómo se generan ni cómo funcionan las claves, ni los algoritmos de cifrado y firma, ni la estructura interna del documento; eso corresponde a [[criptografia-clave]]. Tampoco trata la organización completa del sistema de autoridades que emiten y revocan certificados, ni los protocolos concretos que los utilizan, ni la autenticación de personas mediante credenciales, tema ya visto en [[autenticacion]] y [[credenciales]].

## Referencias
- [FTE-0001] *Operating Systems: Three Easy Pieces*: respaldo del contexto de sistema y de la distinción entre el equipo local y el servicio remoto, usado solo como marco general; no cubre el detalle de certificados.
- [FTE-0002] *Modern Operating Systems*: respaldo del papel del sistema operativo como intermediario entre la aplicación y el equipo local, frente a la comunicación con el equipo remoto; no cubre el detalle de certificados.
