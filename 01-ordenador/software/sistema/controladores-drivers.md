---
titulo: "Controladores (drivers)"
slug: controladores-drivers
rama: software
categoria: sistema
nivel: 4
prerequisitos: [sistema-operativo]
conduce_a: []
alias: ["controladores", "drivers", "controladores de dispositivo"]
estado: borrador
fuentes: [FTE-0004]
---

# Controladores (drivers)

## Idea central
Los controladores son los programas que enseñan al [[sistema-operativo]] a manejar un dispositivo concreto. El sistema operativo coordina el ordenador en general, pero cada dispositivo —una impresora, una tarjeta de sonido, un adaptador de red— entiende sus propias instrucciones; el controlador traduce entre ambos.

## Antes de empezar
- [[sistema-operativo]]: el programa que ofrece el entorno integral de trabajo y coordina el uso del hardware, con el [[nucleo-kernel]] como centro. Esta nota parte de ese entorno ya establecido y explica cómo se le añade el conocimiento específico de cada dispositivo.

## Explicación
El sistema operativo no puede conocer internamente todos los dispositivos que pueden conectarse a un ordenador. Cada modelo tiene sus propias operaciones, sus propios formatos de datos y sus propios tiempos de respuesta, y esas diferencias cambian de un fabricante y de una versión a otra. En lugar de meter todo ese conocimiento detallado en el sistema operativo mismo, se organiza en programas separados —los controladores—, uno o varios para cada tipo de dispositivo, que el sistema operativo incorpora cuando necesita usarlo.

La tarea de un controlador es traducir una petición genérica en la secuencia exacta que el dispositivo entiende. Cuando un programa pide, por ejemplo, que se envíe un texto a la impresora o que se reproduzca un sonido, el sistema operativo no sabe todavía en qué orden ni con qué valores concretos debe ordenar al dispositivo que lo haga; quien lo sabe es el controlador de ese modelo. El controlador escribe en los registros del dispositivo —casillas de control internas que guardan órdenes y datos para el propio dispositivo— los valores adecuados, espera la respuesta correspondiente y devuelve el resultado al sistema operativo. De ese modo, las aplicaciones piden servicios sin conocer la electrónica de cada periférico, y el sistema operativo mantiene una forma uniforme de trabajar con dispositivos muy distintos.

Los controladores forman parte del software de sistema porque actúan por cuenta del sistema operativo, en estrecha relación con el [[nucleo-kernel]], que es quien controla directamente los recursos del equipo. Al cambiar el dispositivo sin cambiar el sistema operativo, lo que se cambia es su controlador: la impresora nueva se maneja con el programa adecuado para ella, y el resto del ordenador sigue trabajando igual. Por eso la instalación o la actualización de un controlador es la forma habitual de añadir un dispositivo nuevo o de corregir el manejo de uno ya instalado.

Esto los distingue del [[firmware]]. El firmware está grabado dentro del propio dispositivo y actúa antes de que intervenga el sistema operativo, preparándolo para funcionar; el controlador, en cambio, reside en el sistema operativo y le acompaña durante su funcionamiento normal, enseñándole a manejar ese dispositivo concreto. Uno pertenece al dispositivo, el otro al sistema operativo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sistema-operativo]] se llega a los controladores al preguntarse cómo el entorno integral ya descrito puede tratar con cada dispositivo particular sin dejar de ser un programa general. Esta nota cubre ese paso: el conocimiento específico de cada dispositivo se delega en su controlador. Al ser una rama terminal, no conduce a una nota siguiente dentro de esta escalera; el resto del sistema —núcleo y gestión de recursos— se trata en sus notas canónicas.

## Límites de esta explicación
Esta nota no explica el [[firmware]] de cada dispositivo ni el arranque previo al sistema operativo —eso se trata en [[firmware]] y en [[bios-uefi]]—, ni cómo el [[nucleo-kernel]] asigna el procesador, la memoria y los dispositivos entre los programas que los solicitan —eso se trata en [[nucleo-kernel]] y en [[gestion-de-recursos]]—. Tampoco detalla la operación interna de ningún dispositivo concreto, como una impresora o una tarjeta de sonido, ni el procedimiento práctico de instalar o actualizar un controlador en un sistema determinado.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
