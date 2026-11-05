---
titulo: "Tabla de páginas"
slug: tabla-de-paginas
rama: software
categoria: sistema
nivel: 9
prerequisitos: [paginacion]
conduce_a: [fallo-de-pagina]
alias: ["tabla de páginas", "page table"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Tabla de páginas

## Idea central
La [[paginacion]] establece que cada página virtual de un programa puede residir en cualquier marco físico, pero esa correspondencia tiene que guardarse en algún lugar. La tabla de páginas (page table) es ese lugar: una estructura del sistema operativo, una por programa, que para cada página virtual indica en qué marco físico está cargada y qué puede hacerse con ella. Sin ella la traducción de direcciones sería imposible.

## Antes de empezar
- [[paginacion]]: cómo se divide el espacio virtual en páginas de tamaño fijo y cómo una dirección virtual se compone de número de página virtual más desplazamiento, que se conserva al traducir.

## Explicación
La tabla de páginas es una lista ordenada por número de página virtual. Su índice de entrada es justamente el número de página virtual: la página 0 del programa ocupa la primera entrada, la página 1 la segunda, y así sucesivamente. En cada entrada se guarda, ante todo, el número del marco físico donde reside esa página en ese momento. Esa pareja —número de página virtual como índice, número de marco como contenido— es la correspondencia completa. Si un programa quiere acceder a la página virtual 5, el sistema lee la entrada 5 de su tabla y obtiene el marco físico correspondiente; a ese número de marco se le añade el desplazamiento y el resultado es la dirección física.

Pero la entrada guarda más que el número de marco, porque no basta con saber dónde está una página: hay que saber si está siquiera en memoria y qué se puede hacer con ella. Por eso cada entrada lleva además unos bits de información auxiliar. El más importante es el bit de presencia —también llamado bit de validez—: si está activo, la página está cargada en el marco indicado; si está inactivo, la página no está en memoria física y su contenido espera fuera, en almacenamiento. Un bit de protección o de permiso indica qué operaciones están permitidas sobre esa página, típicamente lectura, escritura o ejecución, de modo que un intento de escribir en una página marcada como de solo lectura sea detenido. Otros bits habituales, cuya existencia ya aparece en [[paginacion]], marcan si la página ha sido modificada desde que se cargó, lo que avisa al sistema si al liberar el marco debe reescribir su contenido en almacenamiento o puede simplemente descartarlo. Qué bits concretos existen y qué significa cada uno depende de la arquitectura del ordenador, no de cada programa.

La tabla no vive dentro del programa: pertenece al sistema y el ordenador la mantiene localizada sin dudar. La CPU dispone de un registro especial que en todo momento guarda la dirección física del primer elemento de la tabla del programa en ejecución. Cuando el programa necesita traducir una dirección, el hardware usa ese registro base, indexa la tabla con el número de página virtual, lee la entrada y obtiene de ella el número de marco. Al terminar un programa y pasar a otro, el sistema cambia ese registro base a la tabla del nuevo programa, con lo que cada programa ve una tabla distinta aunque dos programas usen los mismos números de página virtual: nada se pisa entre ellos, que es la promesa de la memoria virtual.

El tamaño de la tabla es proporcional al espacio virtual del programa: una entrada por página virtual, aunque la página no esté cargada. Un espacio virtual muy grande genera así una tabla muy grande, ocupando buena parte de la memoria que se suponía libre. Para paginar esa carga se emplean tablas organizadas en varios niveles, donde una primera tabla indexa a otras tablas y estas, a su vez, a las entradas finales. De ese modo solo se crean las tablas intermedias que el programa necesita de verdad.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[paginacion]] se avanza del mecanismo —páginas fijas e intercambio de número de página por número de marco— a la estructura que lo hace posible: una entrada por página virtual, con el marco físico y sus bits de presencia y protección, localizada por un registro base de la CPU y con una tabla propia por programa. El paso siguiente es el caso que esa estructura pone al descubierto: qué ocurre cuando el bit de presencia indica que la página no está cargada y el acceso no puede completarse. Eso se trata en [[fallo-de-pagina]].

## Límites de esta explicación
Esta nota no explica qué ocurre paso a paso cuando la página pedida no está cargada; eso se trata en [[fallo-de-pagina]]. El detalle de cómo se acelera la traducción con cachés dedicadas —la unidad de traducción de direcciones— queda fuera de esta nota y de su alcance, como peldaño posterior. Tampoco explica el modelo alternativo de segmentos, materia de [[segmentacion]], ni cómo se organiza el espacio de un programa concreto, materia de [[espacio-de-usuario]].

## Referencias
- FTE-0001: estructura de la tabla de páginas como lista indexada por número de página virtual y walk de traducción.
- FTE-0002: entrada de página con bits de presencia y protección y una tabla por proceso.
