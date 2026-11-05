---
titulo: "Colisión en tabla hash"
slug: colision-en-tabla-hash
rama: software
categoria: sistema
nivel: 6
prerequisitos: [tabla-hash]
conduce_a: []
alias: ["colisión hash", "colisión en tabla de dispersión", "hash collision"]
estado: borrador
fuentes: [FTE-0005]
---

# Colisión en tabla hash

## Idea central
Una colisión en tabla hash es la situación en la que dos claves distintas de una [[tabla-hash]] producen la misma posición. Es el precio inevitable de reducir el número de posiciones disponibles frente al número de claves posibles: la tabla no puede saber qué clave buscada por posición es la buscada si solo mira la posición, por lo que debe comprobar la clave guardada y resolver el conflicto para que ambas claves coexistan.

## Antes de empezar
- [[tabla-hash]]: la estructura de datos que guarda pares de clave y valor calculando la posición de cada elemento a partir de su clave, sin recorrer la colección.

## Explicación
En una tabla hash, cada posición puede corresponder a varias claves diferentes, porque la función de dispersión —la operación que convierte una clave en una posición— descarta información al reducir un conjunto grande de claves posibles a un número menor de posiciones. Dos claves que no tienen ninguna relación entre sí pueden dar por resultado el mismo número. A este hecho se le llama colisión.

Cuando se inserta la segunda de las claves que colisionan, la posición calculada ya está ocupada por la primera. No es posible simplemente sobrescribirla, porque se perdería la primera clave. Cuando se busca una clave, tampoco basta con acudir a su posición y suponer que el elemento encontrado es el buscado: hay que comprobar que la clave almacenada coincide con la clave buscada. Esa comprobación —comparar claves, no solo posiciones— es la base de toda resolución de colisiones: dos claves pueden compartir posición, pero siguen siendo elementos distintos.

Resolver una colisión significa decidir dónde se guarda cada clave que comparte posición y cómo se encuentran después. Existen dos ideas generales para ello. La primera es el encadenamiento: cada posición mantiene una pequeña lista de los elementos cuyas claves caen en ella, y la búsqueda recorre esa lista comparando claves hasta encontrar la coincidencia. La segunda es el sondeo: si la posición calculada está ocupada por otra clave, se prueba la siguiente posición libre de la tabla según una secuencia de sondeo, y la búsqueda sigue esa misma secuencia hasta dar con la clave. En ambos casos, la posición calculada es solo el punto de partida, no la garantía de hallar el elemento.

Las colisiones no son un error de la tabla, sino una consecuencia de su diseño. Una buena función de dispersión las hace menos frecuentes repartiendo las claves de forma uniforme entre las posiciones, pero no puede eliminarlas del todo, porque siempre habrá más claves posibles que posiciones. Por eso el coste de una tabla hash crece cuando muchas claves colisionan: cada búsqueda o inserción debe comparar más claves antes de dar con la suya. Dimensionar la tabla con suficientes posiciones y elegir una dispersión adecuada mantiene ese coste bajo, pero la posibilidad de colisión permanece siempre y debe gestionarse.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[tabla-hash]] se llega a la colisión al preguntarse qué ocurre con la afirmación de que cada clave produce una posición única: la posición es única para una clave dada, pero varias claves pueden producir la misma. Esta nota cierra ese peldaño explicando por qué la unicidad de la posición no implica unicidad de la clave y cómo se resuelve el conflicto. No hay un `conduce_a` previsto para esta nota en el contrato; queda como rama terminal de esta línea, sin siguiente paso asignado.

## Límites de esta explicación
Esta nota no trata el detalle de cómo se diseñan las funciones de dispersión para repartir las claves de forma uniforme; eso corresponde a la nota prevista de función de dispersión. Tampoco desarrolla en profundidad cada estrategia de resolución —encadenamiento con listas por posición o sondeo con secuencias de posiciones libres—, que quedan como conceptos nuevos propuestos al orquestador. Tampoco trata la elección del tamaño de la tabla en función de su carga ni las claves especiales, como las claves nulas o repetidas al insertar la misma clave dos veces.

## Referencias
- FTE-0005 (Introduction to Algorithms, Cormen et al., 4ª ed.): colisión en tablas hash, encadenamiento y sondeo.
