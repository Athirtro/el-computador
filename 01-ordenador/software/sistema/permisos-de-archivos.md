---
titulo: "Permisos de archivos"
slug: permisos-de-archivos
rama: software
categoria: sistema
nivel: 5
prerequisitos: [sistema-de-archivos]
conduce_a: []
alias: ["permisos de archivo", "file permissions"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Permisos de archivos

## Idea central
Los permisos de archivos son el conjunto de reglas que decide quién puede leer o escribir en cada archivo. Sin ellos, cualquier programa que usara el [[sistema-de-archivos]] podría abrir, modificar o borrar cualquier archivo, sin distinguir entre sus dueños.

## Antes de empezar
- [[sistema-de-archivos]]: el componente del sistema operativo que organiza la información persistente como archivos y carpetas con nombre.

## Explicación
El [[sistema-de-archivos]] no solo guarda los archivos en un lugar con nombre: también guarda información sobre cada archivo, y entre esa información están sus permisos. Un usuario es cada persona identificada ante el sistema operativo por una cuenta propia, que usa al trabajar con el ordenador. Cada archivo tiene un propietario: el usuario que lo creó y que, por defecto, decide quién más puede acceder a él.

La pregunta que responden los permisos es, sobre todo, quién puede hacer dos operaciones: leer el archivo, es decir, ver o copiar su contenido sin cambiarlo, y escribir en él, es decir, modificarlo o sustituirlo. El propietario puede conceder o negar esas operaciones a sí mismo, a un grupo de usuarios y al resto, y cuando otro usuario intenta abrir el archivo, el sistema operativo comprueba su permiso antes de permitir la operación. Si no lo tiene, la apertura se deniega, aunque el archivo sea conocido y su ruta sea correcta.

Conviene distinguir al propietario de los demás usuarios por una razón práctica: crear un archivo no es el único modo de que alguien lo modifique. Cualquier programa que haga una petición con los datos de un usuario recibido heredará los permisos de ese usuario, por lo que un permiso de escritura concedido a mucha gente amplía el número de programas capaces de alterar el archivo. Los permisos no protegen contra un programa que actúe con los permisos del propio propietario, sino contra los usuarios que no los tienen.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sistema-de-archivos]] se llega a los permisos al pasar de la organización visible —archivos y carpetas con nombre— a la regla que decide quién puede usar cada archivo. Esta nota es una rama terminal: no tiene un `conduce_a` previsto y no hace falta para entender la estructura de archivos ni sus formatos.

## Límites de esta explicación
Esta nota no entra en el detalle de los tipos concretos de sistema de archivos, tratado en [[tipos-de-sistema-de-archivos]], ni en operaciones adicionales como la ejecución de un archivo, los atributos especiales ni la creación y administración de las cuentas de usuario.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): permisos y protección en sistemas de archivos.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): permisos y protección en sistemas de archivos.
