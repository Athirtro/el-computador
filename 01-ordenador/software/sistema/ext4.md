---
titulo: "Ext4"
slug: ext4
rama: software
categoria: sistema
nivel: 6
prerequisitos: [tipos-de-sistema-de-archivos]
conduce_a: [inodo]
alias: ["sistema de archivos ext4", "fourth extended filesystem"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Ext4

## Idea central
Ext4 es el sistema de archivos habitual de Linux: la cuarta versión de la familia ext, pensada para discos grandes y para proteger la organización de los archivos ante un corte de corriente. No cambia la idea de [[sistema-de-archivos]] —archivos, carpetas y rutas—, solo el modo concreto de implementarla en Linux.

## Antes de empezar
- [[tipos-de-sistema-de-archivos]]: cada tipo es un conjunto concreto de reglas para guardar, localizar y proteger los datos, y ext4 es uno de ellos frente a NTFS y FAT32.

## Explicación
Ext4 pertenece a la familia ext, creada específicamente para Linux, y es el formato que las distribuciones de ese sistema suelen elegir al preparar el disco principal. Como su núcleo sabe montarlo de forma nativa, no necesita capas de compatibilidad pensadas para otros sistemas; su diseño parte de lo que el kernel Linux necesita para acceder con rapidez y con permisos por usuario.

Su primer rasgo práctico es el tamaño. Frente al límite de unos pocos GB por archivo de FAT32, descrito en [[tipos-de-sistema-de-archivos]], ext4 admite volúmenes y archivos individuales de varios terabytes. Eso lo hace adecuado para discos de sistema con grandes colecciones de archivos, sin la restricción que obligaría a dividir un archivo en piezas externas. Para conseguirlo ordena mejor el espacio libre y agrupa los bloques de un archivo de forma más contigua, de modo que los archivos grandes no queden repartidos en fragmentos dispersos por todo el disco.

Su segundo rasgo es la protección ante fallos. Ext4 aplica [[journaling]]: antes de modificar la organización en el disco, registra en un área separada qué cambios va a hacer. Si el corte de corriente llega a mitad de una escritura, al rearrancar el sistema puede consultar ese registro y completar o deshacer las operaciones pendientes, en lugar de encontrar archivos a medio crear o carpetas incoherentes. El diario no sustituye a la [[copia-de-seguridad]] —no recupera archivos borrados ni datos ya sobrescritos—, solo ayuda a que la estructura del sistema de archivos siga siendo consistente.

Su tercer rasgo es el control por usuario, compartido con NTFS pero expresado en términos de Linux. Cada archivo conserva propietario, permisos de lectura y escritura, fechas y tamaño, información que el núcleo consulta al decidir si un programa puede abrirlo. Esa información de control vive asociada a cada archivo en una ficha de metadatos, el [[inodo]], cuyo detalle es el peldaño siguiente, y es la base sobre la que funcionan los permisos y la recuperación del diario.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[tipos-de-sistema-de-archivos]] se pasa a esta nota al bajar del panorama de los tres tipos al caso concreto de Linux: ya se sabe que FAT32 prioriza compatibilidad y NTFS un escritorio Windows, y ahora se ve cómo ext4 prioriza tamaño y recuperación de consistencia en Linux. El paso siguiente es [[inodo]], que explica la ficha de metadatos que ext4 mantiene por archivo y sobre la que se apoyan tanto los permisos como el [[journaling]].

## Límites de esta explicación
Esta nota no desarrolla la estructura interna de ext4 —cómo reparte bloques, tablas o grupos en el disco— ni los modos concretos de [[journaling]], que se tratan en [[journaling]]. Tampoco detalla NTFS ni FAT32, cubiertos en general en [[tipos-de-sistema-de-archivos]], ni otros sistemas de archivos de Linux, ni la comprobación y reparación de un volumen dañado.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): sistemas de archivos como organización del almacenamiento persistente y necesidad de consistencia.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): tipos de sistema de archivos y organización de archivos y metadatos en sistemas tipo Unix.
