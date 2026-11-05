---
titulo: "Software de sistema"
slug: software-de-sistema
rama: software
categoria: sistema
nivel: 2
prerequisitos: [software]
conduce_a: [sistema-operativo, firmware, bios-uefi, sistema-de-archivos, controladores-drivers]
alias: ["software de sistema"]
estado: borrador
fuentes: []
---

# Software de sistema

## Idea central
El software de sistema es el conjunto de programas que gestionan el hardware y crean el entorno en el que el resto del software funciona. Sin él, cada programa tendría que controlar directamente los componentes físicos, y el ordenador no podría ofrecer servicios como memoria compartida, archivos o dispositivos de entrada y salida.

## Antes de empezar
- [[software]]: qué es el software como componente intangible del ordenador y cómo se divide en cuatro grupos según su función.
- [[hardware]]: los componentes físicos que el software de sistema coordina; esta nota no explica su construcción, solo su relación con el software que los gobierna.

## Explicación
El [[software]] en general indica al [[hardware]] qué hacer. El software de sistema lo hace de forma indirecta y ordenada: ofrece al demás software unas reglas, unos servicios y un orden de arranque, de modo que cada programa no necesita saber cómo se mueve un disco, cómo se reparte la memoria o cómo se enciende una pantalla. Su función es gestionar el hardware mismo y preparar el terreno sobre el que trabajarán las aplicaciones, los lenguajes y cualquier otro programa.

Conviene distinguirlo del software de aplicación, que realiza tareas concretas para la persona usuaria, como redactar un texto o reproducir un vídeo. El software de sistema no resuelve esas tareas; hace posible que el ordenador funcione de forma coordinada para que puedan resolverse. Un procesador puede ejecutar instrucciones y una memoria puede guardar datos, pero es el software de sistema quien decide qué programa usa cada recurso y en qué momento.

En conjunto, se reconoce por cuatro subgrupos. El primero es el [[sistema-operativo]], el programa de sistema más amplio: presenta al usuario y a los programas un entorno de trabajo y coordina el uso del ordenador. En su centro se encuentra el [[nucleo-kernel]], el componente que controla directamente los recursos, aunque el detalle de cómo lo hace se trata en su nota canónica. Como parte de ese entorno, el sistema operativo también organiza la información en [[sistema-de-archivos]] y [[formatos-de-archivos]], es decir, en carpetas y archivos que permiten guardar, localizar y recuperar datos de forma ordenada.

El segundo subgrupo es el [[firmware]], el software que queda grabado en el propio dispositivo y que lo prepara para funcionar antes de que intervenga el sistema operativo. Un caso concreto es [[bios-uefi]] (BIOS/UEFI), el firmware que enciende el ordenador, reconoce los componentes esenciales y localiza el sistema operativo para cargarlo. Aquí solo importa su lugar en el orden de arranque: primero el firmware prepara el hardware; después, el sistema operativo toma el control general.

El tercer subgrupo son los [[controladores-drivers]], los programas que enseñan al sistema operativo a manejar cada dispositivo concreto, como una impresora, una tarjeta de sonido o un adaptador de red. Sin controladores, el sistema operativo solo podría tratar con el hardware de forma genérica; con ellos, cada dispositivo responde según sus propias instrucciones.

El cuarto subgrupo lo forman las herramientas de sistema, programas auxiliares para diagnosticar, configurar, proteger o mantener el ordenador, como utilidades de copia de seguridad, de comprobación de discos o de ajuste de parámetros. No gestionan por sí mismas el hardware como lo hace el núcleo, pero ayudan a mantener el sistema en funcionamiento y a corregir problemas.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software]] se llega al software de sistema al preguntar quién gobierna el hardware para que los demás programas puedan usarse. El paso siguiente es [[sistema-operativo]], que desarrolla el entorno integral; de él se descienden el [[nucleo-kernel]], la gestión de recursos y el [[sistema-de-archivos]]. En paralelo, el [[firmware]] y [[bios-uefi]] explican el arranque previo al sistema operativo, y los [[controladores-drivers]] explican la comunicación con cada dispositivo concreto.

## Límites de esta explicación
Esta nota ofrece solo el panorama. No explica cómo el [[nucleo-kernel]] asigna procesador y memoria, ni cómo funciona el [[sistema-de-archivos]] por dentro, ni el detalle del [[firmware]], de [[bios-uefi]] o de los [[controladores-drivers]]. Cada uno de esos temas tiene su nota canónica: [[sistema-operativo]], [[nucleo-kernel]], [[firmware]], [[bios-uefi]], [[sistema-de-archivos]] y [[controladores-drivers]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
