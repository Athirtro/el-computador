---
titulo: "Sustitución de páginas"
slug: sustitucion-de-paginas
rama: software
categoria: sistema
nivel: 10
prerequisitos: [fallo-de-pagina]
conduce_a: []
alias: ["sustitución de páginas", "page replacement"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Sustitución de páginas

## Idea central
La sustitución de páginas es la decisión de qué página residente se aparta cuando un [[fallo-de-pagina]] necesita un marco y no hay ninguno libre. Es el peldaño que faltaba entre traer una página y qué hacer si para traerla hay que desalojar a otra.

## Antes de empezar
- [[fallo-de-pagina]]: qué ocurre cuando un programa accede a una página virtual no cargada, el núcleo la trae a un marco y la traducción se repite, o bien el acceso es inválido y se rechaza.

## Explicación
El [[fallo-de-pagina]] describía dos caminos: si hay un marco libre, el núcleo lo usa; si no los hay, se aparta una página residente y se ocupa su marco con la página demandada. Esta nota trata solo de esa elección, es decir, de cómo se escoge la página víctima que se aparta.

Antes de apartar una página, el sistema debe decidir qué hacer con su contenido. Si la página víctima no ha sido modificada desde que se cargó, su copia en memoria basta como referencia y el contenido original sigue guardado en el almacenamiento asociado a la [[memoria-virtual]]. En ese caso basta descartarla: si el programa la vuelve a pedir, se traerá de nuevo. Si la página víctima sí ha sido modificada, descartarla perdería esos cambios, y debe escribirse primero en ese almacenamiento para que no se pierdan. Esta diferencia entre página limpia y página modificada condiciona el coste de desalojar cada candidata, porque desalojar una página modificada obliga a una escritura adicional que no hace falta con una limpia.

Dado ese coste, la elección de la víctima persigue un objetivo: que la página desalojada sea la que menos se vaya a necesitar en un futuro próximo, de modo que lo antes posible no se produzca otro fallo para traerla de vuelta. En la práctica no se conoce el futuro, y las políticas de sustitución son aproximaciones a ese objetivo con información distinta.

La política óptima elige siempre la página que se usará más tarde. Como requiere conocer por adelantado el orden en que el programa pedirá sus páginas, no puede aplicarse, y sirve solo como referencia teórica: cualquier política real fallará al menos tantas veces como ella.

La política de sustitución FIFO (first in, first out) aparta la página que lleve más tiempo cargada en memoria, sin tener en cuenta si se ha usado recientemente. Su ventaja es su sencillez, pero puede apartar páginas que se siguen usando con frecuencia.

La política de sustitución LRU (least recently used) aparta la página que menos recientemente se haya usado, porque es la que, por el patrón habitual de acceso de los programas, tardará más en volver a pedirse. En los sistemas reales no se registra la hora exacta de cada uso, y se aproxima mediante un bit de referencia que el hardware marca cada vez que una página se toca: el sistema considera usada toda página cuyo bit esté activo y lo limpia periódicamente.

Existe también la sustitución aleatoria, que aparta una página elegida al azar. No sigue ningún patrón de uso, pero su sencillez la convierte en una base de comparación y, en algunos casos, su aleatoriedad evita que una elección sistemática aparten justamente las páginas que se están usando.

Ninguna de estas políticas es siempre la mejor. La elección de una u otra cambia cuántos fallos de página se producen, y un número excesivo de fallos puede verse agravado si el sistema se ve obligado a apartar páginas que el programa está usando en ese instante. El algoritmo concreto que aplica cada sistema dentro de estas políticas es un peldaño posterior.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[fallo-de-pagina]] se pasa del fallo genérico al caso concreto sin marcos libres. Allí quedaba pendiente qué página se aparta; esta nota explica que la elección busca minimizar los fallos futuros, que apartar una página modificada cuesta más que apartar una limpia, y que las políticas óptima, FIFO, LRU y aleatoria son las aproximaciones habituales a ese objetivo.

## Límites de esta explicación
Esta nota no explica cómo se organiza en la práctica el registro de qué páginas están cargadas ni qué bits acompañan a cada página; eso se trata en el detalle de la [[tabla-de-paginas]]. Tampoco explica cómo se lee ni se escribe el contenido de una página en el dispositivo de almacenamiento, ni los mecanismos que aceleran la traducción cuando la página ya está cargada. Ambos quedan como peldaños posteriores al criterio del orquestador.

## Referencias
- FTE-0001: problema de la sustitución de páginas y políticas óptima, FIFO y LRU como aproximaciones a la elección de la víctima.
- FTE-0002: sustitución de páginas, distinción entre páginas modificadas que deben escribirse y limpias que pueden descartarse, y coste en fallos.
