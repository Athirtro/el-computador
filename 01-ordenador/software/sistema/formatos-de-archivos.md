---
titulo: "Formatos de archivos"
slug: formatos-de-archivos
rama: software
categoria: sistema
nivel: 5
prerequisitos: [estructuras-de-datos, sistema-de-archivos]
conduce_a: []
alias: ["formatos de archivo"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Formatos de archivos

## Idea central
Un formato de archivo es el conjunto de reglas que fija cómo se representan los datos dentro de un archivo para que puedan guardarse de forma persistente y leerse después de manera fiable. El [[sistema-de-archivos]] decide dónde está el archivo y cómo se llama; el formato decide cómo están escritos sus bytes por dentro.

## Antes de empezar
- [[estructuras-de-datos]]: la organización de los datos mientras están en memoria.
- [[sistema-de-archivos]]: la organización persistente de archivos y carpetas, con su nombre y su ruta.

## Explicación
Cuando un programa guarda información en un archivo, no basta con volcar los datos tal como los tiene en memoria. Esos datos deben sobrevivir al apagado del ordenador, poder recuperarse después y ser interpretados de la misma forma por quien los lea. Un formato de archivo es el acuerdo que hace posible esa recuperación: define qué significa cada parte de la secuencia de bytes que forma el archivo.

Todo archivo es, en su nivel más bajo, una secuencia de bytes. Por sí sola, esa secuencia no indica qué representa ni cómo se divide. El formato aporta esa información mediante una estructura interna compartida. Suele partirla en una cabecera, es decir, en los bytes iniciales que indican el tipo de archivo y dónde empieza cada parte, y un cuerpo, donde se guardan los datos propiamente dichos. Cuando el formato lo necesita, añade metadatos: datos que describen a los datos del cuerpo, como su tamaño, su número de elementos o la versión del formato utilizada.

La diferencia con las [[estructuras-de-datos]] es de persistencia y estabilidad. Una estructura de datos está pensada para que un programa acceda, inserte o recorra la información con eficiencia mientras trabaja en memoria; puede depender del programa que la usa y cambiar sin dejar rastro. Un formato, en cambio, debe ser estable: si un archivo se guarda hoy, debe poder leerse mañana, incluso con una versión distinta del programa que lo escribió. Por eso un formato fija también el orden en que se escriben los valores numéricos y la manera de representar cada tipo de dato en disco, en lugar de limitarse a copiar el estado de la memoria.

Existen formatos de texto, en los que los datos se representan como caracteres legibles, y formatos binarios, en los que se representan directamente como bytes. Ambos responden al mismo principio: sin un acuerdo previo sobre la representación, el programa que lee no puede saber qué significan los bytes que encuentra. La extensión del nombre, como `.txt` o `.bin`, es solo una pista convencional; la identificación fiable reside en el contenido definido por el formato, en particular en su cabecera.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[estructuras-de-datos]] y [[sistema-de-archivos]] se llega a los formatos de archivos al pasar de la organización de los datos en memoria y de la organización de los archivos en carpetas a la representación de cada archivo por dentro. Esta nota cierra esa cadena: memoria, nombre y pasaje a disco quedan conectados sin que ninguno de ellos decida el contenido del archivo.

## Límites de esta explicación
Esta nota no detalla ningún formato concreto; cada formato específico necesitaría su propia nota si el libro decide tratarlo. Tampoco trata de nuevo la organización de los datos en memoria, cubierta en [[estructuras-de-datos]], ni la organización de archivos y carpetas, cubierta en [[sistema-de-archivos]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
