---
titulo: "FAT32"
slug: fat32
rama: software
categoria: sistema
nivel: 6
prerequisitos: [tipos-de-sistema-de-archivos]
conduce_a: []
alias: ["File Allocation Table 32"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# FAT32

## Idea central
FAT32 es un tipo de sistema de archivos de la familia FAT, diseñado para ser sencillo y legible por casi cualquier sistema operativo. Su valor no está en sus funciones avanzadas, que son escasas, sino en su compatibilidad: es el formato que se elige cuando un dispositivo de almacenamiento tiene que funcionar en ordenadores y aparatos muy distintos entre sí.

## Antes de empezar
- [[tipos-de-sistema-de-archivos]]: cada tipo de sistema de archivos es un conjunto concreto de reglas para guardar, localizar y proteger los datos.

## Explicación
La familia FAT —siglas de tabla de asignación de archivos (File Allocation Table)— organiza el almacenamiento manteniendo una tabla que indica qué espacio está ocupado y a qué archivo pertenece. FAT32 es la versión de 32 bits de esa familia: el número alude al tamaño de cada entrada de su tabla, que permite direccionar muchos más bloques que las versiones anteriores y, por tanto, trabajar con discos de mayor capacidad.

Esa sencillez explica su principal ventaja. Al ser un diseño antiguo, estable y ampliamente documentado, FAT32 es reconocido de forma nativa por los sistemas operativos de escritorio, por los sistemas de cámaras, reproductores y videoconsolas, y por las memorias extraíbles. Un disco en FAT32 se puede llevar de un equipo a otro sin instalar controladores ni software adicional, y los aparatos sin ordenador lo leen sin dificultad. En la práctica, se reserva para medios extraíbles compartidos y para dispositivos que exigen compatibilidad máxima.

El mismo diseño simple impone sus límites. El límite más conocido es el tamaño máximo de un archivo individual: FAT32 no admite archivos de más de unos 4 GB, de modo que una imagen de disco, un vídeo largo o una copia de seguridad grande no pueden guardarse como un solo archivo en un volumen FAT32, aunque el disco tenga espacio libre de sobra. Además, FAT32 no guarda por archivo la información de control que otros tipos sí gestionan —propietario, permisos de lectura y escritura por usuario y registro de cambios—, por lo que no ofrece el control de acceso descrito en [[permisos-de-archivos]] ni la protección ante cortes que en otros tipos aporta [[journaling]]. Esas carencias no son un defecto accidental: son el precio de un formato mínimo que cualquier sistema puede implementar.

Por eso FAT32 no se usa hoy como disco principal de un sistema operativo moderno, donde se necesitan archivos grandes y protección por usuario, y sí como formato de intercambio en memorias USB y tarjetas. La regla práctica es sencilla: si el requisito dominante es que el medio funcione en cualquier parte, FAT32 es la elección; si el requisito es capacidad o control de acceso, conviene otro tipo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[tipos-de-sistema-de-archivos]] se baja en esta nota del panorama de tipos al caso concreto de FAT32: se concretan la compatibilidad, el límite de tamaño de archivo y la ausencia de permisos y de registro de cambios que allí se anunciaron. FAT32 es una nota de cierre de la cadena, sin `conduce_a` propio: completa el trío ext4, NTFS y FAT32, y deja las funciones que le faltan remitidas a las notas que sí las tratan.

## Límites de esta explicación
Esta nota no desarrolla la estructura interna en disco de FAT32 —sectores, entradas de directorio o cadenas de bloques—, ni las especificaciones exactas de capacidad de volumen, que quedan fuera del nivel de este peldaño. Tampoco trata los tipos ext4 ni NTFS, que tienen sus propias notas previstas en el mapa, ni otros miembros de la familia FAT. El mecanismo de protección ante cortes se trata en [[journaling]] y el control de acceso en [[permisos-de-archivos]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): los tipos de sistema de archivos como reglas concretas de organización del almacenamiento.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): los tipos de sistema de archivos como reglas concretas de organización del almacenamiento.
