---
titulo: "Registro de usuarios"
slug: registro-de-usuarios
rama: software
categoria: sistema
nivel: 7
prerequisitos: [usuario-de-sistema]
conduce_a: []
alias: ["base de datos de usuarios", "user database"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Registro de usuarios

## Idea central
El registro de usuarios es el lugar del [[sistema-de-archivos]] donde el [[sistema-operativo]] guarda de forma persistente las cuentas y los grupos definidos en [[usuario-de-sistema]]. Sin ese registro, al reiniciar el sistema se perdería la lista de quiénes pueden iniciar sesión, a qué grupo pertenece cada cuenta y con qué identificador trabaja.

## Antes de empezar
- [[usuario-de-sistema]]: qué es una cuenta, qué es un grupo y por qué el sistema atribuye todo lo creado a una cuenta.

## Explicación
Una cuenta definida en [[usuario-de-sistema]] no vive solo mientras dura una sesión: el sistema la escribe en disco para poder reconocerla después de cada arranque. Ese conjunto de archivos y bases de datos de solo el sistema es el registro de usuarios. Guarda, por cada cuenta, su nombre de acceso, un identificador numérico estable que la distingue aunque cambie de nombre, su grupo principal, el directorio personal donde se guardan sus archivos propios y el programa que se ejecuta al iniciar sesión. Guarda también, por cada grupo, su nombre, su identificador numérico y la lista de cuentas que lo forman.

En los sistemas de tipo Unix, el registro clásico está formado por dos archivos de texto en el directorio de configuración del sistema: uno enumera las cuentas con sus datos descriptivos, y otro enumera los grupos con sus miembros. La información de cada cuenta queda así separada de la información de cada grupo, de modo que para saber a qué grupos pertenece un usuario hay que consultar el archivo de grupos, y para saber cuál es el grupo principal de la cuenta hay que consultar el archivo de cuentas. Cuando una cuenta se crea o se elimina, o cuando cambia de grupo, el sistema modifica estos archivos y el cambio queda guardado en disco, por lo que sobrevive a reinicios y puede consultarlo cualquier programa del sistema que necesite resolver un nombre de usuario o de grupo.

La separación entre el registro y los procesos en ejecución es esencial: el registro dice qué cuentas existen en el sistema, mientras que cada proceso ejecutándose lleva asociado, en su propio estado, el identificador de la cuenta en cuyo nombre trabaja. Al iniciar sesión, el sistema compara lo que presenta el usuario con lo que dice el registro y, si coincide, pone en marcha una sesión con ese identificador. Si la cuenta no figura en el registro, no puede iniciar sesión aunque la persona exista físicamente.

## Cómo se conecta con lo anterior y lo siguiente
[[usuario-de-sistema]] definió qué es una cuenta y qué es un grupo; esta nota explica dónde quedan guardados. Es la respuesta a la pregunta que aquella dejaba abierta al suspender la administración de cuentas: el registro es el soporte persistente de esa administración. No tiene un `conduce_a` previsto, porque el detalle de cómo se conceden los permisos usando esa información ya se trató en [[permisos-de-archivos]].

## Límites de esta explicación
Esta nota no entra en el detalle de los permisos concedidos a cada cuenta o grupo, tratado en [[permisos-de-archivos]], ni en cómo el sistema guarda y protege las credenciales de acceso, que merecen una nota propia. Tampoco describe los mecanismos propios de otros sistemas distintos de los de tipo Unix: en ellos la información equivale a la descrita, pero puede guardarse en bases de datos internas en lugar de en archivos de texto.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): identidad de usuario, propietarios y grupos como información que el sistema mantiene de forma persistente.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): cuentas de usuario y grupos en sistemas tipo Unix y su almacenamiento en archivos de configuración del sistema.
