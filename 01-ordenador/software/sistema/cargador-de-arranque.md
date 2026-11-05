---
titulo: "Cargador de arranque"
slug: cargador-de-arranque
rama: software
categoria: sistema
nivel: 5
prerequisitos: [bios-uefi]
conduce_a: [sistema-operativo]
alias: ["cargador de arranque", "boot loader", "gestor de arranque"]
estado: borrador
fuentes: [FTE-0003]
---

# Cargador de arranque

## Idea central
El cargador de arranque es el pequeño programa que [[bios-uefi]] localiza en el disco y al que cede el control para que ponga en marcha el [[sistema-operativo]]. Vive en el intervalo entre prepararlo todo, que es tarea de BIOS/UEFI, y gestionarlo todo, que es tarea del sistema operativo. Sin él, el equipo sabría qué hardware tiene pero no sabría cómo empezar a cargar el programa que debe administrarlo.

## Antes de empezar
- [[bios-uefi]]: el firmware de la placa base que reconoce el hardware al encender el equipo y busca el programa que cargará el sistema operativo.
- [[sistema-operativo]]: el programa que el cargador debe preparar, es decir, poner en condiciones de ejecutarse y empezar a administrar el ordenador.

## Explicación
El cargador de arranque (boot loader, primera aparición del término en inglés en el libro) es un programa pequeño y específico: su única misión es preparar el sistema operativo para su ejecución. Cuando BIOS/UEFI lo localiza en el dispositivo de arranque configurado y le cede el control, deja de ser BIOS/UEFI quien manda y pasa a ser el cargador durante un tiempo breve y transitorio. El cargador lee del disco el código del sistema operativo y lo coloca en la [[memoria-ram]] en el lugar donde puede empezar a ejecutarse, es decir, donde el procesador puede encontrarse con sus primeras instrucciones. Hecho eso, le pasa el control al sistema operativo y desaparece como autoridad: a partir de ese momento el que gobierna el equipo ya no es ni BIOS/UEFI ni el cargador, sino el sistema operativo a través de su [[nucleo-kernel]].

El cargador de arranque no sustituye al sistema operativo ni administra el ordenador mientras funciona. No gestiona procesos, no organiza archivos y no atiende programas de usuario: su trabajo es mínimo y está acotado. Esa pequeñez es necesaria porque debe funcionar en un momento en que todavía no hay un sistema operativo disponible para hacer el trabajo por él — en particular, no puede apoyarse en la organización de archivos que el propio sistema operativo necesitará, llamada [[sistema-de-archivos]], así que localiza su objetivo siguiendo el esquema de arranque que BIOS/UEFI le ha comunicado. En la práctica, cuando en un equipo hay más de un sistema operativo o varias configuraciones posibles, este papel se llama gestor de arranque (boot manager, primera aparición del término en inglés en el libro): es el programa que ofrece elegir cuál de ellos cargar antes de ceder el control a su cargador o directamente a su sistema operativo. Ejemplo citado sin desarrollar aquí: un cargador típico de sistemas operativos libres es GNU GRUB, cuya función esencial es esta misma, localizar y entregar el control al sistema elegido.

La cadena completa es, por tanto, encendido, reconocimiento del hardware por BIOS/UEFI, localización del cargador, carga del sistema operativo en memoria y cesión del control al sistema. Cada eslabón es un programa distinto, con una tarea distinta, y cada uno cede el control al siguiente y deja de gobernar.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[bios-uefi]], que prepara el hardware, ya ha localizado el siguiente programa y le cede el control, se pasa al cargador de arranque, el pequeño programa que prepara el [[sistema-operativo]] para su ejecución colocándolo en la [[memoria-ram]] ejecutable. Y desde el cargador se pasa al sistema operativo, que asume a partir de ese momento la gestión general del ordenador. El orden queda así: primero BIOS/UEFI reconoce y entrega, después el cargador prepara, y solo entonces el sistema operativo gobierna. Sin salto: no se salta de la preparación del hardware a la administración del ordenador sin explicar el programa que hace de puente.

## Límites de esta explicación
Esta nota no desarrolla el detalle interno de BIOS/UEFI ni de UEFI —sus protocolos, servicios y módulos—, que se trata en [[bios-uefi]], ni el funcionamiento interno del [[nucleo-kernel]] una vez que el sistema operativo ya está en marcha, que se trata en [[nucleo-kernel]], ni la organización de archivos en disco, que se trata en [[sistema-de-archivos]]. Tampoco trata la familia de cargadores de programas (los que al ejecutar una aplicación la cargan en memoria), que responde a una pregunta distinta y se tratará en su propia nota. Aquí solo se explica el papel del cargador de arranque como eslabón entre la preparación del hardware y la gestión del ordenador.

## Referencias
- FTE-0003 (UEFI Specification, UEFI Forum): contrato de entrega entre BIOS/UEFI y el cargador de arranque.
