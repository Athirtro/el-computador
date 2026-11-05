---
titulo: "Dibujado en pantalla"
slug: dibujado-en-pantalla
rama: software
categoria: aplicacion
nivel: 7
prerequisitos: [primitiva-grafica]
conduce_a: []
alias: ["dibujo en pantalla", "renderizado"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Dibujado en pantalla

## Idea central
El dibujado en pantalla es el proceso por el que una aplicación convierte una descripción abstracta de una imagen en los píxeles concretos que se muestran. Sin este paso, una forma descrita como «un rectángulo aquí» no tendría ninguna representación visible.

## Antes de empezar
- La primitiva gráfica: la descripción abstracta de una forma (punto, línea, rectángulo, círculo, polígono) con su posición, tamaño y color, sin decir aún qué píxeles ocupa. Nota aún pendiente, no enlazable (ver nota al orquestador).
- El píxel: el punto de luz más pequeño de la pantalla, al que se asigna un color; la imagen visible es una rejilla de píxeles.
- La pantalla: la superficie donde se muestra esa rejilla de píxeles y que se actualiza de forma periódica.

## Explicación
El dibujado en pantalla es una cadena de pasos que va de la descripción a la luz. El primer paso es decidir qué píxeles toca cada primitiva. Una primitiva geométrica no coincide en general con la rejilla de píxeles: un borde inclinado, por ejemplo, debe traducirse en la serie de píxeles que mejor lo aproxima. Esa traducción de forma continua a píxeles discretos es el núcleo del dibujado: sin ella no hay imagen, solo geometría.

El segundo paso es asignar a cada píxel tocado un valor de color y, en su caso, de opacidad. El color se describe en esta nota solo de forma general: cada píxel recibe una combinación de intensidades que el hardware de pantalla interpreta como un tono visible. Lo que importa para este peldaño no es cómo se produce físicamente el color, sino que el dibujado consiste en escribir, píxel a píxel, qué tono le corresponde a cada posición de la rejilla.

El tercer paso es resolver los solapamientos. Cuando dos primitivas ocupan el mismo píxel, o cuando una ventana se superpone a otra, un solo píxel no puede tener dos colores a la vez. El proceso de dibujado debe decidir qué primitiva queda delante y escribir solo su color en ese píxel, descartando el de la que queda detrás. Ese orden de pintado decide qué se ve y qué queda oculto.

El cuarto paso es componer la imagen completa en una zona de memoria destinada a ello, el búfer de imagen: el espacio donde se van escribiendo los píxeles de una imagen antes de mostrarla. Componer en memoria permite construir la imagen entera sin mostrar a la persona estados intermedios a medio dibujar. Una vez compuesta, esa imagen se transfiere a la pantalla, que la presenta en cada ciclo de refresco. Si el contenido cambia, se repite el ciclo: se vuelven a escribir los píxeles afectados en el búfer y se vuelve a mostrar la imagen resultante.

## Cómo se conecta con lo anterior y lo siguiente
Desde la primitiva gráfica, que describe qué formas deben aparecer y dónde, se desciende a cómo esas formas llegan a verse: el dibujado en pantalla traduce cada descripción en píxeles, resuelve sus solapamientos y compone la imagen que la pantalla muestra. Esta nota no abre un peldaño siguiente en la cola: es una rama terminal que cierra el recorrido desde la interfaz visible hasta la imagen compuesta.

## Límites de esta explicación
Esta nota no desarrolla cómo se calcula cada primitiva concreta —por ejemplo, qué píxeles forman una línea o un círculo—, porque ese detalle pertenece a la primitiva gráfica, nota aún pendiente y no enlazable. Tampoco trata cómo el hardware produce físicamente la luz de cada píxel ni cómo el sistema operativo entrega la imagen a la pantalla, temas que pertenecen al software de sistema y al hardware, aún sin nota canónica.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre búfer de imagen, rasterización o composición de píxeles.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum y Bos): respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre dibujado en pantalla.
