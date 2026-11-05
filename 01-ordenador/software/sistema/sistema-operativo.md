---
titulo: "Sistema operativo"
slug: sistema-operativo
rama: software
categoria: sistema
nivel: 3
prerequisitos: [software-de-sistema]
conduce_a: [nucleo-kernel, sistema-de-archivos, controladores-drivers]
alias: ["sistema operativo", "OS"]
estado: borrador
fuentes: []
---

# Sistema operativo

## Idea central
El sistema operativo es el programa de sistema que ofrece un entorno integral de trabajo sobre el ordenador: coordina el uso del hardware y presenta a los demás programas y a la persona usuaria unos servicios ordenados. Sin él, cada programa tendría que controlar directamente los componentes físicos.

## Antes de empezar
- [[software-de-sistema]]: el conjunto de programas que gestionan el hardware y preparan el entorno en el que funciona el resto del software.

## Explicación
El sistema operativo (OS) es el componente de [[software-de-sistema]] que convierte un conjunto de recursos físicos —procesador, memoria y dispositivos— en un entorno utilizable. Una aplicación no necesita saber cómo se mueve un disco ni cómo se reparte la memoria: pide un servicio al sistema operativo y este decide cómo atenderlo. Esa intermediación es su función esencial.

En su centro se encuentra el [[nucleo-kernel]] (kernel), el componente siempre activo que controla directamente los recursos. Un ejemplo familiar es Linux: lo visible —ventanas, archivos, aplicaciones— descansa sobre un núcleo que coordina el hardware, rodeado por el resto del entorno que lo hace usable. Esta nota solo lo señala como centro del sistema operativo; cómo asigna procesador y memoria o cómo atiende cada petición se trata en [[nucleo-kernel]].

El entorno integral que ofrece comprende varias funciones. Presenta una forma de interactuar con el ordenador, ya sea mediante ventanas y menús o mediante texto escrito. Carga y supervisa los programas que la persona usuaria ejecuta, entendidos como instrucciones en ejecución. Organiza la información que se guarda de forma persistente, a través de [[sistema-de-archivos]], es decir, archivos y carpetas que permiten guardarla, localizarla y recuperarla. Y permite usar cada dispositivo concreto gracias a los [[controladores-drivers]], los programas que enseñan al sistema operativo a manejar impresoras, tarjetas de sonido, adaptadores de red y demás periféricos.

El sistema operativo no realiza la tarea concreta de la aplicación —redactar un texto, reproducir un vídeo o navegar—: hace posible que el ordenador funcione de forma coordinada para que esa tarea pueda realizarse. Tampoco sustituye al [[firmware]] ni a [[bios-uefi]], que preparan el hardware antes del arranque y lo localizan para cargar el sistema operativo; una vez cargado, es el sistema operativo quien toma el control general.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-sistema]] se llega al sistema operativo al pasar del panorama —qué programas gestionan el hardware— al programa concreto que ofrece el entorno integral. Desde aquí, el paso natural es el [[nucleo-kernel]], que detalla el componente central, y después la gestión de recursos. En paralelo, el sistema operativo prepara dos ramas: [[sistema-de-archivos]], para organizar la información, y [[controladores-drivers]], para tratar con cada dispositivo.

## Límites de esta explicación
Esta nota no explica cómo el [[nucleo-kernel]] asigna procesador, memoria y dispositivos, ni cómo funciona la gestión de recursos por dentro; eso se trata en [[nucleo-kernel]] y [[gestion-de-recursos]]. Tampoco detalla el sistema de archivos, los controladores ni el arranque previo al sistema operativo, tratados en [[sistema-de-archivos]], [[controladores-drivers]] y [[bios-uefi]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
