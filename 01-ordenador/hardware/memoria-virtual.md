---
titulo: "Memoria virtual"
slug: memoria-virtual
rama: software
categoria: sistema
nivel: 7
prerequisitos: [gestor-de-memoria]
conduce_a: [espacio-de-usuario, espacio-de-kernel, paginacion, segmentacion]
alias: ["memoria virtual", "virtual memory"]
estado: borrador
fuentes: []
---

# Memoria virtual

## Idea central
La memoria virtual es el espacio amplio, ordenado y privado que el sistema operativo ofrece a cada programa en ejecución, en lugar de entregarle porciones sueltas de la memoria física. Permite que cada programa use y piense en direcciones propias, sin conocer dónde están las celdas físicas ni compartirlas con los demás, y aun cuando esos programas, en conjunto, superan la capacidad de la memoria física disponible.

## Antes de empezar
- [[gestor-de-memoria]]: la parte del núcleo que reparte la memoria física limitada entre los programas y la recupera cuando termina el trabajo de cada uno.
- [[memoria-ram]]: la memoria principal física y volátil del ordenador, cuyo espacio limitado motiva esta abstracción.

## Explicación
En un reparto directo, el gestor de memoria entrega a cada programa una porción de memoria física y ese programa trabaja sobre posiciones físicas concretas. Con la memoria virtual, el programa deja de ver esas posiciones físicas. Trabaja con direcciones virtuales, esto es, posiciones de su propio espacio de direcciones, el conjunto ordenado de lugares que el sistema le asigna como si fueran suyos. Que un programa pida el lugar diez mil en su propio espacio no significa que ese lugar exista a la fuerza como celda física concreta con ese mismo número.

La traducción entre un espacio y otro es la clave de la idea. Cada vez que un programa usa una dirección virtual, el sistema la convierte en una dirección física real de memoria RAM, o la sustituye por otra parte de su contenido que sí está en RAM en ese momento. Esa conversión permite dos cosas a la vez. Primero, que dos programas usen la misma dirección virtual sin pisarse, porque cada uno vive en su propio espacio y el sistema dirige cada pedido a celdas distintas. Segundo, que un programa pueda tener más contenido del que cabe en la RAM en un instante dado, porque parte de su espacio puede esperar en el [[almacenamiento]], el espacio de retención del ordenador, mientras otra parte se usa en RAM.

El programa no nota el cambio. Ve un espacio regular, como si tuviera una gran memoria propia y continua para sus instrucciones y datos. No necesita saber en qué orden las porciones se reparten por la memoria física, qué partes están en un momento dado en [[memoria-ram]] y cuáles esperan en almacenamiento, ni qué direcciones físicas ocupan otros programas. Esa ocultación también protege: si un programa intenta usar una dirección fuera de su propio espacio, el sistema lo detiene en lugar de dejarle alcanzar lugares ajenos.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[gestor-de-memoria]] se pasa del reparto de un recurso físico limitado entre programas que lo solicitan a la vez, a una abstracción que cambia por completo lo que cada programa ve: en lugar de competir a ciegas por celdas físicas, cada programa recibe un espacio virtual amplio, ordenado y privado, y el sistema se encarga de mantenerlo sobre la memoria real. El paso siguiente distingue las dos partes de ese espacio que importan para la seguridad y el privilegio: [[espacio-de-usuario]], la zona donde trabajan los programas ordinarios, y [[espacio-de-kernel]], la zona privilegiada donde trabaja el núcleo. Los mecanismos concretos que realizan la división y la traducción, [[paginacion]] y [[segmentacion]], se estudian después, en su propio peldaño.

## Límites de esta explicación
Esta nota no explica cómo se divide el espacio en páginas ni cómo se traduce cada dirección de forma concreta; eso se trata en [[paginacion]]. Tampoco explica el modelo alternativo de dividir el espacio en segmentos independientes; eso se trata en [[segmentacion]]. No explica el contenido físico de la memoria, materia de [[memoria-ram]], ni cómo se organizan los datos dentro del espacio, materia de [[estructuras-de-datos]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
