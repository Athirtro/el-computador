---
titulo: "Sistema de archivos"
slug: sistema-de-archivos
rama: software
categoria: sistema
nivel: 4
prerequisitos: [sistema-operativo]
conduce_a: [estructuras-de-datos, formatos-de-archivos]
alias: ["sistema de archivos", "filesystem"]
estado: borrador
fuentes: []
---

# Sistema de archivos

## Idea central
El sistema de archivos es la parte del [[sistema-operativo]] que organiza la información guardada de forma persistente y la presenta como archivos y carpetas con nombre. Gracias a él, una aplicación puede guardar, localizar y recuperar datos sin ocuparse de cómo están repartidos en el dispositivo de almacenamiento.

## Antes de empezar
- [[sistema-operativo]]: el programa de sistema que ofrece el entorno integral de trabajo y coordina el uso del hardware.

## Explicación
El sistema de archivos (filesystem) es el componente del [[sistema-operativo]] encargado de la información que permanece cuando el ordenador deja de funcionar. Esa persistencia significa que un documento, una fotografía o un programa guardados hoy pueden volver a encontrarse mañana, sin tener que crearlos de nuevo.

Sin esta organización, guardar información sería solo acumular datos sin nombre ni lugar. Por eso el sistema de archivos introduce dos ideas visibles. Un archivo es una colección de datos con un nombre, que se puede crear, leer, modificar y borrar. Una carpeta —también llamada directorio— es un contenedor con nombre que agrupa archivos y otras carpetas. Al poner carpetas dentro de carpetas se forma una jerarquía: cada elemento cuelga de un lugar concreto y se localiza siguiendo ese camino, llamado ruta.

Esa jerarquía es lo que convierte un conjunto disperso de datos en algo recuperable. Cuando un programa pide abrir un archivo, no busca en todo el almacenamiento: sigue la ruta que indica dónde está dentro de las carpetas. El sistema de archivos mantiene ese mapa de nombres y lugares, y decide dónde colocar cada archivo nuevo para que el resto de programas pueda encontrarlo después.

Conviene distinguir el archivo del contenido que guarda. El sistema de archivos se ocupa del nombre, la carpeta y la organización; no decide cómo están escritos por dentro los bytes de un documento o de una imagen. Esa representación interna pertenece a [[formatos-de-archivos]]. Tampoco se ocupa aquí de cómo se agrupan los datos mientras están en memoria, lo que se trata en [[estructuras-de-datos]].

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sistema-operativo]] se llega al sistema de archivos al pasar de la función general —organizar la información persistente— al mecanismo concreto que crea archivos y carpetas. Una vez visible esa organización, el paso siguiente es preguntarse cómo se representa cada archivo por dentro, en [[formatos-de-archivos]], y cómo se organizan los datos en memoria, en [[estructuras-de-datos]].

## Límites de esta explicación
Esta nota no explica la representación interna de cada archivo, tratada en [[formatos-de-archivos]], ni la organización de datos en memoria, tratada en [[estructuras-de-datos]]. Tampoco entra en los tipos concretos de sistema de archivos ni en los dispositivos físicos de almacenamiento.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
