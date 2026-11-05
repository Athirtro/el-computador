---
titulo: "Árbol"
slug: arbol
rama: software
categoria: sistema
nivel: 5
prerequisitos: [estructuras-de-datos]
conduce_a: []
alias: ["árbol"]
estado: borrador
fuentes: []
---

# Árbol

## Idea central
Un árbol es una estructura de datos en la que cada elemento puede depender de otros elementos en varios niveles, formando jerarquías. Permite representar relaciones de dependencia —por ejemplo, carpetas que contienen carpetas— sin tener que aplanarlas en una sola secuencia.

## Antes de empezar
- [[estructuras-de-datos]]: la organización de los datos en memoria para poder buscarlos, modificarlos o recorrerlos. Esta nota es una de las organizaciones posibles dentro de esa idea general.

## Explicación
Partimos de una organización de datos en memoria y nos preguntamos qué ocurre cuando la relación entre elementos deja de ser lineal. En una secuencia, cada elemento tiene un predecesor y un sucesor; en una jerarquía, un elemento puede tener varios elementos bajo su dependencia, y cada uno de esos puede tener a su vez otros. El árbol es la forma de organizar esos datos cuando la dependencia tiene niveles.

Cada elemento del árbol se llama nodo. Un nodo guarda un valor y las referencias a los nodos que dependen directamente de él. Si un nodo $A$ depende de otro nodo $B$ en el nivel inmediatamente superior, $B$ es el padre de $A$ y $A$ es un hijo de $B$; un nodo puede tener varios hijos, pero solo un padre, salvo el nodo inicial. Ese nodo inicial, el único que no tiene padre, es la raíz, y desde él se alcanzan todos los demás siguiendo referencias de padre a hijo. Los nodos que no tienen hijos se llaman hojas. La posición de un nodo en la jerarquía se mide en niveles: la raíz está en el nivel superior y cada paso de padre a hijo baja un nivel.

Esta organización cambia el coste de las operaciones frente a las estructuras lineales. Buscar un elemento no exige recorrer toda la secuencia, porque se desciende desde la raíz siguiendo la jerarquía; insertar o eliminar un nodo solo afecta a su padre y a sus hijos, sin desplazar bloques completos de datos. A cambio, recorrer el árbol entero es más complejo que recorrer una secuencia, porque hay que visitar cada rama respetando los niveles. La elección del árbol se justifica, por tanto, cuando la información tiene una dependencia jerárquica natural y la operación frecuente es localizar un elemento dentro de esa jerarquía.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[estructuras-de-datos]] se llega al árbol al concretar la idea de organización jerárquica que allí se anunciaba en una línea: los nodos, el padre, los hijos, la raíz y las hojas son el peldaño que convierte esa mención en un concepto explicado. Esta nota no conduce directamente a ninguna otra: es una rama terminal de la cadena de estructuras de datos, y el lector que la haya comprendido puede pasar a otras organizaciones, como [[tabla-hash]], sin que esta nota sea un paso obligatorio hacia ella.

## Límites de esta explicación
Esta nota no trata la organización por clave calculada, que se trata en [[tabla-hash]]. Tampoco trata cómo se representan estos datos de forma persistente en disco, tratado en [[formatos-de-archivos]], ni variantes especializadas del árbol, como los árboles binarios o los árboles equilibrados, que quedan fuera del alcance de este peldaño y requerirían notas propias si el orquestador las aprueba.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
