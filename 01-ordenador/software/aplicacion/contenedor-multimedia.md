---
titulo: "Contenedor multimedia"
slug: contenedor-multimedia
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [codec]
conduce_a: []
alias: ["contenedor multimedia", "multimedia container", "formato contenedor"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Contenedor multimedia

## Idea central
Un contenedor multimedia es el formato de archivo que agrupa en un único archivo las pistas de audio, de vídeo y, cuando existen, las de subtítulos y datos, junto con los índices imprescindibles para localizar cada fragmento. No comprime ni descomprime el contenido: dice qué pistas hay, qué [[codec]] usa cada una y dónde empieza cada fragmento dentro del archivo.

## Antes de empezar
- [[codec]]: qué hace un códec, por qué las pistas llegan comprimidas y por qué el reproductor necesita descomprimir cada fragmento antes de presentarlo. Esta nota presupone esa idea y no repite su funcionamiento.

## Explicación
El [[reproductor-multimedia]] no puede presentar los fragmentos tal como están guardados. Los fragmentos llegan comprimidos con un códec, y el reproductor debe invertir esa transformación en el instante de la reproducción. Sin embargo, saber cómo descomprimir una pista no basta para reproducir un archivo: hace falta saber también cuántas pistas contiene el archivo, qué códec utiliza cada pista y en qué punto del archivo comienza cada fragmento. Esa es la tarea del contenedor.

El contenedor funciona como la envoltura común de todas las pistas. En su interior guarda las pistas completas, cada una comprimida con su códec, y añade información de organización que no pertenece a ninguna pista concreta: una cabecera que identifica el formato, metadatos generales como la duración o el título, y referencias al tipo de códec utilizado. También guarda índices, es decir, tablas que dicen en qué posición del archivo empieza cada pista y en qué posición empieza cada fragmento dentro de la pista. Sin esos índices, el reproductor tendría que recorrer el archivo entero desde el principio para encontrar el fragmento que le toca en cada instante, lo que impediría el avance, el retroceso y el salto a un punto concreto.

La distinción entre códec y contenedor se entiende por lo que cada uno decide. El códec decide cómo está transformado el contenido de una pista y cómo debe reconstruirse. El contenedor decide cómo se ordenan las pistas dentro del archivo y cómo se localiza cada fragmento. Un mismo contenedor puede agrupar una pista de vídeo comprimida con un códec y una pista de audio comprimida con otro, y cambiar el contenedor no cambia la forma en que está comprimida ninguna pista. Por eso el reproductor necesita leer primero el contenedor, para encontrar las pistas y sus índices, y consultar después el códec de cada pista, para poder presentarla.

Esta separación también explica por qué un archivo tiene dos nombres ligados a su tecnología. Uno suele referirse al contenedor y otro al códec que lleva dentro, y suelen confundirse porque en la práctica se distribuyen juntos. Un reproductor compatible con un contenedor concreto no garantiza que pueda reproducir cualquier archivo en ese contenedor si desconoce el códec que cada pista utiliza, y viceversa: conocer un códec solo sirve si el reproductor sabe localizar los fragmentos comprimidos con él dentro del contenedor. Cuando falla alguna de las dos partes, el archivo no se reproduce aunque el resto de la cadena funcione.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[codec]] se desciende a este peldaño porque aquella nota distingue el códec del contenedor en una sola idea —que el contenedor agrupa las pistas y añade índices para localizarlas— y deja esa idea sin desarrollar. Esta nota desarrolla exactamente ese punto: qué agrupa el contenedor y qué índices guarda para que el reproductor encuentre cada fragmento. No conduce a ningún otro slug en este momento, porque los contenedores concretos, la sincronía entre pistas y los servicios del sistema que entregan el archivo pertenecen a notas aún no registradas y no pueden enlazarse todavía.

## Límites de esta explicación
Esta nota no trata el funcionamiento de ningún códec concreto ni de ningún contenedor concreto: queda en [[codec]] la parte de compresión y no se enlaza aquí ningún formato específico por no existir aún como conceptos registrados. Tampoco trata la sincronía entre audio y vídeo ni cómo el reproductor decide el instante de presentación de cada fragmento; queda en [[reproductor-multimedia]]. La representación general de archivos en disco queda en [[formatos-de-archivos]], sin desarrollar sus formatos concretos.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): respalda únicamente la idea general de que la aplicación se apoya en los servicios del sistema operativo en lugar de gestionar directamente el hardware, aplicada aquí a la lectura del archivo y a la entrega de la imagen y el sonido; no contiene el detalle técnico de contenedores multimedia, índices ni códecs concretos.
- FTE-0002 (Modern Operating Systems, Tanenbaum y Bos): respalda la misma distinción entre el programa de aplicación y los servicios del sistema en que aquel se apoya; no contiene el detalle técnico de contenedores multimedia, índices ni códecs concretos.
