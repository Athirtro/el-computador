---
titulo: "Tabla de páginas multinivel"
slug: tabla-de-paginas-multinivel
rama: software
categoria: sistema
nivel: 10
prerequisitos: [tabla-de-paginas]
conduce_a: []
alias: ["tabla de páginas multinivel", "multi-level page table"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Tabla de páginas multinivel

## Idea central
La [[tabla-de-paginas]] de un solo nivel obliga a reservar una entrada por cada página virtual del programa, aunque la mayoría estén vacías. La tabla de páginas multinivel reparte esa lista en varios niveles: una primera tabla no apunta directamente a marcos físicos, sino a otras tablas, y solo las tablas intermedias que el programa necesita de verdad ocupan memoria. Así un espacio virtual enorme deja de exigir una tabla enorme.

## Antes de empezar
- [[tabla-de-paginas]]: correspondencia entre número de página virtual y marco físico, con bits de presencia y protección, y un registro de la CPU que localiza la tabla del programa en ejecución.

## Explicación
El problema que resuelve es de tamaño. Con espacio virtual de $2^{32}$ bytes y páginas de 4 KiB hay un millón de páginas virtuales; una tabla de un solo nivel necesita un millón de entradas, esten o no en uso. Como explica [[paginacion]], la paginación divide todo el espacio virtual en páginas fijas, y la tabla de un solo nivel debe cubrirlas todas por igual, sin poder compartir huecos. En programas que apenas tocan una fracción pequeña de su espacio virtual, casi toda esa reserva se desperdicia.

La idea multinivel consiste en trocear el número de página virtual en varios índices. En el ejemplo más simple, con dos niveles, la parte alta del número de página virtual indexa el primer nivel —el directorio— y la parte baja indexa el segundo nivel. La entrada del primer nivel ya no contiene un marco físico: contiene la dirección de otra tabla de páginas, o marca que esa subtablas todavía no existe. La entrada del segundo nivel sí es la entrada final de la [[tabla-de-paginas]] clásica, con el marco físico y sus bits de presencia y protección.

La consecuencia práctica es que solo se crean las subtablas que un programa usa. Si un programa solo emplea las primeras mil páginas virtuales, basta con el directorio y con las pocas subtablas que esas mil páginas tocan; las demás entradas del directorio quedan vacías, como simples marcas de ausencia. El coste es tiempo: cada traducción de dirección ya no es una sola lectura de la tabla, sino un recorrido por cada nivel, con una lectura por nivel. La estructura que tira de memoria ahorra tiempo. El número de niveles concreto —dos, tres, cuatro— es una decisión de la arquitectura de cada ordenador, no del programa: lo que se mantiene igual es el principio, tablas intermedias que indexan tablas.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[tabla-de-paginas]] se pasa de la correspondencia página virtual a marco en una lista única a la misma correspondencia repartida en niveles jerárquicos: el primer nivel indexa subtablas y la última tabla indexa marcos. El pago es un recorrido más largo por cada traducción, y la siguiente pregunta que plantea es cómo acelerar ese recorrido sin renunciar al ahorro. Ese paso pertenece a un peldaño posterior y no se desarrolla en esta nota.

## Límites de esta explicación
Esta nota no trata el mecanismo que acelera el recorrido por los niveles mediante cachés especiales de traducción; queda fuera de su alcance como peldaño siguiente, en el tema de la TLB. Tampoco explica qué ocurre cuando una entrada indica que la página no está cargada, materia de [[fallo-de-pagina]], ni el modelo alternativo de segmentos, materia de [[segmentacion]], ni el reparto del espacio virtual entre usuario y núcleo, materia de [[memoria-virtual]].

## Referencias
- FTE-0001: tablas de páginas jerárquicas y el ahorro de memoria frente a la tabla de un solo nivel.
- FTE-0002: estructura por niveles de la tabla de páginas y el recorrido de traducción en varios pasos.
