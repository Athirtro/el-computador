---
titulo: "Entrada de página"
slug: entrada-de-pagina
rama: software
categoria: sistema
nivel: 9
prerequisitos: [tabla-de-paginas]
conduce_a: [bit-de-presencia]
alias: ["entrada de página", "page table entry", "page table element"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Entrada de página

## Idea central
Cada fila de la [[tabla-de-paginas]] es una entrada de página (page table entry): un registro de tamaño fijo que para una página virtual concreta guarda dónde está en la memoria física y qué significa ese dato. Sin examinar su estructura interna —número de marco y bits auxiliares— la correspondencia virtual-física queda incompleta.

## Antes de empezar
- [[tabla-de-paginas]]: la tabla es una lista indexada por número de página virtual, una por programa, localizada por un registro base de la CPU.

## Explicación
El campo principal de la entrada es el número de marco físico (frame number). Ese número no es una dirección completa, sino el índice del marco dentro de la memoria física, por lo que su tamaño en bits depende de cuántos marcos existen. Si el tamaño de página es $P$ y la memoria física es $M$, el número de marcos es $M/P$, y los bits necesarios para contarlos son $\log_2(M/P)$. Con páginas de $4$ KiB y una memoria física de $32$ GiB, por ejemplo, hay $2^{22}$ marcos y bastan $22$ bits para numerarlos; el desplazamiento dentro de la página se añade después, fuera de la entrada, como se vio en [[paginacion]].

Junto al número de marco, la entrada lleva bits de estado. El primero en importancia es el bit de presencia (present bit), que indica si la página está cargada en el marco indicado; su detalle pertenece a [[bit-de-presencia]]. Los demás bits describen el uso de la página: bits de protección o permiso, que delimitan lectura, escritura y ejecución; un bit de modificación (dirty bit), que avisa si el contenido cambió desde la carga y debe reescribirse al liberar el marco; y un bit de acceso o referencia, que registra si la página fue usada recientemente y sirve para decidir qué marco sustituir. La arquitectura concreta del ordenador fija qué bits existen y en qué posiciones, pero la idea es estable: la entrada combina localización y permiso en un único registro legible de una vez por el hardware.

El diseño tiene una consecuencia práctica. Como cada entrada debe tener el mismo tamaño para que la tabla sea indexable, el número de marco ocupa siempre los mismos bits, aunque la página no esté cargada, y los bits auxiliares se reservan siempre. Una tabla grande no es solo una lista larga: cada elemento tiene un coste fijo en el que se paga espacio por capacidad de descripción, no por uso real. Las tablas de varios niveles de [[tabla-de-paginas-multinivel]] reducen ese coste creando entradas intermedias que apuntan a otras tablas, pero la entrada final conserva esta misma estructura.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[tabla-de-paginas]] se pasa del conjunto ordenado de correspondencias a la anatomía de una correspondencia: número de marco de $\log_2(M/P)$ bits más bit de presencia, protección, modificación y acceso. El siguiente paso es interpretar el bit que decide si la traducción puede completarse, lo que se trata en [[bit-de-presencia]], y de ahí a qué ocurre cuando está inactivo en [[fallo-de-pagina]].

## Límites de esta explicación
Esta nota no explica el mecanismo por el que el bit de presencia se pone a cero o a uno, materia de [[bit-de-presencia]], ni su consecuencia cuando la página no está cargada, materia de [[fallo-de-pagina]]. Tampoco trata de la aceleración de la traducción con cachés dedicadas, materia de [[tlb]], ni de la organización de la tabla en varios niveles, materia de [[tabla-de-paginas-multinivel]].

## Referencias
- FTE-0001: estructura de la entrada de página como registro con número de marco indexable por página virtual.
- FTE-0002: bits de presencia y protección por entrada y una tabla por proceso.
