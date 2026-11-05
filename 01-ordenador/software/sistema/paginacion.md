---
titulo: "Paginación"
slug: paginacion
rama: software
categoria: sistema
nivel: 8
prerequisitos: [memoria-virtual]
conduce_a: []
alias: ["paginación", "paging"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Paginación

## Idea central
La paginación es el mecanismo que hace posible la [[memoria-virtual]]: divide el espacio virtual de cada programa en bloques de tamaño fijo y traduce cada dirección virtual a la dirección física que contiene ese bloque en cada momento. Sin ella, la memoria virtual quedaría como una idea sin un modo concreto de repartir y localizar sus partes.

## Antes de empezar
- [[memoria-virtual]]: la abstracción que ofrece a cada programa un espacio amplio, ordenado y privado, y que exige traducir cada dirección virtual a una dirección física real o a un contenido que espera en almacenamiento.

## Explicación
La paginación parte de una división sencilla. El espacio virtual se corta en porciones contiguas del mismo tamaño, llamadas páginas (*page*). La memoria física se corta en porciones del mismo tamaño, llamadas marcos de página (*page frame*). El tamaño de página y de marco es idéntico y lo fija la arquitectura del ordenador, no cada programa. Esa igualdad de tamaño es la base de todo lo demás: cualquier página puede ocupar cualquier marco, sin necesidad de que encaje a medida.

Una dirección virtual ya no se lee como un número plano, sino como dos partes. La primera parte es el número de página virtual: dice qué página del espacio del programa se está usando. La segunda es el desplazamiento dentro de la página: dice qué posición ocupa el dato dentro de esa página. Como la página y el marco tienen el mismo tamaño, el desplazamiento se conserva tal cual al traducir. Solo cambia la primera parte: el número de página virtual se sustituye por el número del marco físico donde reside esa página en ese momento.

La correspondencia entre páginas virtuales y marcos físicos no está escrita en las propias direcciones. La guarda el sistema en una tabla de páginas, es decir, un registro que indica, para cada página virtual de un programa, en qué marco físico está cargada, si está cargada o si su contenido espera fuera de la memoria física, y qué permisos tiene. Cada programa tiene su propia tabla, de modo que dos programas pueden usar la misma página virtual y acabar en marcos físicos distintos sin pisarse, que es exactamente lo que la memoria virtual prometía.

Al usar una dirección, el programa entrega los dos números, y la traducción los convierte en una dirección física formada por el número de marco y el mismo desplazamiento. Si la traducción descubre que la página pedida no está cargada en ningún marco, el sistema no puede completar el acceso: debe traer su contenido a un marco libre antes de continuar. Esa posibilidad de tener cargadas solo algunas páginas en un momento dado es lo que permite que un espacio virtual sea mayor que la memoria física.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[memoria-virtual]] se pasa de la promesa —un espacio privado y amplio que el sistema traduce a memoria real— al mecanismo que la cumple: páginas de tamaño fijo, una tabla por programa que dice dónde está cada una, y una traducción que conserva el desplazamiento y solo cambia el número de página por el número de marco. Esta nota cierra el peldaño de la paginación; a partir de aquí, el resto de mecanismos de gestión de memoria se apoyan en ella.

## Límites de esta explicación
Esta nota no explica el modelo alternativo de dividir el espacio en segmentos de tamaño variable; eso se trata en [[segmentacion]]. No explica el detalle de cómo se organiza el espacio de un programa concreto, materia de [[espacio-de-usuario]]. Tampoco explica cómo se estructura internamente la tabla de páginas en varios niveles, cómo se acelera la traducción con cachés dedicadas, ni qué ocurre paso a paso cuando se pide una página no cargada; son peldaños posteriores si el orquestador los crea.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
