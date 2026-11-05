---
titulo: "Criptografía de clave"
slug: criptografia-clave
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [certificados-digitales]
conduce_a: [confidencialidad-integridad]
alias: ["criptografía con clave", "cryptography with key"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Criptografía de clave

## Idea central
La criptografía de clave es el procedimiento por el que un mensaje se transforma con una clave para que solo quien la posee pueda recuperar el contenido original. La clave es un valor secreto que define la transformación: si la clave se protege y se entrega solo al destinatario, el mensaje cifrado no revela el original a quien lo intercepta.

## Antes de empezar
- [[certificados-digitales]]: el documento que asocia una clave pública a una identidad, para que el emisor pueda verificar a quién entrega la clave simétrica.

## Explicación
En [[seguridad-aplicacion-con-red]] se vio que una aplicación con red necesita saber con quién habla y proteger los datos mientras viajan. La criptografía de clave responde al segundo problema: antes de enviar el mensaje, el emisor lo transforma con una clave y produce un texto cifrado; el destinatario aplica la clave inversa y recupera el mensaje original. Quien no dispone de la clave obtiene solo el texto ilegible. El término en inglés, criptografía (cryptography), se usa para el conjunto de estas transformaciones con clave.

Existen dos formas principales de usar la clave. En la criptografía de clave simétrica, emisor y destinatario comparten la misma clave secreta, o claves equivalentes en cuanto a su efecto: lo que uno cifra con su clave lo descifra el otro con la suya. Es eficaz para mensajes largos, pero obliga a acordar y proteger el secreto antes de hablar y a repetir el acuerdo con cada interlocutor. Si la clave se filtra, cualquier tercero puede leer y alterar los mensajes posteriores.

En la criptografía de clave asimétrica, cada participante dispone de un par de claves vinculadas: una pública, que puede entregarse a cualquiera, y una privada, que solo guarda su propietario. Lo que se cifra con la clave pública solo se descifra con la privada correspondiente, y lo que se cifra con la privada puede verificarse con la pública. Esto permite iniciar una conversación con un interlocutor desconocido sin compartir antes un secreto: el destinatario entrega su clave pública y el emisor cifra con ella el mensaje o una clave simétrica efímera. El precio es que el procedimiento asimétrico es más lento, por lo que en la práctica se usa para autenticar al interlocutor y acordar una clave simétrica que cifra el grueso del mensaje.

En ambos casos, la seguridad descansa en la custodia de la clave secreta y en la verificación de que la clave pública entregada corresponde efectivamente al destinatario esperado. Si un impostor sustituye su clave pública por la del destinatario, el emisor cifrará para el impostor sin que el procedimiento lo detecte por sí solo. Por eso el uso de claves asimétricas se combina con [[certificados-digitales]], que vinculan la clave pública a una identidad.

## Cómo se conecta con lo anterior y lo siguiente
Este peldaño desciende desde la necesidad de proteger los datos en tránsito descrita en [[seguridad-aplicacion-con-red]] y en [[aplicacion-con-red]]: el intercambio cliente-servidor, explicado en [[cliente-servidor]] y [[protocolo-de-red]], queda incompleto si no se explica qué ocurre con la clave compartida. Desde aquí se conduce a [[confidencialidad-integridad]], donde se desarrollan las propiedades de confidencialidad e integridad que la clave hace posibles, sin repetir en esta nota su detalle.

## Límites de esta explicación
Esta nota no desarrolla los algoritmos concretos de cifrado simétrico ni asimétrico, ni la gestión de claves de larga vida, ni el detalle de la confidencialidad y la integridad, tema de [[confidencialidad-integridad]]. Tampoco trata la verificación de identidad del interlocutor más allá de su apoyo en [[certificados-digitales]], ni la [[autenticacion]] de usuarios en [[sesion]].

## Referencias
- [FTE-0001] *Operating Systems: Three Easy Pieces*: respaldo general del papel del sistema operativo como intermediario entre la aplicación y los servicios del equipo, que delimita por contraste la protección del mensaje en tránsito por red; no desarrolla criptografía.
- [FTE-0002] *Modern Operating Systems*: respaldo general de la separación entre seguridad local y comunicación con el equipo remoto; no desarrolla criptografía.
