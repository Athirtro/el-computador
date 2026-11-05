---
titulo: "Espacio de kernel"
slug: espacio-de-kernel
rama: software
categoria: sistema
nivel: 8
prerequisitos: [memoria-virtual]
conduce_a: []
alias: ["kernel space"]
estado: borrador
fuentes: []
---

# Espacio de kernel

## Idea central
El espacio de kernel es la parte reservada del espacio virtual de direcciones donde reside y trabaja solo el núcleo. Es la zona privilegiada donde el núcleo accede a toda la memoria y al hardware, separada de la zona de los programas ordinarios para que ningún programa de usuario pueda llegar a ella directamente.

## Antes de empezar
- [[memoria-virtual]]: la abstracción que da a cada programa un espacio de direcciones propio y ordenado, y que el sistema traduce a memoria física real.

## Explicación
Tras la memoria virtual, cada programa ve su propio espacio de direcciones como si fuera suyo y continuo. En un sistema real, ese espacio no es homogéneo: una parte está pensada para los programas de usuario y otra está reservada al núcleo. Esta segunda parte es el espacio de kernel.

El núcleo es el programa que puede entrar en esa zona. En el espacio de kernel viven su código, sus estructuras de datos internas y las traducciones que le permiten llegar a cualquier celda física de [[memoria-ram]] y a los dispositivos. Por eso se habla de zona privilegiada: no es una zona más para almacenar datos propios de una aplicación, sino el lugar desde el que el núcleo puede revisar, repartir, proteger o mapear el resto de la memoria sin pedir permiso a ningún programa.

La separación entre lo privilegiado y lo no privilegiado protege en ambos sentidos. Un programa ordinario, que trabaja en [[espacio-de-usuario]], no puede entrar por su cuenta en el espacio de kernel, ni leer ni escribir allí, y un fallo de un programa no debería corromper las estructuras del núcleo. Cuando un programa necesita algo que solo el núcleo puede hacer, le pide el servicio por un cauce controlado y el núcleo lo ejecuta en su propio espacio; el programa no se traslada allí, solo recibe el resultado cuando el servicio termina.

La división concreta entre las dos zonas, con qué parte del espacio de direcciones cae en cada lado y cómo el procesador distingue el acceso permitido del prohibido, es el mecanismo de traducción y de protección. Esta nota solo establece el hecho previo: en un espacio virtual compartido hay un lado para el usuario y otro, privilegiado, para el núcleo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[memoria-virtual]] se pasa del espacio virtual privado de cada programa a su división interna. En el lado a donde van los programas ordinarios se aplica el [[espacio-de-usuario]]; en el lado reservado vive [[nucleo-kernel]] y se aplica esta nota. No se introduce un peldaño siguiente, porque aquí se cierra el recorrido de memoria virtual iniciado en el gestor de memoria: ya aparece la zona privilegiada como concepto propio, separado de la zona de usuario.

## Límites de esta explicación
Esta nota no explica qué hay en la zona de usuario ni cómo se asigna allí la memoria de cada programa; eso se trata en [[espacio-de-usuario]]. Tampoco explica cómo el núcleo coordina el uso de la memoria, materia de [[gestion-de-recursos]], ni cómo funciona el cauce por el que un programa pide un servicio al núcleo. La figura del núcleo como centro de control pertenece a [[nucleo-kernel]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
