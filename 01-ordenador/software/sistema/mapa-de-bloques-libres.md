---
titulo: "Mapa de bloques libres"
slug: mapa-de-bloques-libres
rama: software
categoria: sistema
nivel: 6
prerequisitos: [inodo]
conduce_a: []
alias: ["mapa de bloques libres", "free block bitmap", "free space map"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Mapa de bloques libres

## Idea central
El mapa de bloques libres es la tabla que el [[sistema-de-archivos]] mantiene para saber qué bloques del disco están ocupados y cuáles pueden asignarse a un archivo nuevo. Junto al [[inodo]], que describe los bloques de cada archivo, permite repartir el espacio sin recorrer todos los archivos ni dejar que dos archivos reclamen el mismo bloque.

## Antes de empezar
- [[inodo]]: la entrada que describe un archivo o carpeta y enumera los bloques de datos que ocupa.
- [[sistema-de-archivos]]: la parte del sistema operativo que organiza la información persistente en un volumen.
- [[tipos-de-sistema-de-archivos]]: cada tipo concreto, como ext4, NTFS o FAT32, implementa este registro con sus propias estructuras internas.

## Explicación
El disco se organiza en bloques, es decir, en unidades fijas de tamaño fijo en las que se guarda la información. El mapa de bloques libres es una tabla que contiene una entrada por cada bloque del volumen: cada posición corresponde a un bloque concreto y su valor indica si ese bloque está libre u ocupado. En su forma más habitual se implementa como un mapa de bits (bitmap), una fila de bits en la que cada bit representa un bloque y su valor distingue entre libre y ocupado; según el tipo de sistema de archivos, la convención puede invertir el significado del valor, pero el principio es el mismo.

Cuando el sistema operativo necesita guardar datos, no puede preguntarse simplemente qué bloques le interesan: debe encontrar bloques que nadie está usando. El mapa permite hacerlo sin recorrer todas las entradas de archivos. El sistema consulta la tabla, localiza una posición libre, marca esa posición como ocupada y solo después anota la asignación en el [[inodo]] correspondiente, de modo que el archivo pasa a registrar el bloque como suyo. Al borrar un archivo ocurre lo inverso: el sistema libera los bloques que su [[inodo]] enumeraba y marca esas posiciones como libres en el mapa, para que puedan volver a asignarse.

Frente a esta tabla global, el [[inodo]] ocupa un lugar complementario y deliberadamente distinto. El [[inodo]] responde a la pregunta de qué bloques pertenecen a un archivo concreto; el mapa responde a la pregunta de qué queda libre en todo el volumen. Recalcular el espacio libre recorriendo todas las entradas sería posible, pero costoso y frágil: obligaría a visitar cada archivo para deducir qué bloques no aparecen en ninguno. El mapa centraliza esa información en un solo registro, actualizado en cada asignación y en cada liberación.

Existen dos formas habituales de almacenar este registro. La primera es el mapa de bits, en el que cada bloque consume un solo bit, con lo que la tabla ocupa poco espacio incluso en volúmenes grandes, aunque localizar un bloque libre puede requerir revisar muchos bits. La segunda es una lista de bloques libres, en la que solo se anotan los bloques disponibles y se encadenan entre sí; cuando se asigna un bloque, se retira de la lista, y cuando se libera, se inserta en ella. Ambas formas resuelven el mismo problema con compromisos distintos entre espacio ocupado por la tabla y rapidez para buscar un hueco, y la elección concreta depende de cada tipo de sistema de archivos.

Este registro es también una de las estructuras que la [[comprobacion-de-consistencia]] compara con el resto de metadatos: si las entradas de los archivos ocupan bloques que el mapa señala como libres, o si el mapa marca como ocupados bloques que ningún archivo reclama, la organización queda incoherente. Por eso el mapa debe mantenerse actualizado en cada operación de escritura y borrado, y por eso su reconstrucción forma parte de la recuperación del volumen tras un corte.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[inodo]] se pasa a esta nota al preguntarse cómo sabe el sistema qué bloques puede entregar a un archivo nuevo sin que entren en conflicto con los ya asignados. El [[inodo]] lista los bloques de un archivo; el mapa de bloques libres es el índice global del volumen que dice qué posiciones siguen disponibles. Es una rama terminal de la cadena: explica el registro que complementa al [[inodo]] para la asignación de espacio, sin abrir un nuevo peldaño hacia el detalle interno de cada tipo de sistema de archivos ni hacia los procedimientos de reparación, que se tratan en otras notas.

## Límites de esta explicación
Esta nota no desarrolla el detalle del [[inodo]], sus campos ni cómo enumera los bloques de un archivo, que se trata en [[inodo]]. Tampoco describe cómo cada tipo concreto, como ext4, NTFS o FAT32, sitúa y nombra el mapa dentro del volumen, que se trata en [[tipos-de-sistema-de-archivos]]. El uso de este mapa en la reparación tras un corte se trata en [[comprobacion-de-consistencia]] y [[journaling]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): gestión del espacio libre en sistemas de archivos.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum y Bos): gestión del espacio libre en sistemas de archivos.
