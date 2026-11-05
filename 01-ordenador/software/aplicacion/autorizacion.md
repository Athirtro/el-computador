---
titulo: "Autorización"
slug: autorizacion
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [sesion]
conduce_a: []
alias: ["authorization"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Autorización

## Idea central
La autorización decide qué operaciones puede realizar una identidad ya autenticada dentro de una sesión abierta, una vez comprobado quién es. Su papel es delimitar el subconjunto de operaciones que la aplicación permite a esa identidad y denegar el resto, sin confundir la comprobación de identidad con el permiso para actuar.

## Antes de empezar
- [[sesion]]: periodo abierto tras una autenticación aceptada, durante el cual el servidor reconoce al mismo interlocutor mediante un identificador de sesión sin exigir de nuevo las [[credenciales]].
- [[autenticacion]]: procedimiento que comprueba la identidad del interlocutor. Responde a quién es, no a qué puede hacer.
- [[credenciales]]: secreto que se presenta durante la autenticación, como nombre de usuario y contraseña.

## Explicación
La distinción entre autenticación y autorización es el punto de partida. La autenticación establece que una identidad es la que afirma ser; la autorización parte de esa identidad reconocida en la [[sesion]] y pregunta qué operaciones están permitidas para ella. De ahí que una sesión abierta no signifique acceso unrestricted: el identificador de sesión prueba quién actúa, pero no concede por sí mismo ninguna capacidad sobre los datos o funciones de la aplicación.

Un permiso, en este contexto, es una autorización concreta para realizar una operación determinada sobre un objeto determinado, es decir, leer, modificar o eliminar una información, o ejecutar una función de gestión dentro de la aplicación. Por ejemplo, dentro de una [[aplicacion-con-red]], una cuenta puede estar autorizada a consultar sus propios datos y denegada a consultar los de otra cuenta, aunque ambas cuentas compartan la misma sesión abierta. La decisión se toma antes de ejecutar la operación: si el permiso no consta, la aplicación deniega la operación, aunque la identidad sea válida.

Puesto que una identidad puede ser una [[usuario-de-sistema]] concreta, las reglas que asocian operaciones a identidades suelen expresarse mediante una [[lista-de-control-de-acceso]], que enumera las acciones permitidas para cada usuario, grupo u otro sujeto reconocido. Esos permisos pueden agruparse en un rol, que es un conjunto de permisos asignados en bloque a todas las cuentas que cumplen una misma función dentro de la aplicación. De este modo, la aplicación no decide cada caso desde cero, sino que comprueba si la sesión activa corresponde a una identidad con permiso o rol suficiente para la operación solicitada.

La denegación no equivale a cerrar la sesión ni a impugnar la autenticación: es la respuesta prevista cuando la identidad autenticada no está autorizada para una operación concreta. El usuario permanece reconocido mientras la sesión siga abierta, pero esa operación concreta queda vetada. Si la cuenta pierde su permiso o su rol, o si la sesión sigue abierta tras un cambio de estado, las operaciones posteriores son juzgadas conforme a la situación vigente. Así, autorización y sesión son dos controles independientes y sucesivos, donde el primero acota qué puede hacerse dentro del segundo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sesion]] se desciende a este peldaño porque una vez resuelta la pregunta de cómo el servidor reconoce a la misma identidad entre peticiones, queda la pregunta de qué le permite hacer a esa identidad reconocida. La autorización responde a esa pregunta como el último eslabón de este recorrido: convierte el reconocimiento mantenido por la sesión en un límite operativo sobre las acciones permitidas. Al no tener conduce_a en este momento, esta nota cierra la rama de este curso de lectura; cualquier desarrollo posterior de políticas de permisos partiría de esta decisión entre permitir y denegar.

## Límites de esta explicación
Esta nota no desarrolla el detalle de los permisos que el sistema operativo impone sobre archivos en el sistema de archivos, tratados en [[permisos-de-archivos]], ni el modo en que el núcleo regula el acceso privilegiado al hardware, descrito en [[modo-privilegiado]]. Tampoco trata la verificación de la identidad ni la custodia de las credenciales, que corresponden a [[autenticacion]] y [[credenciales]], ni la apertura y el cierre de la sesión, cubiertos en [[sesion]].

## Referencias
- [FTE-0001] *Operating Systems: Three Easy Pieces*: respaldo de la distinción entre la identidad verificada y el acceso que se permite a esa identidad dentro del periodo en que permanece activa.
- [FTE-0002] *Modern Operating Systems*: respaldo de la función de la aplicación como intermediario que conserva el estado de quien usa el servicio y acota las operaciones que admite por petición.
