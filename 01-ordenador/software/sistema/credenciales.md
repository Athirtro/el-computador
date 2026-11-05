---
titulo: "Credenciales"
slug: credenciales
rama: software
categoria: sistema
nivel: 7
prerequisitos: [usuario-de-sistema]
conduce_a: [autenticacion]
alias: ["nombre de usuario y contraseña", "credentials"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Credenciales

## Idea central
Las credenciales son la pareja de datos secretos con la que una cuenta demuestra que quien actúa en su nombre es su titular: un identificador público, el nombre de usuario, y un secreto que solo debería conocer ese titular, la contraseña. Sin credenciales, la cuenta definida en [[usuario-de-sistema]] sería solo un nombre sin ningún medio de reclamar su identidad; con ellas, el sistema puede distinguir a quien simplemente conoce el nombre de quien además conoce el secreto asociado a él.

## Antes de empezar
- [[usuario-de-sistema]]: la cuenta, con su nombre, sus grupos y su condición de propietaria de archivos y responsable de procesos, a la que las credenciales se refieren.

## Explicación
El nombre de usuario por sí solo no es una credencial secreta: es el identificador con el que el sistema localiza la cuenta, y cualquiera a quien se le dijo puede conocerlo. La credencial propiamente dicha es la contraseña (password en inglés): el secreto que el titular no comparte y que el sistema asocia a ese nombre. Cuando alguien se presenta diciendo ser un determinado usuario, lo que afirma conocer es esa contraseña; la cuenta no puede reclamar su identidad solo por enunciar su nombre.

Por eso las credenciales no se custodian como un dato cualquiera de la cuenta. El sistema las guarda en una zona protegida, separada de los datos ordinarios de los archivos y accesible solo para el propio sistema o para quien lo administre legítimamente, como se describió al tratar la protección de cuentas y propietarios en [[usuario-de-sistema]] y [[registro-de-usuarios]]. Esa custodia implica dos reglas: la contraseña en claro no debería quedar escrita en archivos accesibles a las aplicaciones, y el sistema no debería devolverla a quien la pida, sino conservar únicamente una forma transformada de la que no pueda recuperarse el secreto original, pensada solo para poder comprobar después si un candidato coincide. Compartir la contraseña con otra persona equivale a entregar la identidad de la cuenta: todo lo hecho con ella parecerá hecho por su titular, y se pierde la trazabilidad de quién actuó, tal como se advertía en [[usuario-de-sistema]].

Las credenciales son, en síntesis, un secreto compartido solo entre el titular y el sistema, ligado a una cuenta concreta. Su valor no está en el nombre, público, sino en que el secreto no se conoce ni se difunde; por eso su custodia es lo que hace que la identidad de la cuenta sea algo más que una etiqueta.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[usuario-de-sistema]] se da un paso más: aquella nota definió la cuenta, sus grupos y su papel como propietaria, pero no explicó con qué secreto se reclama. Esta nota añade ese secreto y cómo debe guardarse. El paso siguiente es [[autenticacion]], que explicará el proceso completo por el que el sistema comprueba un candidato a credencial y decide si acepta a quien se presenta como titular de la cuenta.

## Límites de esta explicación
Esta nota no describe el proceso de comprobación de la credencial, los intentos de acceso ni las políticas de bloqueo, que se tratan en [[autenticacion]]; tampoco trata los permisos que la cuenta ejerce una vez aceptada su identidad, que corresponden a [[permisos-de-archivos]], ni el detalle de dónde y cómo persiste el registro de cuentas, que corresponde a [[registro-de-usuarios]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): protección de la identidad del usuario y custodia de la información que la acredita en el modelo de protección de un sistema operativo.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): cuentas de usuario y el secreto asociado a cada cuenta como base de la atribución de acciones a su titular.
