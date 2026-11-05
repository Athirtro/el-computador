---
titulo: "Firmware"
slug: firmware
rama: software
categoria: sistema
nivel: 3
prerequisitos: [software-de-sistema]
conduce_a: [bios-uefi]
alias: ["firmware"]
estado: borrador
fuentes: [FTE-0003]
---

# Firmware

## Idea central
El firmware es software que queda grabado en el propio dispositivo y lo prepara para funcionar antes de que intervenga el sistema operativo. Es el primer programa que actúa al encender un equipo, y sin él ninguno de los demás —ni el sistema operativo, ni las aplicaciones— podría empezar a trabajar.

## Antes de empezar
- [[software-de-sistema]]: el grupo de programas que gobierna el [[hardware]] y crea el entorno en el que funciona el resto del software.
- [[hardware]]: los componentes físicos que el firmware prepara; esta nota no explica su construcción interna, solo el software que los pone en marcha.

## Explicación
Todo software indica al hardware qué hacer, pero no todo software vive en el mismo lugar ni actúa en el mismo momento. El [[sistema-operativo]] es un programa amplio que se carga al arrancar el ordenador y coordina su uso general; en su centro se encuentra el [[nucleo-kernel]], que controla directamente los recursos. El firmware, en cambio, no necesita ser cargado desde un disco como el sistema operativo: ya está dentro del dispositivo al que pertenece, grabado en él, y por eso puede actuar desde el instante en que recibe energía.

Su función es preparar el hardware para el trabajo que vendrá después. Al encender el equipo, comprueba que los componentes esenciales están presentes y responden, inicializa la comunicación básica entre ellos y deja el sistema en condiciones de cargar el siguiente programa. Solo cuando esa preparación termina puede el sistema operativo empezar a organizar procesos, memoria y archivos. El firmware no gestiona el ordenador entero —esa tarea corresponde al sistema operativo y a su núcleo—, sino que pone el dispositivo en un estado mínimo y ordenado a partir del cual el resto del software puede tomar el control.

El firmware no es exclusivo del ordenador completo: cada dispositivo del sistema lleva el suyo. Una impresora, una tarjeta de sonido o un adaptador de red necesitan sus propias instrucciones grabadas para saber cómo encenderse y cómo responder a las peticiones que les lleguen. Esa es la diferencia de fondo con los [[controladores-drivers]], que son programas situados en el sistema operativo y le enseñan a manejar cada dispositivo concreto: el firmware pertenece al dispositivo y actúa antes del sistema operativo; el controlador pertenece al sistema operativo y le acompaña después. El caso principal dentro de un ordenador es [[bios-uefi]], el firmware de la placa base que enciende el equipo y localiza el sistema operativo para cargarlo; su funcionamiento detallado se trata en su nota canónica.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-sistema]] se sigue el orden de arranque de un ordenador: primero el firmware despierta y prepara el hardware, después el sistema operativo toma el control general y, en su interior, el núcleo coordina los recursos. Esta nota cubre solo el primer paso, el del software grabado en el dispositivo; el siguiente paso es [[bios-uefi]], que muestra cómo ese arranque se concreta en la placa base de un ordenador.

## Límites de esta explicación
Esta nota no desarrolla cómo funciona [[bios-uefi]] por dentro —reconocimiento de componentes, configuración y carga del sistema operativo—, ni cómo los [[controladores-drivers]] enseñan al sistema operativo a manejar cada dispositivo, ni cómo el [[nucleo-kernel]] reparte procesador y memoria una vez arrancado. Cada uno de esos temas tiene su nota canónica: [[bios-uefi]], [[controladores-drivers]] y [[nucleo-kernel]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
