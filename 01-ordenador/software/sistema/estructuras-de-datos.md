---
titulo: "Estructuras de datos"
slug: estructuras-de-datos
rama: software
categoria: sistema
nivel: 4
prerequisitos: [sistema-operativo]
conduce_a: [formatos-de-archivos]
alias: ["estructuras de datos"]
estado: borrador
fuentes: []
---

# Estructuras de datos

## Idea central

Una estructura de datos es una forma de organizar la información guardada en memoria para poder encontrarla, modificarla o recorrerla con facilidad. Los bits por sí solos no indican qué significan ni cómo se relacionan entre sí: la organización es la que convierte un conjunto de valores sueltos en información utilizable para un programa.

## Antes de empezar

- [[sistema-operativo]]: el entorno integral que carga y supervisa los programas y les ofrece servicios sobre el hardware.

## Explicación

Un programa necesita manejar datos: números, textos, registros de usuarios o elementos de una lista. Esos datos ocupan posiciones en la [[memoria-ram]], la memoria principal volátil del ordenador, pero su disposición en memoria no es indiferente. Acceder a un elemento concreto, insertar uno nuevo o recorrer todos ellos exige un orden y unas reglas de localización. A ese orden lo llamamos estructura de datos.

La distinción esencial es de qué manera se relacionan los elementos. En una estructura secuencial, como el arreglo o vector, los elementos ocupan posiciones contiguas y cada uno se localiza por su índice, es decir, por su número de posición dentro de la secuencia. Esto permite llegar directamente a cualquier elemento, pero añadir o quitar elementos en el medio obliga a desplazar a los demás. En una estructura encadenada, como la lista enlazada, cada elemento guarda, además de su valor, la localización del siguiente; el recorrido se hace entonces paso a paso siguiendo esos enlaces, y las inserciones o eliminaciones no requieren desplazar bloques completos.

Existen también organizaciones jerárquicas, como el árbol, en las que cada elemento puede depender de otros en varios niveles, y clasificaciones por clave, como la tabla de dispersión o tabla hash, que asocia cada valor a una posición calculada a partir de una clave representativa. Todas responden a la misma idea: elegir una organización que haga eficiente la operación más frecuente —buscar, insertar, eliminar o recorrer— asumiendo el coste de las operaciones menos frecuentes.

El sistema operativo ofrece un espacio de memoria ordenado en el que los programas pueden aplicar estas organizaciones, pero no prescribe cuál conviene a cada tarea. Esa elección depende del uso previsto: cuando prima el acceso directo, se prefieren las estructuras secuenciales; cuando priman las inserciones y borrados frecuentes, las encadenadas. La estructura, por tanto, no es un dato más, sino la manera de disponer los datos para que las operaciones del programa sean posibles y eficientes.

## Cómo se conecta con lo anterior y lo siguiente

Desde [[sistema-operativo]] se llega a las estructuras de datos al pasar del entorno que supervisa los programas a la organización interna de la información con la que trabajo. El siguiente paso natural es [[formatos-de-archivos]]: la misma información, una vez organizada en memoria, debe representarse de una forma estable para guardarla en disco y recuperarla después, lo que exige reglas de representación distintas de las de su organización en memoria.

## Límites de esta explicación

Esta nota no trata cómo se representan los datos almacenados de forma persistente, ni la estructura de cada formato concreto; eso se trata en [[formatos-de-archivos]]. Tampoco explica cómo el sistema operativo asigna y protege la memoria de cada programa, tratado en [[memoria-virtual]], ni el detalle de cada tipo de estructura, que queda fuera del alcance de este peldaño.

## Referencias

Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
