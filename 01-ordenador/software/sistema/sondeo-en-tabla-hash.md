---
titulo: "Sondeo en tabla hash"
slug: sondeo-en-tabla-hash
rama: software
categoria: sistema
nivel: 7
prerequisitos: [colision-en-tabla-hash]
conduce_a: []
alias: ["direccionamiento abierto", "open addressing"]
estado: borrador
fuentes: [FTE-0005]
---

# Sondeo en tabla hash

## Idea central
El sondeo en tabla hash, o direccionamiento abierto (open addressing), es la resolución de una [[colision-en-tabla-hash]] sin listas auxiliares: si la posición calculada para una clave está ocupada por otra clave, se busca la siguiente posición libre según una secuencia de sondeo. La tabla sigue siendo un único vector de posiciones, y la clave buscada se encuentra recorriendo esa misma secuencia desde su posición inicial.

## Antes de empezar
- [[colision-en-tabla-hash]]: la situación en la que dos claves distintas producen la misma posición y es obligatorio comprobar la clave guardada antes de dar un elemento por encontrado.

## Explicación
En una [[tabla-hash]], cada clave se coloca en la posición que indica la [[funcion-de-dispersion]]. Cuando dos claves colisionan, la segunda no puede sobrescribir a la primera, porque se perdería. El sondeo resuelve el conflicto manteniendo ambas claves dentro del mismo vector: la primera ocupa la posición calculada y la segunda ocupa la siguiente posición libre de la secuencia de sondeo. La secuencia parte de la posición inicial y avanza con pasos regulares a través de la tabla, volviendo al principio si llega al final, de modo que toda la tabla puede recorrerse en el peor caso.

Con la secuencia definida de forma abstracta, la posición de prueba $i$-ésima de una clave $k$ se expresa como $h(k,i)$, donde $h(k,0)$ es la posición calculada por la función de dispersión y cada $i$ siguiente designa la siguiente posición libre candidata. Para insertar una clave se recorren las posiciones de la secuencia hasta hallar una libre; para buscar una clave se recorren las mismas posiciones comparando la clave guardada en cada una con la clave buscada, y se detiene la búsqueda al encontrarla o al topar con una posición vacía, que demuestra que la clave no está en la tabla. La inserción y la búsqueda obedecen la misma secuencia, y esa simetría es lo que hace posible encontrar después lo que se guardó antes.

El sondeo funciona porque la posición calculada deja de ser el único lugar posible de una clave y pasa a ser el punto de partida de su búsqueda. A cambio, cuando la tabla está muy llena, las secuencias de varias claves se solapan y cada búsqueda debe comparar más claves ajenas antes de dar con la suya o con un hueco. El sondeo no elimina ese coste; lo mantiene acotado mientras la tabla conserve posiciones libres suficientes.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[colision-en-tabla-hash]] se llega al sondeo al precisar una de las dos resoluciones que aquella nota solo enunció: allí se explicó que una clave que colisiona puede guardarse en la siguiente posición libre de una secuencia, y aquí se desarrolla esa idea como mecanismo completo de inserción y búsqueda. No hay un `conduce_a` previsto para esta nota en el contrato; queda como rama terminal de esta línea, sin siguiente paso asignado.

## Límites de esta explicación
Esta nota no trata el encadenamiento, la resolución alternativa en la que cada posición guarda una lista de claves que caen en ella, prevista como nota propia en el mapa. Tampoco entra en las estrategias concretas de construcción de la secuencia de sondeo más allá de la siguiente posición libre, ni en la elección del tamaño de la tabla en función de su ocupación; ambas quedan fuera de este peldaño.

## Referencias
- FTE-0005 (Introduction to Algorithms, Cormen et al., 4ª ed.): sondeo como resolución de colisiones por direccionamiento abierto y recorrido de la secuencia de posiciones.
