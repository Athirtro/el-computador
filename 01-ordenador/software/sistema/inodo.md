---
titulo: "Inodo"
slug: inodo
rama: software
categoria: sistema
nivel: 6
prerequisitos: [sistema-de-archivos]
conduce_a: [mapa-de-bloques-libres]
alias: ["inode"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Inodo

## Idea central
El inodo (inode) es la ficha individual de metadatos que el sistema de archivos guarda por cada archivo. Guarda dónde están sus datos y cómo puede usarse, para que el sistema sepa abrirlo sin buscarlo en todo el almacenamiento.

## Antes de empezar
- [[sistema-de-archivos]]: la organización persistente de archivos y carpetas con nombre.

## Explicación
El sistema de archivos separa el nombre de la identidad de un archivo. La carpeta conserva solo una entrada con el nombre y un número que lo identifica; esa serie de entradas es la jerarquía de carpetas ya vista. Todo lo demás sobre el archivo vive en una sola entrada numerada, el inodo (inode), de la que hay una por archivo. El conjunto de todas esas entradas se guarda como una tabla de inodos en el dispositivo de almacenamiento.

Un inodo guarda los datos de control del archivo: su tamaño en bytes, los punteros a los bloques donde están escritos su contenido, el número de nombres que lo referencian, el propietario y los permisos de lectura, escritura y ejecución, y las fechas de último acceso y última modificación. No guarda el contenido en sí; solo indica dónde encontrarlo.

Esa separación explica por qué un mismo archivo puede tener dos nombres distintos, los enlaces duros: dos entradas de directorio apuntan al mismo número de inodo y el contador de enlaces del inodo pasa a dos. Borrar un nombre solo decrementa ese contador; el archivo solo desaparece cuando llega a cero y no queda ningún nombre que lo referencie. Renombrar o mover un archivo también es barato, porque solo cambia la entrada de directorio y no los punteros del inodo ni sus bloques de datos.

La idea es la misma que el [[bloque-de-control-de-proceso]] para los procesos: una ficha única por entidad con su estado y sus referencias, consultada cada vez que hay que actuar sobre ella. En este caso, consultar el inodo es el paso obligado para abrir, leer, escribir o borrar un archivo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sistema-de-archivos]] se llega al inodo al bajar de la organización visible —nombres y carpetas— a la ficha que hace operativa esa organización. Una vez vistas las fichas por archivo, el paso siguiente es preguntarse cómo se reparten los bloques a los que apuntan y cómo se sabe cuáles están libres, en [[mapa-de-bloques-libres]].

## Límites de esta explicación
Esta nota no explica cómo se registra qué bloques están libres ni cómo se asignan, tratado en [[mapa-de-bloques-libres]], ni el detalle de permisos, en [[permisos-de-archivos]], ni las diferencias de implementación entre sistemas concretos, en [[tipos-de-sistema-de-archivos]]. El término inodo es literal en sistemas Unix; otros sistemas emplean entradas equivalentes con otro nombre.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): estructura de inodo, tabla de inodos y enlaces.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): entrada de metadatos por archivo y punteros a bloques de datos.
