---
titulo: "Usuario de sistema"
slug: usuario-de-sistema
rama: software
categoria: sistema
nivel: 6
prerequisitos: [permisos-de-archivos]
conduce_a: []
alias: ["cuenta de usuario", "user account"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Usuario de sistema

## Idea central
Un usuario de sistema es una identidad que el [[sistema-operativo]] reconoce y a la que atribuye todo lo que se hace en su nombre. Sin esa identidad, las reglas de [[permisos-de-archivos]] no tendrían a quién aplicarse: nadie podría ser propietario de un archivo, pertenecer a un grupo ni heredar permisos al lanzar un programa.

## Antes de empezar
- [[permisos-de-archivos]]: las reglas que deciden quién puede leer o escribir en cada archivo y que presuponen usuarios identificables con un propietario por archivo.

## Explicación
Cuando una persona enciende el ordenador y trabaja en él, no lo hace como una figura anónima: lo hace con una cuenta de usuario, es decir, un registro que el sistema guarda con un nombre y con los datos necesarios para distinguirla de las demás cuentas. Cada cuenta es un usuario de sistema. Todo lo que esa persona hace —abrir archivos, crearlos, ejecutar programas— se le atribuye a esa cuenta, y el sistema usa esa atribución para comprobar permisos y para saber a quién pertenece cada archivo nuevo.

Cada cuenta también puede pertenecer a uno o varios grupos: conjuntos de cuentas que comparten los mismos derechos de acceso. Los permisos de un archivo se conceden por categorías —al propietario, al grupo y al resto, como se vio en [[permisos-de-archivos]]—, de modo que pertenecer a un grupo es el modo de recibir derechos sin concederlos a todo el mundo. Un usuario que necesita leer archivos de trabajo de su grupo no necesita un permiso personal en cada archivo: le basta con formar parte del grupo al que esos permisos ya se concedieron.

Entender la cuenta exige distinguir entre quién la usa y qué es. La cuenta no es la persona física, sino el registro que el sistema mantiene de ella; una misma persona puede tener varias cuentas, por ejemplo una de uso diario y otra de administración, y una misma cuenta puede ser usada por varias personas si comparten credenciales, aunque eso rompe la trazabilidad de quién hizo cada cosa. Por eso el sistema además distingue cuentas con privilegios especiales, destinadas a tareas de administración y mantenimiento, de las cuentas ordinarias de trabajo.

Todo lo creado estando dentro de una cuenta —archivos, carpetas y procesos lanzados— queda asociado a ella como propietario o como responsable. Si un programa hace una petición al [[sistema-operativo]] en nombre de un usuario, hereda los derechos de ese usuario, por lo que la identidad de la cuenta es la base sobre la que después se comprueban los permisos concretas de cada archivo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[permisos-de-archivos]] se retrocede un paso: aquellos permisos presuponen cuentas, grupos y propietarios, y esta nota define esos tres elementos. Es una rama terminal: no tiene un `conduce_a` previsto y no hace falta para entender la estructura de archivos ni sus formatos.

## Límites de esta explicación
Esta nota no entra en el detalle de los permisos concretos de lectura y escritura, tratado en [[permisos-de-archivos]], ni en cómo el sistema guarda y protege las credenciales, ni en la administración de cuentas y grupos.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): identidad de usuario, propietarios y grupos en el modelo de protección de un sistema operativo.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): cuentas de usuario, grupos y propiedad como base de los permisos de archivos.
