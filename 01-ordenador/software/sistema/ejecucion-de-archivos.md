---
titulo: "Ejecución de archivos"
slug: ejecucion-de-archivos
rama: software
categoria: sistema
nivel: 6
prerequisitos: [permisos-de-archivos]
conduce_a: []
alias: ["permiso de ejecución", "execute permission"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Ejecución de archivos

## Idea central
Ejecutar un archivo no es leerlo: es pedir al sistema operativo que lo cargue como si fuera un programa y cree un proceso a partir de él. Para ello existe un tercer permiso, distinto de leer y escribir, que decide si esa petición está permitida.

## Antes de empezar
- [[permisos-de-archivos]]: las reglas que deciden quién puede leer o escribir en cada archivo y que el sistema operativo comprueba antes de abrirlo.

## Explicación
[[permisos-de-archivos]] trata dos operaciones sobre un archivo: leerlo, es decir, ver o copiar su contenido sin cambiarlo, y escribir en él, es decir, modificarlo o sustituirlo. Falta una tercera operación, ejecutar el archivo, que consiste en pedir al sistema operativo que lo interprete como un programa: que lo cargue en memoria y cree un [[proceso]], un programa ya en ejecución con estado propio. Ese permiso de ejecución decide si esa petición está permitida para quien la hace.

La diferencia práctica entre leer y ejecutar es directa. Un archivo puede ser legible pero no ejecutable: su contenido puede leerse o copiarse, pero al intentar ejecutarlo el sistema operativo deniega la operación. También puede ser ejecutable pero no legible: sus instrucciones pueden cargarse y correr sin que quien las ejecuta pueda ver o copiar su contenido. En ese caso, ejecutar no implica leer, y leer no implica ejecutar, porque son dos comprobaciones distintas que el sistema operativo hace sobre el mismo archivo antes de conceder cada operación.

Que un archivo sea ejecutable no significa todavía que pueda ejecutarse con éxito. El sistema operativo que debe cargarlo —el cargador, pieza que introduce un programa en memoria para convertirlo en proceso— necesita reconocer en su contenido instrucciones válidas o un formato que sepa interpretar. Un texto legible sin ese formato se deniega o falla al intentarlo, aunque tenga permiso de ejecución. En el límite, un programa escrito como texto para ser interpretado línea a línea necesita, además del permiso de ejecución, que quien lo interpreta pueda leerlo; en ese caso la ejecución exige en la práctica ambos permisos a la vez. Este detalle pertenece al funcionamiento de los cargadores e intérpretes, no al permiso en sí.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[permisos-de-archivos]] se llega a esta nota al completar el trío de operaciones que los permisos controlan: leer y escribir describen qué se puede hacer con el contenido de un archivo ya abierto, mientras que ejecutar describe la petición de convertir ese archivo en un proceso. Es una rama terminal: no tiene un `conduce_a` previsto y no hace falta para entender la estructura de archivos ni los permisos genéricos.

## Límites de esta explicación
Esta nota no desarrolla los permisos genéricos ni quién los concede, que se tratan en [[permisos-de-archivos]], ni cómo el sistema operativo carga un programa en memoria, que corresponde a los cargadores y a los intérpretes.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): protección y permisos en sistemas de archivos, incluido el permiso de ejecución.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): permisos y protección en sistemas de archivos, incluido el permiso de ejecución.
