---
titulo: "Bit de presencia"
slug: bit-de-presencia
rama: software
categoria: sistema
nivel: 9
prerequisitos: [entrada-de-pagina]
conduce_a: []
alias: ["bit de presencia", "bit de validez", "present bit"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Bit de presencia

## Idea central
El bit de presencia es un único bit dentro de cada [[entrada-de-pagina]] que indica si la página virtual correspondiente está cargada en memoria física o si su contenido sigue en almacenamiento. Es la diferencia entre una traducción de direcciones que puede completarse y una que debe detenerse para traer la página antes de continuar.

## Antes de empezar
- [[entrada-de-pagina]]: qué guarda cada entrada de la [[tabla-de-paginas]] —el número de marco físico y los bits de información auxiliar— y por qué el número de marco solo tiene sentido si la página está presente.

## Explicación
En la [[paginacion]], cada página virtual de un programa puede residir en cualquier marco físico, y la [[tabla-de-paginas]] guarda esa correspondencia. Pero esa correspondencia es condicional: solo describe dónde está la página cuando la página está. Un programa puede tener asignadas muchas más páginas virtuales de las que caben en memoria física en un momento dado, porque [[memoria-virtual]] permite que el resto de su contenido resida en almacenamiento hasta que haga falta. La entrada de página existe igualmente para esas páginas no cargadas, y necesita una forma de distinguir ambos casos sin perder el resto de la información. Esa forma es el bit de presencia, también llamado bit de validez.

Cuando el bit está activo, la página está cargada en el marco físico indicado en la misma entrada. La traducción puede completarse: se lee el número de marco, se le suma el desplazamiento dentro de la página y se obtiene la dirección física. Cuando el bit está inactivo, la página no está en memoria física y el número de marco de la entrada no debe usarse, porque no señala ningún contenido válido. La dirección virtual sigue siendo legítima —el programa la ha asignado y el sistema la reconoce—, pero su contenido espera fuera, en almacenamiento, hasta que el sistema lo traiga a un marco libre y active el bit.

Esa distinción es lo que convierte un acceso a una página ausente en un evento controlado en lugar de un error silencioso. Si el hardware ignorara el bit y tradujera igualmente, accedería a un marco que contiene datos de otra página u otra cosa, con resultados impredecibles. En cambio, con el bit inactivo el hardware puede detener el acceso de forma ordenada y entregar el control al sistema operativo, que es quien decide dónde debe ir la página y cómo se actualiza la entrada. La presencia es, por tanto, un permiso de validez sobre el resto de la entrada: sin ella, el número de marco carece de significado.

El bit de presencia no es un dato del programa sino del estado de la página, y lo mantiene el sistema operativo, no el programa. El programa no puede activarlo ni desactivarlo directamente: solo el sistema, al cargar la página en un marco o al retirarla de él, puede cambiar su valor. Así, el bit funciona como una señal entre el hardware, que lo lee en cada traducción, y el sistema, que lo escribe cuando el estado de la página cambia. Conviene no confundirlo con los demás bits de la entrada, como el de protección, que indica qué operaciones están permitidas sobre la página, o el que marca si ha sido modificada desde que se cargó. El bit de presencia responde solo a una pregunta: ¿está la página en memoria física?

## Cómo se conecta con lo anterior y lo siguiente
Desde [[entrada-de-pagina]] se pasa de la estructura general de la entrada —número de marco más bits auxiliares— a un único bit cuyo significado hay que entender antes de confiar en cualquier otra cosa de la entrada: si la página no está presente, el número de marco no señala nada válido. El caso que este bit pone al descubierto, qué ocurre paso a paso cuando el bit está inactivo y el acceso no puede completarse sin cargar la página, se trata en [[fallo-de-pagina]].

## Límites de esta explicación
Esta nota no explica el procedimiento completo que sigue el sistema cuando la página no está cargada; eso se trata en [[fallo-de-pagina]]. El detalle de cómo se acelera la traducción evitando consultar la tabla en cada acceso queda fuera, como peldaño posterior. Tampoco explica los demás bits de la entrada, como los de protección, ni el modelo alternativo de segmentos, materia de [[segmentacion]].

## Referencias
- FTE-0001: distinción entre página presente en memoria y página residente en almacenamiento mediante el bit de presencia de la entrada de página.
- FTE-0002: bit de presencia/validez como condición para que el número de marco de la entrada sea utilizable en la traducción.
