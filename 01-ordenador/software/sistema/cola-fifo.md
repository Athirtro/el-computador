---
titulo: "Cola FIFO"
slug: cola-fifo
rama: software
categoria: sistema
nivel: 5
prerequisitos: [estructuras-de-datos]
conduce_a: []
alias: ["cola FIFO", "first in, first out"]
estado: borrador
fuentes: []
---

# Cola FIFO

## Idea central
Una cola FIFO es una estructura de datos en la que los elementos se extraen en el mismo orden en el que fueron insertados, es decir, primero en entrar primero en salir. Sirve para gestionar esperas en orden de llegada: ningún elemento nuevo puede adelantar a los ya presentes.

## Antes de empezar
- [[estructuras-de-datos]]: la organización de la información en memoria que hace posible encontrar, insertar y recorrer los datos de un programa.

## Explicación
Una cola FIFO (first in, first out) es una forma concreta de organizar datos en memoria según el orden en que llegan. Sus dos extremos tienen funciones distintas y fijas: por un extremo se introducen los elementos nuevos y por el otro extremo se retiran los que han esperado más tiempo. El orden de extracción es, por tanto, el mismo que el de inserción, de modo que el primero en entrar es también el primero en salir.

La cola admite dos operaciones básicas. Encolar consiste en añadir un elemento por el extremo de entrada sin alterar la posición de los que ya esperan; quien llega se sitúa detrás de todos los anteriores. Desencolar consiste en retirar el elemento por el extremo de salida, que es siempre el que lleva más tiempo esperando, y descartarlo o entregarlo para su procesamiento. La cola se dice vacía cuando no guarda ningún elemento y solo puede desencolverse cuando contiene al menos uno.

Esta disciplina impone una regla de equidad estricta. No existe acceso directo al interior: no se puede extraer un elemento intermedio sin extraer antes todos los que están por delante, ni insertar uno por el principio saltando la espera. Esa restricción es precisamente lo que hace útil a la cola. Cuando varios elementos compiten por ser atendidos —peticiones, mensajes o trabajos—, atenderlos en orden de llegada evita favoritismos y hace predecible el comportamiento del sistema.

Conviene distinguir la cola de una organización que simplemente guarda elementos en el orden en que los recibió. Sin la regla de extracción por el extremo más antiguo, la información del orden de llegada no tendría consecuencias operativas. La cola se define por esa consecuencia: el orden de entrada es también el orden de salida, y todas las operaciones preservan esa propiedad.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[estructuras-de-datos]] se llega a la cola FIFO al pasar de la idea general de organizar datos en memoria a una organización concreta basada en el orden de llegada. La persona que comprende por qué la disposición de los datos determina el coste de buscar, insertar o recorrer comprende también qué aporta esta estructura: convierte el orden temporal de entrada en una regla de servicio. En el mapa vigente esta nota es una rama de salida sin notas posteriores asignadas.

## Límites de esta explicación
Esta nota no trata la pila, estructura en la que el último elemento en entrar es el primero en salir y que responde a una regla de servicio opuesta, ni el detalle de cómo se implementa una cola con arreglos, listas enlazadas u otros mecanismos concretos. Tampoco trata cómo el sistema operativo usa colas para organizar procesos o peticiones, que corresponde a notas posteriores del sistema.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
