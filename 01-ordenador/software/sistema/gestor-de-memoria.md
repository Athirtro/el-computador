---
titulo: "Gestor de memoria"
slug: gestor-de-memoria
rama: software
categoria: sistema
nivel: 6
prerequisitos: [gestion-de-recursos]
conduce_a: [memoria-virtual]
alias: ["gestor de memoria", "memory manager"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Gestor de memoria

## Idea central
El gestor de memoria es la parte de la actividad del núcleo que decide cuánta memoria tiene disponible cada programa mientras trabaja, y que la recupera cuando el programa lo deja de necesitar o termina. Existe porque la memoria principal es limitada y varios programas la solicitan a la vez.

## Antes de empezar
- [[gestion-de-recursos]]: el ciclo común de solicitud, concesión, espera, uso y recuperación con que el núcleo reparte los recursos limitados entre los programas.

## Explicación
Un programa, al ponerse en ejecución, necesita memoria para guardar sus instrucciones y los datos con que trabaja. Como esa memoria es la [[memoria-ram]], el espacio físico principal y volátil del ordenador, no puede entregarse entera a un solo programa sin dejar a los demás sin lugar donde trabajar. El gestor de memoria se encarga de dividirla en porciones y asignar cada porción a un programa concreto.

El reparto sigue el mismo ciclo descrito para cualquier recurso. Un programa solicita memoria; el gestor comprueba cuánta queda libre y concede una porción; el programa la utiliza mientras trabaja; y, cuando termina o libera una parte que ya no necesita, el gestor la recupera para ponerla a disposición de la siguiente petición. La recuperación es tan importante como la concesión: sin ella, porciones ya inútiles quedarían apartadas para siempre y el espacio disponible se agotaría aunque el ordenador tuviera memoria libre.

El reparto no se limita a entregar porciones sin orden. Si el gestor concede a un programa más memoria de la que va a usar, esa memoria queda retenida e inutilizable para los demás; si la concede en fragmentos dispersos, la memoria libre puede quedar partida en huecos pequeños que no sirven para una petición grande, aunque en total haya espacio suficiente. Por eso el gestor debe decidir cuánto conceder, en qué porciones y en qué momento recuperar, equilibrando el aprovechamiento con la disponibilidad para las peticiones siguientes. Gestionar memoria es el caso concreto, para este recurso, de las exigencias generales ya descritas: aprovechar el recurso, respetar las preferencias establecidas, evitar que alguien quede esperando para siempre y no permitir que un programa retenga lo que otros necesitan.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[gestion-de-recursos]] se pasa del esquema general de reparto a su aplicación a un recurso concreto: la memoria. [[gestor-de-procesos]] hace lo mismo con el procesador y [[gestor-de-memoria]] con la memoria, dividiendo un espacio físico limitado entre programas que lo solicitan a la vez. El siguiente paso muestra por qué ese reparto físico directo no basta en los sistemas actuales y cómo el sistema ofrece a cada programa un espacio mayor y más sencillo de usar: [[memoria-virtual]].

## Límites de esta explicación
Esta nota no explica cómo se construye ese espacio ampliado ni cómo se traduce cada petición de un programa a posiciones físicas concretas; eso se trata en [[memoria-virtual]], de la que esta nota es prerequisito. Tampoco explica cómo se asigna el procesador entre los programas en ejecución, tarea de [[gestor-de-procesos]], ni el contenido físico de la memoria, materia de [[memoria-ram]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
