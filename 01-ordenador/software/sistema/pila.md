---
titulo: "Pila"
slug: pila
rama: software
categoria: sistema
nivel: 5
prerequisitos: [estructuras-de-datos]
conduce_a: []
alias: ["pila LIFO"]
estado: borrador
fuentes: [FTE-0001, FTE-0002, FTE-0005]
---

# Pila

## Idea central
La pila es una estructura de datos en la que solo se puede insertar o retirar elementos por un extremo, llamado cima. La última en entrar es la primera en salir, criterio conocido como LIFO (last in, first out). Su interés reside en que ese orden coincide con el orden anidado en que un programa llama a funciones y regresa de ellas.

## Antes de empezar
- [[estructuras-de-datos]]: la organización de la información en memoria para hacer eficientes las operaciones de buscar, insertar, eliminar o recorrer.

## Explicación
Una pila se comporta como una pila de fichas: no se puede sacar una ficha del medio sin retirar antes las que tiene encima. Esa restricción es su única regla de acceso. Todas las inserciones, empujar un elemento, y todas las eliminaciones, sacar un elemento, ocurren por la cima, en el mismo extremo. Los elementos que no están en la cima permanecen inaccesibles hasta que los que los cubren han salido.

El orden que resulta es LIFO por necesidad. Si se insertan A, B y C en ese orden, C queda en la cima y será el primer elemento disponible para retirar, seguido de B y, por último, de A. La pila no permite el acceso directo a un elemento por su posición, como ocurre en un arreglo, ni el recorrido ordenado de todos sus elementos sin vaciarla. A cambio, inserción y eliminación por la cima son siempre operaciones inmediatas sobre el último elemento introducido.

Esta disciplina encaja con el mecanismo de llamada a funciones. Una llamada a una función es una instrucción que transfiere el control a otra parte del programa guardando el punto de regreso, es decir, la instrucción siguiente a la que volverá cuando la función invitada termine. Al producirse una llamada, el programa empuja en la pila la información necesaria para retomar la llamada anterior: el punto de regreso y el estado local de la función que llama. Cuando la función invitada acaba, retira de la cima su propio estado y recupera el punto de regreso para devolver el control.

La correspondencia se explica porque las llamadas están anidadas: una función puede llamar a otra y ésta a una tercera, pero cada una debe regresar antes de que regrese la que la llamó. El orden LIFO garantiza que la función más reciente en intervenir sea también la primera en retirarse, como exige la cadena de retornos. La pila, por tanto, no es solo una organización genérica, sino el mecanismo que hace posible coordinar llamadas anidadas sin que cada función tenga que gestionar manualmente el orden de restauración.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[estructuras-de-datos]] se llega a la pila al pasar de la idea general de organizar datos en memoria a una regla concreta de acceso: solo por la cima. La pila especializa esa idea para un tipo de uso en el que el orden de retirada debe ser el inverso al de llegada, y su caso principal son las llamadas anidadas. No hay un peldaño posterior asignado a esta nota.

## Límites de esta explicación
Esta nota no trata la cola, estructura en la que la eliminación ocurre por el extremo contrario al de inserción, ni el árbol, organización jerárquica con varios niveles de dependencia; ambas quedan para sus notas propias previstas en el mapa del libro. Tampoco detalla cómo se implementa la pila en memoria ni cómo la gestiona el sistema operativo en cada proceso.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): pilas en la gestión de llamadas del sistema.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): pilas en la gestión de llamadas del sistema.
- FTE-0005 (Introduction to Algorithms, Cormen et al., 4ª ed.): definición LIFO y operaciones de la pila.
