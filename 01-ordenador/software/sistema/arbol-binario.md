---
titulo: "Árbol binario"
slug: arbol-binario
rama: software
categoria: sistema
nivel: 6
prerequisitos: [arbol]
conduce_a: [arbol-equilibrado]
alias: ["árbol binario", "binary tree"]
estado: borrador
fuentes: [FTE-0005]
---

# Árbol binario

## Idea central
Un árbol binario es un [[arbol]] en el que cada nodo tiene como máximo dos hijos, distinguibles como hijo izquierdo e hijo derecho. La distinción entre ambos es estructural: un nodo puede tener solo hijo izquierdo, solo hijo derecho, ambos o ninguno, y esas configuraciones no son equivalentes.

## Antes de empezar
- [[arbol]]: jerarquía de nodos con padre, hijos, raíz y hojas. Esta nota restringe qué formas puede adoptar esa jerarquía: ningún nodo tiene más de dos hijos.

## Explicación
En un árbol general, un nodo puede tener cualquier número de hijos y el orden entre ellos no forma parte de la estructura. En un árbol binario, cada nodo tiene dos posiciones fijas para sus hijos: la izquierda y la derecha. Cada posición puede estar ocupada por un hijo o vacía, de modo que un nodo admite únicamente cuatro configuraciones: sin hijos —es una hoja—, solo hijo izquierdo, solo hijo derecho, o ambos hijos.

Esta restricción parece menor, pero cambia la forma del árbol. Al haber como máximo dos hijos por nodo, la jerarquía se ramifica como máximo en dos direcciones desde cada nodo, y el camino desde la raíz hasta cualquier nodo queda descrito por una sucesión de decisiones izquierda o derecha. Ello permite recorrer el árbol de forma sistemática y sin ambigüedad: en cada nodo se sabe exactamente cuál es el siguiente hijo por cada lado.

La restricción no dice nada sobre el contenido de los nodos. Un árbol binario puede guardar cualquier valor en cada nodo y no impone ninguna relación de orden entre un nodo y sus hijos: la distinción izquierda/derecha es puramente estructural. Tampoco garantiza ninguna forma particular del conjunto. Un árbol binario da forma de cadena, con un solo hijo por nodo, es válido, y uno ramificado de forma uniforme también lo es; lo que se pierde al degenerar en cadena es la ventaja de buscar descendiendo por la jerarquía, porque el recorrido puede llegar a visitar todos los nodos.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[arbol]] se llega a esta nota al restringir el número de hijos por nodo a dos y al darles identidad propia como izquierdo y derecho. El árbol general explicaba la jerarquía; el árbol binario explica una forma concreta y limitada de esa jerarquía, con su regla de cuatro configuraciones por nodo. El siguiente peldaño es [[arbol-equilibrado]]: allí se trata qué ocurre cuando la forma del árbol binario degenera, como en el caso de la cadena, y cómo mantenerlo ramificado para que las operaciones sigan siendo eficientes.

## Límites de esta explicación
Esta nota no trata el equilibrado de árboles binarios, que se trata en [[arbol-equilibrado]]. Tampoco trata la ordenación de los valores de los nodos —por ejemplo, exigir que lo que está a la izquierda sea menor que el nodo—, ni las técnicas concretas de recorrido sistemático del árbol completo, ni su representación en memoria o en disco.

## Referencias
- FTE-0005 (Introduction to Algorithms, Cormen et al., 4ª ed.): definición de árbol binario y estructura de nodos con hijos izquierdo y derecho.
