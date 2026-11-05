---
titulo: "NTFS"
slug: ntfs
rama: software
categoria: sistema
nivel: 6
prerequisitos: [tipos-de-sistema-de-archivos]
conduce_a: []
alias: ["sistema de archivos NTFS", "New Technology File System"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# NTFS

## Idea central
NTFS (New Technology File System) es el sistema de archivos habitual de Windows: organiza archivos y carpetas en discos grandes y guarda, junto a cada archivo, la información necesaria para decidir quién puede leerlo o modificarlo. Su pieza central es la tabla maestra de archivos, donde el sistema registra todo lo que existe en el volumen.

## Antes de empezar
- [[tipos-de-sistema-de-archivos]]: cada tipo de sistema de archivos aplica las ideas generales de [[sistema-de-archivos]] con reglas propias sobre nombres, tamaños y permisos.

## Explicación
NTFS apareció con Windows NT como sistema de archivos de propósito general y se convirtió en el predeterminado de las versiones de Windows posteriores, incluidas Windows XP, Vista, 7, 10 y 11. Frente a FAT32, admite volúmenes y archivos individuales muy grandes, nombres largos y, sobre todo, control de acceso por usuario: no es una simple lista de nombres, sino una estructura que conserva metadatos de cada objeto. Esos metadatos son los datos «sobre los datos»: propietario, fechas, atributos y permisos, guardados por el propio sistema de archivos y no por cada programa.

La tabla maestra de archivos (Master File Table, MFT) es el índice central de NTFS. Cada archivo o carpeta —e incluso los archivos internos del propio sistema de archivos— tiene una entrada numerada en la MFT. En esa entrada se guardan atributos como el nombre, la información estándar (tamaños y fechas) y el atributo que contiene los datos del archivo; cuando los datos no caben en la entrada, la entrada guarda referencias a los bloques del disco donde están. Gracias a esa numeración, el sistema puede localizar un archivo sin recorrer toda la jerarquía de carpetas y puede mantener información adicional sin tocar el contenido. La propia MFT es un archivo especial del volumen, lo que le permite crecer de forma ordenada a medida que se crean archivos.

Los permisos se expresan mediante listas de control de acceso: para cada archivo o carpeta, NTFS guarda una lista de entradas que vinculan usuarios o grupos con acciones permitidas o denegadas, como leer, escribir o modificar. Esas entradas se apoyan en las cuentas del sistema, tratadas en [[usuario-de-sistema]], y el propietario puede cambiarlas. Los permisos normalmente se heredan de la carpeta contenedora, de modo que al crear un archivo en una carpeta protegida este recibe las reglas de su padre, aunque el propietario puede ajustarlas después. Esta es la diferencia práctica respecto a un sistema sin permisos reales: en NTFS «quién puede tocar qué» forma parte de la organización del disco, como se introduce en [[permisos-de-archivos]].

NTFS también protege la consistencia del volumen con un registro de cambios: anota las operaciones antes o mientras se aplican, de modo que tras un corte de corriente o un fallo el sistema puede rehacer o deshacer las escrituras incompletas. Ese mecanismo es el [[journaling]] aplicado a este tipo concreto, y es otra razón por la que NTFS se usa en el disco principal de Windows y no solo en medios extraíbles compartidos.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[tipos-de-sistema-de-archivos]] se pasa a esta nota al elegir uno de los tres tipos comparados: aquí se desarrolla el caso de Windows. Lo anterior aporta la idea de archivos, carpetas y límites; esta nota añade cómo NTFS los implementa con la MFT y los permisos por usuario. No hay una nota siguiente asignada en el contrato, por lo que la cadena queda abierta a medida que el mapa añada los conceptos internos que NTFS necesita, como la tabla maestra como concepto propio o las listas de control de acceso.

## Límites de esta explicación
Esta nota no desarrolla el sistema de archivos de Linux, tratado en [[ext4]], ni el formato FAT32, comparado en [[tipos-de-sistema-de-archivos]]. Tampoco detalla la estructura binaria de la MFT, los atributos internos, la compresión ni el cifrado de NTFS, ni las herramientas de recuperación y reparación de volúmenes dañados. El mecanismo general de registro de cambios se trata en [[journaling]] y los permisos en general en [[permisos-de-archivos]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): los tipos de sistema de archivos como reglas concretas de organización y los metadatos asociados a cada archivo.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): los sistemas de archivos como parte del sistema operativo y la necesidad de control de acceso y consistencia.
