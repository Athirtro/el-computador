---
titulo: "Lista de control de acceso"
slug: lista-de-control-de-acceso
rama: software
categoria: sistema
nivel: 7
prerequisitos: [ntfs, permisos-de-archivos]
conduce_a: []
alias: ["ACL", "access control list"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Lista de control de acceso

## Idea central
La lista de control de acceso (access control list, ACL) es la estructura con la que [[ntfs]] expresa, para cada archivo o carpeta, quién puede hacer qué. En lugar de un único propietario y tres categorías fijas, una ACL es una lista de entradas que vinculan usuarios y grupos concretos con acciones permitidas o denegadas sobre ese objeto.

## Antes de empezar
- [[ntfs]]: el sistema de archivos de Windows, donde cada archivo y carpeta guarda, junto a sus metadatos, las reglas que deciden quién puede leerlo o modificarlo.
- [[permisos-de-archivos]]: la idea general de que cada archivo tiene un propietario y unas reglas de lectura y escritura que el sistema operativo comprueba antes de permitir una operación.

## Explicación
En [[permisos-de-archivos]] los permisos se introdujeron como una regla sobre el propietario y, de forma más general, los demás usuarios. La ACL es una manera concreta y más expresiva de guardar esa regla en un sistema como [[ntfs]]: en vez de clasificar a todo el mundo en unas pocas casillas, el sistema guarda una lista ordenada de entradas, una por cada concesión o denegación que se quiera aplicar a un sujeto concreto.

Cada entrada de la lista responde a tres preguntas: a quién se aplica (un [[usuario-de-sistema]] o un grupo de usuarios), qué acción regula (leer, escribir o modificar, entre otras) y si esa acción se permite o se deniega para ese sujeto sobre ese archivo o carpeta. Con esa información, cuando un usuario intenta abrir un archivo, el sistema operativo no pregunta solo «¿es el propietario?», sino que recorre la ACL del objeto en busca de entradas que se refieran a él o a los grupos a los que pertenece, y actúa según lo que esas entradas digan.

Esa granularidad es la ventaja práctica de la ACL frente al modelo simple de propietario y categorías. Permite, por ejemplo, que dos usuarios distintos tengan derechos diferentes sobre el mismo archivo sin que ninguno sea su propietario, o que un grupo de trabajo reciba permiso de lectura mientras otro grupo recibe permiso de escritura. Cada entrada se evalúa por separado, de modo que el conjunto de la lista describe el acceso completo al objeto en lugar de reducirlo a una sola etiqueta. La ACL pertenece al objeto protegido —archivo o carpeta— y no a los programas que lo abren: cualquier programa que actúe con los datos de un usuario recibido queda sujeto a las entradas que se refieran a ese usuario.

Las entradas también pueden heredarse: una carpeta guarda su propia lista y los archivos y subcarpetas que se crean dentro de ella reciben, por defecto, las reglas de su contenedora, tal como ya se apuntó en [[ntfs]]. El propietario —o un usuario con derecho a cambiar los permisos— puede después añadir, quitar o modificar entradas concretas sin cambiar las demás. Así, la herencia evita repetir la misma lista en cada objeto nuevo, mientras que la posibilidad de ajustar entradas individuales permite tratar las excepciones sin debilitar la regla general de la carpeta.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[permisos-de-archivos]] se pasa a la ACL al buscar una representación concreta de la regla «quién puede leer o escribir en cada archivo», y desde [[ntfs]] al tomar el sistema de archivos que la implementa con listas de entradas por usuario y grupo. Esta nota es una rama terminal: no tiene un `conduce_a` asignado en el contrato y no hace falta para entender la organización de archivos ni sus formatos.

## Límites de esta explicación
Esta nota no desarrolla la estructura interna de la tabla en la que [[ntfs]] guarda la ACL ni el detalle de las entradas de la tabla maestra de archivos, tratado en [[tabla-maestra-de-archivos]]. Tampoco trata la creación y administración de las cuentas y grupos a los que se refieren las entradas, que se tratan en [[usuario-de-sistema]], ni las operaciones de ejecución, tratadas en [[ejecucion-de-archivos]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): protección de archivos y control de acceso por usuario como parte de la organización del sistema de archivos.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): permisos y listas de control de acceso como mecanismo de protección en sistemas de archivos.
