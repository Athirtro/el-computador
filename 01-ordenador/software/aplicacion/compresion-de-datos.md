---
titulo: "Compresión de datos"
slug: compresion-de-datos
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [codec]
conduce_a: []
alias: ["compresión de datos", "data compression"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Compresión de datos

## Idea central
La compresión de datos (*data compression*) es la transformación de una secuencia de datos en una representación con menos bits, explotando la información redundante que contiene. Es el principio que permite que un [[codec]] guarde audio y vídeo ocupando mucho menos espacio del que ocuparían sin comprimir.

## Antes de empezar
- [[codec]]: qué comprime y descomprime un códec, por qué una pista sin comprimir es demasiado grande para almacenarla y distribuirla, y qué significa comprimir con pérdida o sin pérdida en el caso concreto del audio y del vídeo.

## Explicación
Un dato es, en lo esencial, una secuencia de bits, donde un bit es la unidad mínima de información que puede tomar dos valores. Comprimir consiste en producir otra secuencia de bits, más corta, a partir de la cual sea posible representar lo mismo o algo suficientemente parecido. La compresión solo es posible porque los datos reales rara vez son aleatorios: suelen contener redundancia, es decir, información que se repite, que aparece con mucha frecuencia o que puede deducirse de lo que la rodea. Si los datos fuesen datos aleatorios ya sin repetición ni patrón, no habría forma de representarlos con menos bits sin perder nada, y por eso los datos ya comprimidos o aleatorios apenas pueden comprimirlos otra vez.

La redundancia aparece de varias formas. Una secuencia puede repetir los mismos símbolos muchas veces, de modo que basta guardarla una sola vez junto con la indicación de dónde se repite. También puede seguir un patrón predecible, de modo que en lugar de guardar cada elemento completo basta guardar lo que cambia respecto a los anteriores. Los datos de audio y de vídeo son un ejemplo familiar: muestras de sonido próximas suelen ser parecidas entre sí, e imágenes consecutivas de vídeo también, y el códec aprovecha esa continuidad para guardar diferencias en lugar de fragmentos completos e independientes. La misma idea se aplica a cualquier otro tipo de dato en que haya repetición o regularidad: la compresión ahorra espacio solo en la medida en que el dato contiene redundancia que puede describirse con menos bits que el dato mismo.

Sobre esa base conviene distinguir dos criterios, que ya aparecieron en [[codec]] y que aquí se enuncian de forma general. En la compresión sin pérdida, la descompresión recupera exactamente los datos originales bit a bit; todo el ahorro proviene de eliminar redundancia, sin descartar nada. En la compresión con pérdida, la descompresión recupera una aproximación de los datos originales, porque el compresor ha descartado información que considera menos importante para quien va a percibirlos o usarlos. La diferencia no está en el tipo de dato, sino en el acuerdo sobre qué se exige a la reconstrucción: fidelidad exacta o tamaño menor a cambio de una diferencia aceptable. En ambos casos, comprimir y descomprimir deben aplicar reglas complementarias bien definidas, porque sin conocerlas no es posible pasar de la secuencia guardada a los datos ni al revés.

Esa distinción explica además que comprimir más no sea siempre mejor. Con pérdida se puede ahorrar mucho más, pero se paga con fidelidad. Sin pérdida se conserva todo, pero el ahorro queda limitado por la redundancia que el dato realmente tenga. El compresor que mejores resultados logra no es el que más recorta, sino el que explota mejor la redundancia concreta de cada tipo de dato y, cuando hay pérdida, descarta solo lo que menos importa para su uso previsto.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[codec]] se desciende a este peldaño porque aquella nota define al códec como el programa que aplica la compresión a las pistas de audio y de vídeo, y deja sin desarrollar el principio general que hace posible esa transformación. Esta nota desarrolla ese principio: sin redundancia no hay compresión posible, y con redundancia queda explicar cuánto puede ahorrarse y qué se pierde a cambio según se exija fidelidad exacta o se admita una aproximación. No conduce a ningún otro slug en este momento, porque los algoritmos concretos de compresión, los códecs concretos y los formatos que los empaquetan pertenecen a notas aún no registradas y no pueden enlazarse todavía.

## Límites de esta explicación
Esta nota no trata el contenedor, es decir, el formato de archivo que agrupa las pistas de un mismo contenido y añade índices para localizarlas, ni el detalle de ningún algoritmo o códec concreto. Tampoco mide el ahorro logrado ni desarrolla cuándo conviene exigir fidelidad exacta y cuándo admitir pérdida, cuestiones que quedan para notas futuras dedicadas a cada aspecto y que no se enlazan porque aún no existen como conceptos registrados.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): no respalda ninguna afirmación técnica de esta nota; no contiene el detalle de la compresión de datos ni de la redundancia. Se mantiene en el frontmatter por indicación del contrato, pendiente de que el orquestador lo sustituya por una fuente que sí trate la materia.
- FTE-0002 (Modern Operating Systems, Tanenbaum y Bos): no respalda ninguna afirmación técnica de esta nota; no contiene el detalle de la compresión de datos ni de la redundancia. Se mantiene en el frontmatter por indicación del contrato, pendiente de que el orquestador lo sustituya por una fuente que sí trate la materia.
