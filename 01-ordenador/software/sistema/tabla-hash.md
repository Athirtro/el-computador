---
titulo: "Tabla hash"
slug: tabla-hash
rama: software
categoria: sistema
nivel: 5
prerequisitos: [estructuras-de-datos]
conduce_a: []
alias: ["tabla hash", "tabla de dispersión", "hash table"]
estado: borrador
fuentes: []
---

# Tabla hash

## Idea central
La tabla hash es una estructura de datos que organiza pares de clave y valor en memoria para localizar un valor directamente a partir de su clave. En lugar de recorrer todos los elementos, calcula la posición donde debe estar guardado ese elemento. Esa localización inmediata es su utilidad esencial.

## Antes de empezar
- [[estructuras-de-datos]]: la organización de la información en memoria para poder buscarla, modificarla o recorrerla.

## Explicación
Una tabla hash parte de un conjunto de posiciones —habitualmente un arreglo— en las que se guardan los elementos. Cada elemento se reconoce por una clave, es decir, por un valor representativo que lo identifica frente a los demás, como el nombre de un usuario o un número de cuenta. Junto a cada clave se guarda el valor asociado a ella.

La clave por sí sola no indica en qué posición de la tabla se encuentra su valor. Para pasar de una a otra se emplea una función de dispersión: una operación, definida por el programa, que toma la clave como entrada y devuelve un número que se usa como posición dentro de la tabla. La misma clave produce siempre la misma posición, de modo que buscar un elemento consiste en aplicar de nuevo esa función y acudir directamente a la posición calculada, sin recorrer los demás elementos. Insertar un elemento nuevo supone aplicar la función a su clave y guardarlo en la posición resultante; eliminar o consultar un elemento existente sigue el mismo procedimiento.

Esta organización convierte la búsqueda por clave en un acceso prácticamente directo, a diferencia de una estructura secuencial, donde localizar un elemento por su posición exige seguir su índice, o de una lista, donde hay que recorrer los enlaces uno a uno. El precio de esa inmediatez es que la posición no depende del orden de llegada ni del contenido completo del elemento, sino solo de su clave y de la función elegida. Si la tabla se llena demasiado, las posiciones calculadas se reparten peor y el acceso deja de ser tan directo, por lo que la tabla debe dimensionarse pensando en cuántos elementos va a contener.

Puede ocurrir que dos claves distintas produzcan la misma posición; entonces ambas quedan asociadas a un mismo lugar de la tabla. Esta nota no desarrolla cómo se resuelven esos casos ni cómo se eligen o ajustan las funciones de dispersión en la práctica.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[estructuras-de-datos]] se llega a la tabla hash al pasar de la idea general de organizar los datos en memoria a una organización concreta orientada a la búsqueda por clave: ya no se recorre la colección, sino que se calcula dónde debe estar el elemento. No hay un `conduce_a` previsto para esta nota en el contrato; queda como rama terminal de esta línea, sin siguiente paso asignado.

## Límites de esta explicación
Esta nota no trata el detalle de las colisiones —cuándo dos claves caen en la misma posición y cómo se guardan ambas—, ni el diseño de funciones de dispersión concretas, ni la elección del tamaño de la tabla en función de su carga. Tampoco trata la representación de estos datos en disco, que corresponde a [[formatos-de-archivos]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
