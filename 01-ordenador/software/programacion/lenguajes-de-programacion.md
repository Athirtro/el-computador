---
titulo: "Lenguajes de programación"
slug: lenguajes-de-programacion
rama: software
categoria: programacion
nivel: 3
prerequisitos: [software-de-programacion]
conduce_a: [lenguajes-compilados, lenguajes-interpretados]
alias: ["lenguajes de programación", "programming languages"]
estado: borrador
fuentes: []
---

# Lenguajes de programación

## Idea central
Un lenguaje de programación es un sistema formal para describir las operaciones que debe realizar un ordenador, con un vocabulario y unas reglas de composición que permiten expresarlas de forma precisa. Su sentido práctico es alejar la escritura del programa de las instrucciones concretas que la máquina entiende, sin perder la capacidad de especificar el cálculo.

## Antes de empezar
- [[software-de-programacion]]: qué es el software encargado de escribir, traducir y ejecutar programas, y dónde encaja en él el lenguaje frente a las herramientas.

## Explicación
El procesador no entiende las palabras de un lenguaje de programación. Solo ejecuta [[codigo-maquina]], es decir, patrones de bits que corresponden directamente a las instrucciones de su [[conjunto-de-instrucciones-isa]]. Entre la intención de quien programa y ese nivel hay un salto enorme. Un lenguaje de alto nivel reduce ese salto: permite decir «ordena esta lista» o «calcula este factorial» con construcciones propias, sin tener que enumerar una a una las operaciones elementales que la máquina llevará a cabo, como ocurre en [[lenguaje-ensamblador]].

Todo lenguaje se define por dos cosas. La primera es su sintaxis, el conjunto de formas correctas de escribirlo, análogo a la gramática de una lengua natural. La segunda es su semántica, el significado que se asigna a cada forma correcta, lo que la ejecución de un texto bien escrito debe producir. Un error de sintaxis impide que el texto sea siquiera reconocido como programa válido; un programa sintácticamente correcto puede, aun así, significar algo distinto de lo que su autor pretendía.

La distancia respecto a la máquina es lo que hace «alto» a un lenguaje de alto nivel. Python es un buen ejemplo de esa distancia: su escritura es breve y cercana al pensamiento, y abstrae por defecto de detalles como la dirección exacta de la memoria, de modo que el mismo programa descripción puede ejecutarse en máquinas distintas con tal de que exista la herramienta que lo interprete o traduzca. C ofrece un contraste útil dentro del mismo peldaño. También es un lenguaje de alto nivel, porque no exige escribir en mnemotécnicos de ensamblador ni en bits, pero deja a quien programa un control mucho más directo sobre recursos como la memoria y conserva una correspondencia más visible entre lo escrito y lo que la máquina hará. La diferencia entre Python y C no es aquí de qué familia de traducción pertenece cada uno, sino de cuánta abstracción respecto al hardware impone el propio lenguaje.

Comparten, en cambio, la consecuencia esencial de ser de alto nivel: el texto fuente que se escribe no es ejecutable directamente por el procesador, sino una descripción que debe ser traducida o ejecutada por un programa intermedio. Por eso el lenguaje no funciona solo. Necesita el software de programación descrito en [[software-de-programacion]], y estudiar la forma concreta de esa traducción es el paso siguiente.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-programacion]] se mostró el panorama de herramientas que hacen posible escribir y ejecutar software. Esta nota entra en la primera de esas piezas, el lenguaje como medio de expresión, y lo define como sistema formal con sintaxis y semántica, situado muy por encima del [[codigo-maquina]] que la máquina sí entiende. El paso siguiente es clasificar cómo se traslada ese texto hasta la ejecución. En [[lenguajes-compilados]] y [[lenguajes-interpretados]] se desarrollará, cada uno por separado, si la traducción se hace completa antes de ejecutar el programa o si se ejecuta a medida que se lee.

## Límites de esta explicación
Esta nota no desarrolla el detalle de la [[lenguajes-compilados]] ni de la [[lenguajes-interpretados]]: cuándo se detectan los errores, qué archivo queda sobre el disco y cómo intervienen el [[compilador]] y el [[interprete]] se tratan en sus notas canónicas. Tampoco entra en el paso a paso de la [[compilacion]] hacia [[lenguaje-ensamblador]] y [[codigo-maquina]], ni en la sintaxis concreta de ningún lenguaje concreto.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
