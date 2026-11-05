---
titulo: "Tabla maestra de archivos"
slug: tabla-maestra-de-archivos
rama: software
categoria: sistema
nivel: 7
prerequisitos: [ntfs]
conduce_a: []
alias: ["Master File Table", "MFT"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Tabla maestra de archivos

## Idea central
La tabla maestra de archivos es el índice central de [[ntfs]]: una tabla de entradas numeradas donde el sistema registra cada archivo, carpeta y objeto interno del volumen. Gracias a esa numeración, NTFS localiza la información de un archivo sin recorrer toda la jerarquía de carpetas.

## Antes de empezar
- [[ntfs]]: en NTFS todo objeto del volumen tiene una entrada en la tabla maestra, que guarda sus metadatos y las referencias a sus datos.

## Explicación
NTFS, como todo [[sistema-de-archivos]], necesita responder a dos preguntas distintas: dónde están los datos de un archivo y qué información administrativa lo acompaña, como su nombre, su tamaño, sus fechas y quién puede usarlo. Esa información administrativa son los metadatos, ya introducidos en [[ntfs]]. La tabla maestra de archivos, o MFT, es la estructura que centraliza esos metadatos.

La MFT es una tabla de tamaño fijo por entrada: cada archivo o carpeta ocupa una entrada numerada, y el número de esa entrada actúa como su identificador dentro del volumen. Cuando el sistema necesita un archivo, no busca en las carpetas una a una, sino que consulta directamente la entrada que le corresponde y lee en ella el nombre, la información estándar y las referencias a los bloques del disco donde se guardan los datos si estos no caben en la propia entrada. De este modo, la localización de un archivo es una consulta en tabla y no un recorrido de la jerarquía, que es la idea de [[tabla-hash]] aplicada a la organización en disco por [[sistema-de-archivos]].

Las primeras entradas de la tabla están reservadas a los archivos internos del propio sistema de archivos, de modo que NTFS se describe a sí mismo con la misma estructura que usa para los archivos del usuario. La propia MFT es uno de esos archivos especiales, y puede crecer de forma ordenada a medida que se crean archivos en el volumen. Esta comparación con [[inodo]] es útil solo como analogía: el inodo cumple en ext4 una función similar de ficha de metadatos por archivo, pero la MFT es un concepto propio de NTFS y no debe confundirse con él.

Cada entrada de la MFT organiza la información en atributos, es decir, en piezas con nombre y contenido propios: uno guarda el nombre, otro la información estándar, otro los datos del archivo y otro las reglas de acceso. Esta nota solo introduce la existencia de esos atributos; el detalle de las reglas de acceso no forma parte de su alcance.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[ntfs]] se pasa a esta nota al preguntarse cómo implementa NTFS lo que aquella anuncia: la MFT es el mecanismo que hace posible que cada objeto del volumen tenga una ficha numerada y localizable. No hay una nota siguiente asignada en el contrato, por lo que la cadena queda abierta a los conceptos internos que el mapa añada a partir de aquí, como el detalle de los atributos de una entrada.

## Límites de esta explicación
Esta nota no desarrolla el detalle de las listas de control de acceso, tratado en [[permisos-de-archivos]], ni la estructura binaria de cada entrada de la MFT. Tampoco trata los demás [[tipos-de-sistema-de-archivos]], el sistema de archivos de Linux tratado en [[ext4]], ni el mecanismo de consistencia de NTFS, descrito en [[journaling]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): los metadatos asociados a cada archivo y la organización de archivos y carpetas en un sistema de archivos.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): los sistemas de archivos como parte del sistema operativo y la necesidad de estructuras de control de acceso y consistencia.
