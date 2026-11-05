---
titulo: "Encadenamiento en tabla hash"
slug: encadenamiento-en-tabla-hash
rama: software
categoria: sistema
nivel: 7
prerequisitos: [colision-en-tabla-hash]
conduce_a: []
alias: ["encadenamiento", "resolución por encadenamiento", "separate chaining"]
estado: borrador
fuentes: [FTE-0005]
---

# Encadenamiento en tabla hash

## Idea central
El encadenamiento es la forma de resolver una [[colision-en-tabla-hash]] conservando una lista de claves por cada posición de la [[tabla-hash]]. En lugar de desplazar las claves que colisionan a otra posición, la tabla acepta que varias claves compartan posición y las guarda juntas, en una lista que se recorre comparando claves hasta encontrar la buscada.

## Antes de empezar
- [[colision-en-tabla-hash]]: dos claves distintas pueden producir la misma posición, por lo que la posición calculada es solo el punto de partida y hay que comprobar la clave guardada.

## Explicación
En una tabla hash sin encadenamiento, cada posición guarda como máximo un elemento. Si una clave ya ocupa su posición y llega otra clave que produce la misma posición, hay que decidir dónde colocar la segunda. El encadenamiento —también llamado encadenamiento separado (*separate chaining*)— resuelve ese conflicto sin mover nada fuera de la posición: cada posición deja de guardar un único elemento y pasa a guardar el primero de una lista de los elementos cuyas claves caen en esa posición. Una lista aquí es una cadena de nodos, cada uno con una clave, su valor asociado y un enlace —una referencia a la memoria— al siguiente nodo; la posición guarda el enlace al primer nodo, o indica que la lista está vacía. Usando la palabra cubeta para la lista de una posición, la tabla es un conjunto de cubetas y la función de dispersión elige a qué cubeta va cada clave.

Insertar una clave encadenada consiste en calcular su posición y añadir el nuevo nodo a la cubeta de esa posición; la colocación habitual es al principio de la lista, porque no exige recorrerla. Buscar una clave consiste en calcular su posición y recorrer solo la cubeta de esa posición comparando la clave buscada con cada clave guardada hasta encontrarla o agotar la lista. Eliminar es retirar el nodo correspondiente de su cubeta y enlazar el anterior con el siguiente, sin tocar los demás elementos de la tabla.

La idea clave es que la búsqueda ya no depende de que la posición esté libre: la posición localiza la cubeta, y dentro de la cubeta se resuelve la identidad de la clave. Por eso el encadenamiento tolera bien las colisiones: si dos claves colisionan, la segunda no expulsa a la primera ni desplaza a nadie, y si colisionan diez, basta con recorrer diez nodos en el peor caso de esa cubeta. Esa diferencia afecta al coste. Si la tabla tiene $m$ posiciones y guarda $n$ elementos, el factor de carga $\alpha = n/m$ mide cuántos elementos caen de media por cubeta. Con una buena función de dispersión, el coste medio de buscar, insertar o eliminar queda en torno a $O(1 + \alpha)$, es decir, constante mientras $\alpha$ se mantenga bajo. El peor caso —todas las claves en la misma cubeta— degrada la operación a recorrer la lista entera, como en una búsqueda lineal.

La ventaja práctica de esta organización es su sencillez: no hay que decidir qué posición libre probar ni preocuparse por que las claves almacenadas estorben a otras; cada cubeta actúa de forma independiente y las operaciones de inserción y eliminación son locales. Su coste es memoria adicional para los enlaces de la lista y para las cubetas vacías que una tabla grande mantiene aunque pocas claves las usen. Por eso el encadenamiento funciona mejor cuando la tabla se dimensiona con posiciones suficientes para mantener el factor de carga bajo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[colision-en-tabla-hash]] se llega a esta nota al preguntarse dónde se guardan y cómo se encuentran las claves que comparten posición. La colisión establece que la posición no basta para identificar la clave; el encadenamiento aporta la respuesta estructural: todas las claves de una posición conviven en una lista por posición y la comprobación de claves se hace recorriendo esa lista. No hay un `conduce_a` previsto para esta nota en el contrato, por lo que queda como rama terminal de esta línea; su contraste natural es [[sondeo-en-tabla-hash]], que resuelve el mismo conflicto buscando otra posición.

## Límites de esta explicación
Esta nota no trata el [[sondeo-en-tabla-hash]], la alternativa que resuelve la colisión probando posiciones libres según una secuencia de sondeo. Tampoco trata cómo elegir la función de dispersión que reparte las claves entre cubetas —ver [[funcion-de-dispersion]]—, ni la elección del tamaño de la tabla a partir del factor de carga admisible ni el redimensionado cuando la tabla se llena.

## Referencias
- FTE-0005 (Introduction to Algorithms, Cormen et al., 4ª ed.): resolución de colisiones por encadenamiento en tablas hash, listas por posición y coste medio según factor de carga.
