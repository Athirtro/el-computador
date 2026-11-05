---
titulo: "Software de programación"
slug: software-de-programacion
rama: software
categoria: programacion
nivel: 2
prerequisitos: [software]
conduce_a: [lenguajes-de-programacion, compilador, interprete]
alias: ["software de programación", "herramientas"]
estado: borrador
fuentes: []
---

# Software de programación

## Idea central
El software de programación es el conjunto de herramientas que permite escribir, traducir y ejecutar otros programas. Es el puente entre la intención de la persona que programa en un [[lenguajes-de-programacion]] y las instrucciones que el hardware puede ejecutar.

## Antes de empezar
- [[software]]: qué es el software como componente intangible del ordenador y su clasificación en cuatro grupos.
- [[lenguajes-de-programacion]]: qué es un lenguaje de programación como medio para describir operaciones; su detalle completo se trata en su nota canónica.

## Explicación
Escribir un programa exige algo más que pensar la tarea: hay que expresarla en un [[lenguajes-de-programacion]], un sistema formal con vocabulario y reglas de composición propio. Ese texto fuente no lo entiende directamente el procesador, que solo ejecuta [[codigo-maquina]]. Entre ambos extremos hacen falta herramientas que traduzcan, comprueben y ejecuten, y ese es el territorio del software de programación.

En el panorama conviven tres familias principales. La primera son los propios lenguajes, con Python como ejemplo próximo: permiten describir con relativa cercanía al pensamiento humano operaciones como calcular un factorial o recorrer una lista. La segunda familia son los traductores. El [[compilador]] traduce el texto fuente completo a un lenguaje de nivel inferior, normalmente [[lenguaje-ensamblador]] o directamente código máquina, antes de que el programa se ejecute; el [[interprete]], en cambio, ejecuta el programa directamente, instrucción a instrucción, sin producir un ejecutable separado por adelantado. La diferencia no es solo de rendimiento: condiciona cuándo se detectan los errores, si durante la traducción o durante la ejecución, y qué artefacto queda sobre el disco.

La tercera familia es el entorno que reúne las anteriores para trabajar sobre ellas: el entorno de desarrollo integrado (IDE, *integrated development environment*), que combina editor de texto, comprobación de errores, ejecución y depuración en un solo programa. Su papel en esta nota es solo panorámico: facilita la escritura y el ajuste del programa, pero no sustituye ni al lenguaje ni a los traductores, y su funcionamiento interno no forma parte de este peldaño.

El software de programación, en conjunto, no ejecuta por sí mismo la tarea final del programa creado, como editar un documento o gestionar memoria; produce o ejecuta el programa que lo hará. Por eso se distingue del [[software-de-sistema]], que gestiona el hardware, y del [[software-de-aplicacion]], que resuelve tareas del usuario.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software]] se distingue el componente intangible y se separan sus cuatro grupos; esta nota entra en el tercero, el que sirve para crear software nuevo. El paso siguiente es el detalle de cada pieza: [[lenguajes-de-programacion]] desarrolla cómo se expresa la tarea, [[compilador]] y [[interprete]] explican cómo se traduce o se ejecuta ese texto, y [[compilacion]] describe el proceso completo hacia el [[lenguaje-ensamblador]] y el [[codigo-maquina]].

## Límites de esta explicación
Esta nota no desarrolla cómo funciona la [[compilacion]] paso a paso, ni el funcionamiento interno del [[compilador]] o del [[interprete]], ni las fases del [[enlazadores]] y los [[cargadores]]; cada uno tiene su nota canónica. Tampoco entra en el diseño concreto de los entornos de desarrollo integrados ni en lenguajes concretos.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
