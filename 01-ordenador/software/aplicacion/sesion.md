---
titulo: "Sesión"
slug: sesion
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [seguridad-aplicacion-con-red]
conduce_a: [autorizacion]
alias: ["sesión de usuario", "session"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Sesión

## Idea central
Una sesión es el periodo abierto entre una autenticación aceptada y su cierre, durante el cual el servidor reconoce al mismo interlocutor sin que este repita sus credenciales. Existe porque en una aplicación con red cada petición se hace por separado y el servidor, por sí mismo, no recuerda a quien atiende.

## Antes de empezar
- [[seguridad-aplicacion-con-red]]: la aplicación con red debe comprobar con quién habla y proteger los datos en tránsito antes de entregar el resultado a la persona.
- [[autenticacion]]: el procedimiento por el que la aplicación comprueba la identidad del interlocutor presentando y contrastando una credencial.
- [[credenciales]]: el secreto —por ejemplo, nombre de usuario y contraseña— que se presenta para ser contrastado.

## Explicación
En [[aplicacion-con-red]] el cliente envía peticiones independientes y el servidor las atiende una a una: nada en una petición aislada indica que quien la envía sea la misma persona que envió la anterior. Si cada petición exigiera de nuevo la credencial, la aplicación sería impracticable y, además, multiplicaría la exposición del secreto en la red. La sesión resuelve ese problema abriendo, tras una autenticación aceptada, un periodo durante el cual el servidor trata como conocido al interlocutor que presenta la referencia correspondiente.

Esa referencia es un identificador de sesión: un valor opaco, sin significado propio, que el servidor asocia a la identidad ya autenticada y que el cliente devuelve en cada petición posterior dentro del periodo. El cliente no necesita reproducir su contraseña; basta con presentar el identificador, y el servidor lo busca en su registro de sesiones abiertas para saber a qué identidad corresponde. Si el identificador no aparece, ha caducado o ya fue cerrado, el servidor no debe atender la petición como si procediera de un usuario autenticado, sino exigir una autenticación nueva.

La sesión tiene, por tanto, un principio y un final. Comienza cuando [[autenticacion]] concluye con éxito y termina cuando el usuario la cierra, cuando caduca tras un tiempo de inactividad o cuando el servidor la invalida. El cierre no es un mero gesto de despedida: borra la asociación entre el identificador y la identidad, de modo que ese identificador deja de ser válido aunque alguien lo conserve. Del mismo modo, mientras la sesión sigue abierta, el identificador funciona como una prueba de identidad de corta duración, por lo que su pérdida equivale a perder el acceso durante ese periodo.

La sesión no sustituye a la autenticación ni a la protección de los datos en tránsito: la primera la crea y la segunda protege el contenido de cada mensaje, incluidos el propio identificador. Tampoco decide qué puede hacer la persona ya reconocida dentro del periodo; eso pertenece al paso siguiente del recorrido. Su único papel es mantener el reconocimiento entre peticiones hasta el cierre.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[seguridad-aplicacion-con-red]] se desciende a este peldaño porque la autenticación, una vez aceptada, plantea una pregunta inmediata: cómo sigue el servidor sabiendo, en cada petición posterior, que quien escribe es el mismo interlocutor ya comprobado. La sesión responde a esa pregunta con el periodo abierto y el identificador que lo sostiene, sin repetir la autenticación en cada intercambio. A partir de esa identidad mantenida, la nota siguiente del recorrido podrá decidir qué operaciones quedan permitidas dentro de la sesión abierta.

## Límites de esta explicación
Esta nota no desarrolla qué operaciones están permitidas dentro de una sesión una vez reconocida la identidad; eso corresponde a la nota posterior de autorización, que el lector encontrará como paso siguiente en el recorrido. Tampoco trata los mecanismos concretos de cifrado y de protección de los datos en tránsito, ya cubiertos en [[seguridad-aplicacion-con-red]], ni la custodia de las credenciales en sí, tratada en [[credenciales]].

## Referencias
- [FTE-0001] *Operating Systems: Three Easy Pieces*: respaldo de la distinción entre la cuenta de usuario autenticada una vez y el reconocimiento que se mantiene mientras esa cuenta sigue activa.
- [FTE-0002] *Modern Operating Systems*: respaldo de la función del sistema y de la aplicación como intermediarios que conservan el estado de quien usa el servicio, frente a peticiones aisladas sin memoria.
