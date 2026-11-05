---
titulo: "Formato de documento"
slug: formato-de-documento
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [procesador-de-texto]
conduce_a: []
alias: ["formato de documento", "document format"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Formato de documento

## Idea central
El formato de documento es el acuerdo preciso sobre cómo se guarda un documento en disco para que otra ejecución del mismo programa —o un programa compatible— pueda reconstruirlo tal como se veía en pantalla. Sin ese acuerdo, el documento en memoria se pierde al cerrar el programa, porque el procesador de texto trabaja con una representación temporal y el disco solo conserva bytes.

## Antes de empezar
- [[procesador-de-texto]]: qué es un procesador de texto y que el documento combina texto con instrucciones de presentación.
- [[sistema-de-archivos]]: cómo el sistema operativo guarda bytes en un archivo dentro de un volumen.
- [[formatos-de-archivos]]: qué es, en general, un formato de archivo como representación de datos en disco.

## Explicación
Desde [[procesador-de-texto]] se sabe que el documento en memoria no es solo caracteres: cada fragmento lleva propiedades de presentación, estilos, márgenes, encabezados y organización en páginas. Mientras el programa trabaja, esa información vive en memoria principal y desaparece cuando el programa termina. Para que el trabajo persista, el programa debe traducirla a una secuencia de bytes que el [[sistema-de-archivos]] pueda escribir en un archivo.

Esa traducción es el formato de documento. Un formato define un orden fijo de lectura: qué parte del archivo indica el tipo de contenido, dónde se guardan los párrafos y sus marcas de formato, dónde van los estilos reutilizables, cómo se incrustan o se enlazan imágenes y tablas, y qué información adicional se conserva, como el autor o la fecha de última modificación. Al abrir el archivo, el programa lee los bytes en ese orden y reconstruye en memoria la misma combinación de texto y presentación con la que fue guardado.

Cada formato concreta ese acuerdo de un modo propio y no tiene por qué coincidir con el de otro programa. Por eso un procesador puede guardar en su propio formato y también exportar a formatos de intercambio, y por eso al abrir un documento de otro origen puede perder elementos que el formato destino no sabe representar. La elección de formato decide qué se conserva intacto al guardar, qué se transforma y qué se pierde. El programa no gestiona directamente el disco: entrega los bytes al sistema operativo y este los deposita en el [[sistema-de-archivos]], según los [[formatos-de-archivos]] que el programa declara soportar.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[procesador-de-texto]], que presenta el documento como texto más formato en pantalla, se desciende un peldaño hasta la persistencia: el formato de documento es la regla que permite convertir esa presentación en memoria en bytes recuperables en disco y volver a reconstruirla al abrir el archivo. No abre un nuevo peldaño lineal en el libro.

## Límites de esta explicación
Esta nota no desarrolla la estructura interna de ningún formato concreto ni compara formatos entre sí, porque eso pertenece al estudio de cada programa o estándar concreto; aquí solo se trata la función general del formato como registro del documento. Tampoco trata los formatos de archivo en general —imágenes, sonido, ejecutables—, que corresponden a [[formatos-de-archivos]], ni el almacenamiento físico dirigido por el sistema, que corresponde al [[sistema-de-archivos]].

## Referencias
- FTE-0001: respaldo general de la afirmación de que la aplicación delega en el sistema operativo la persistencia de sus datos en archivos.
- FTE-0002: respaldo general de la misma afirmación sobre la dependencia de la aplicación respecto a los servicios del sistema para guardar y recuperar archivos.
