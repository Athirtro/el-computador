---
titulo: "Extent"
slug: extent
rama: software
categoria: sistema
nivel: 7
prerequisitos: [ext4]
conduce_a: []
alias: ["extensión contigua", "extent"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Extent

## Idea central
Un extent es un rango contiguo de bloques de disco que pertenecen al mismo archivo: un bloque inicial y una longitud. En lugar de anotar bloque a bloque dónde está cada trozo de un archivo, el sistema anota unos pocos rangos completos, lo que ahorra espacio de metadatos y facilita leer el archivo de forma seguida.

## Antes de empezar
- [[ext4]]: el sistema de archivos de Linux en el que aparece el extent como forma de localizar los bloques de cada archivo, frente a anotarlos uno por uno.

## Explicación
En un [[sistema-de-archivos]] el disco se divide en bloques, unidades fijas de almacenamiento numeradas de forma consecutiva. Cada archivo ocupa uno o varios de esos bloques y el sistema debe recordar, en los metadatos de cada archivo, cuáles son. Esos metadatos viven asociados al archivo en su [[inodo]], sin que esta nota entre en su estructura interna.

El problema aparece con los archivos grandes. Si cada bloque se anota por separado, un archivo de miles de bloques necesita miles de anotaciones y localizarlo punto por punto pierde la ventaja de que, en la práctica, sus bloques suelen estar juntos en el disco. La anotación bloque a bloque también ocupa más espacio de metadatos y obliga a más consultas al leer el archivo.

Un extent resuelve ese problema agrupando por rangos. En lugar de una lista de bloques individuales, el sistema guarda pares de comienzo y longitud: por ejemplo, un rango que empieza en un bloque determinado y abarca cien bloques consecutivos. El archivo queda descrito como una sucesión de esos rangos, normalmente pocos, aunque su tamaño total sea grande. Leer el archivo consiste entonces en recorrer cada rango de forma seguida.

La contigüidad tiene además una consecuencia práctica: cuando los bloques de un archivo están seguidos, el dispositivo de almacenamiento puede transferirlos en una sola operación secuencial, más rápida y con menos movimientos que ir saltando de un bloque a otro disperso por el disco. Por eso el extent no es solo una forma compacta de anotar, sino también una herramienta para mantener juntos los datos de un archivo y evitar su dispersión en fragmentos separados. El control de qué bloques están libres para formar rangos nuevos se apoya en el [[mapa-de-bloques-libres]].

## Cómo se conecta con lo anterior y lo siguiente
Desde [[ext4]] se baja a este peldaño al pasar del sistema de archivos en general a su forma de localizar los datos de cada archivo: ya se sabe que ext4 ordena el espacio libre de forma más contigua, y el extent es el mecanismo concreto que expresa esa contigüidad como rangos. Esta nota es terminal en el contrato asignado, sin `conduce_a`; su función es cerrar la idea de localización por rangos, sobre la que otras notas internas de ext4 podrían apoyarse.

## Límites de esta explicación
Esta nota no desarrolla la estructura interna de ext4 —ni el formato exacto de sus tablas de extents, ni sus límites, ni cómo convive con otras formas de localización—, que queda fuera por el alcance asignado. Tampoco trata la [[journaling]] ni el [[mapa-de-bloques-libres]] en detalle, ni otros sistemas de archivos que usan rangos con nombres distintos.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): organización de archivos en bloques y localización de los bloques de cada archivo en el sistema de archivos.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): metadatos de archivo y organización de los bloques en sistemas tipo Unix.
