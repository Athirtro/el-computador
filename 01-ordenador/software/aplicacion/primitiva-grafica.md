---
titulo: "Primitiva gráfica"
slug: primitiva-grafica
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [interfaz-grafica-de-usuario]
conduce_a: [dibuixado-en-pantalla]
alias: ["primitiva gráfica", "graphic primitive"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Primitiva gráfica

## Idea central
Una primitiva gráfica es el elemento dibujable más básico de una interfaz: una forma geométrica mínima descrita por unos pocos parámetros (su posición, su tamaño, su color) de la que puede construirse todo lo que se ve en pantalla. Sirve para separar lo que se quiere mostrar —la forma— de cómo se muestra —los píxeles concretos—.

## Antes de empezar
- [[interfaz-grafica-de-usuario]]: qué es el conjunto de elementos visuales con los que una aplicación gráfica se presenta y se opera.

## Explicación
En [[interfaz-grafica-de-usuario]] la interfaz aparecía como un conjunto de elementos con función —botones, campos, menús, áreas de contenido—. Esos elementos no se dibujan de una sola pieza: se componen a partir de unas pocas formas mínimas. Una primitiva gráfica es exactamente eso: la forma mínima que sirve de materia para construir la presentación.

Conviene fijar dos términos, porque son la base de todo lo que sigue. Un píxel —*pixel*, del inglés *picture element*— es el punto más pequeño de luz que puede encenderse en la pantalla; es la unidad física del dibujo. Una descripción geométrica, en cambio, es la definición de una forma por sus medidas: «un segmento que une estos dos puntos con este grosor y este color», sin decir todavía qué píxeles concretos habrán de encenderse.

Una primitiva gráfica conecta esos dos niveles. Formalmente, es una instrucción del tipo «dibuja esta forma con estos parámetros»: unas coordenadas que fijan su posición, unas medidas que fijan su extensión y unos atributos de presentación, como el color del trazo o del relleno. El catálogo habitual de primitivas es breve: el punto, la línea recta, el rectángulo, la elipse y el círculo, el polígono —una figura de lados rectos— y el texto dibujado como contorno. Con solo estas piezas se puede construir cualquier símbolo visible: un icono es un conjunto de rectángulos y elipses, un gráfico es un conjunto de líneas y polígonos, y hasta el marco de una [[ventana]] es, en su fondo, un gran rectángulo.

La distinción que esta nota debe dejar clara es la que separa la primitiva del [[widget]]. El widget es la primitiva ya vestida de función: un rectángulo que además, al activarlo, ordena una acción, o un campo de texto con su borde. La primitiva es solo la forma dibujable, sin comportamiento de interacción; no sabe si la han pulsado ni qué significa. La aplicación describe qué formas quiere, y queda para otro peldaño decidir cómo esas descripciones se convierten en píxeles encendidos en la pantalla.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[interfaz-grafica-de-usuario]], donde la interfaz era el conjunto de elementos visibles y operables, esta nota baja un peldaño: esos elementos se construyen con primitivas gráficas, las formas mínimas y paramétricas de las que todo dibujo puede componerse. El siguiente peldaño es el dibujado en pantalla, donde se explica cómo una descripción geométrica de primitivas se transforma en los píxeles concretos que, encendidos en su posición, forman la imagen visible.

## Límites de esta explicación
Esta nota no trata los widgets ni su comportamiento de interacción; los widgets se tratan en [[widget]]. Tampoco trata el procedimiento por el que una descripción geométrica se convierte en píxeles —el dibujado en pantalla— ni las bibliotecas concretas de gráficos, que pertenecen a otro nivel. Las figuras complejas, como los gráficos o las imágenes, se construyen combinando primitivas y quedan fuera del alcance de esta nota.

## Referencias
- [FTE-0001]: *Operating Systems: Three Easy Pieces*, Arpaci-Dusseau y Arpaci-Dusseau. Respalda el papel del sistema operativo como proveedor de los servicios que la aplicación utiliza para presentarse en pantalla y recibir las acciones del usuario sobre lo visible.
- [FTE-0002]: *Modern Operating Systems*, 4ª ed., Tanenbaum y Bos. Respalda la distinción entre el programa de aplicación y los servicios del sistema que le permiten operar sobre los recursos del ordenador.
