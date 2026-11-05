---
titulo: "Segmentación"
slug: segmentacion
rama: software
categoria: sistema
nivel: 8
prerequisitos: [memoria-virtual]
conduce_a: []
alias: ["segmentación", "segmentation"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Segmentación

## Idea central
La segmentación es un modo de dividir el espacio de direcciones virtuales que ofrece [[memoria-virtual]] en trozos independientes de tamaño variable, cada uno con un sentido lógico propio. En lugar de un único espacio lineal, el programa ve varias regiones separadas —por ejemplo, una para el código, otra para los datos y otra para la pila— y cada dirección se forma diciendo en qué segmento se está y en qué posición dentro de ese segmento.

## Antes de empezar
- [[memoria-virtual]]: la abstracción que da a cada programa un espacio amplio, ordenado y privado, y que traduce las direcciones virtuales a posiciones físicas en [[memoria-ram]] o a contenido que espera en almacenamiento.

## Explicación
El punto de partida es el problema de la memoria virtual: un programa trabaja con direcciones virtuales y no conoce las direcciones físicas. La segmentación decide cómo se organiza ese espacio virtual antes de traducirlo. En vez de tratarlo como un único bloque continuo, lo corta en segmentos. Un segmento es una región independiente con su propio inicio, su propio tamaño y su propia función lógica. Dos segmentos pueden tener tamaños distintos en un mismo programa, y el tamaño de un segmento puede cambiar sin necesidad de mover los demás.

Por eso una dirección ya no es un solo número dentro de un bloque único, sino una pareja: un selector que elige el segmento y un desplazamiento que indica la posición dentro de ese segmento. La traducción necesita saber, para cada segmento, en qué posición física de la memoria empieza y hasta dónde se extiende. Si el desplazamiento cae fuera de ese rango, el acceso es inválido y el sistema lo detiene, igual que en la memoria virtual general detiene un acceso fuera del espacio concedido.

Esta división aporta dos ventajas claras. La primera es semántica: los segmentos reflejan cómo el programa entiende su propio contenido, así que es natural aplicar permisos distintos a cada uno —por ejemplo, permitir leer y ejecutar el segmento de código, pero no escribir en él, y permitir leer y escribir en el segmento de datos, pero no ejecutarlo—. La segunda es de aislamiento: cada segmento se comprueba por separado, de modo que un programa no puede alcanzar por accidente la zona lógica de otro tipo de contenido ni la de otro programa sin pasar por la traducción.

El precio de esta flexibilidad es la fragmentación. Como los segmentos son de tamaño variable y pueden crecer, acortarse o liberarse, la memoria física puede quedar llena de huecos sueltos demasiado pequeños para encajar un segmento nuevo, aunque en total quede espacio libre suficiente. Reunir esos huecos exige mover segmentos ya colocados, con el coste que eso supone. Esa tensión entre expresividad lógica y dificultad para colocar piezas de tamaño irregular es el rasgo que distingue a la segmentación.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[memoria-virtual]] se pasa de la idea general de un espacio privado y traducido a una forma concreta de organizarlo: la segmentación responde a la pregunta de cómo se reparte ese espacio entre piezas con sentido lógico, por medio de segmentos independientes identificados por un selector y recorridos por un desplazamiento. No hay un siguiente paso obligado desde esta nota; el mecanismo alternativo para dividir el espacio, con piezas de tamaño fijo, se trata en [[paginacion]].

## Límites de esta explicación
Esta nota no explica el detalle de la división en piezas de tamaño fijo ni el mecanismo con que se traduce cada dirección de forma concreta; eso se trata en [[paginacion]]. Tampoco explica cómo se organizan los datos dentro de cada segmento, materia de [[estructuras-de-datos]], ni las zonas de usuario y de núcleo del espacio, materia de [[espacio-de-usuario]] y [[espacio-de-kernel]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
