---
titulo: "Ventana"
slug: ventana
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-grafica]
conduce_a: []
alias: ["ventana", "window"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Ventana

## Idea central
Una ventana es la región delimitada de la pantalla dentro de la cual una aplicación gráfica presenta su contenido y recibe la interacción de la persona. Es el espacio de trabajo visual que separa el contenido de un programa del resto de la superficie de pantalla.

## Antes de empezar
- [[aplicacion-grafica]]: qué es una aplicación gráfica y por qué su unidad básica es la interfaz gráfica de usuario.

## Explicación
Desde [[aplicacion-grafica]] se sabe que el programa presenta su trabajo con elementos visuales y que la ventana es la pieza central de esa presentación. La ventana (window) es, en lo esencial, un rectángulo de la pantalla con un borde que lo delimita: el marco, es decir, el contorno que marca dónde empieza y dónde termina esa superficie, y que suele incluir una barra de título, es decir, la franja superior dentro del marco donde la aplicación indica su nombre o el documento que está mostrando.

El contenido propio de la aplicación — texto, imagen, datos o controles que permiten actuar sobre ellos — aparece solo dentro de esa región. El sistema gráfico encargado de dibujar en pantalla recorta el contenido en el borde del marco, de modo que lo que queda fuera de la ventana no pertenece a esa aplicación. Así, varias aplicaciones pueden mostrar sus superficies a la vez en la misma pantalla, cada una en su propia región delimitada.

La ventana no es un simple adorno: es el lugar donde la persona ve el resultado de sus acciones y donde dirige su entrada hacia un programa concreto. Sin esa delimitación, no habría un espacio diferenciado para cada aplicación con el que trabajar.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-grafica]] se desciende desde el tipo de aplicación —un programa que se usa mediante una interfaz visual— hasta su unidad básica de presentación: la ventana es el rectángulo delimitado que hace posible que la aplicación muestre su contenido y reciba la interacción. Cómo el sistema muestra, apila, mueve o descarta esas regiones cuando hay varias abiertas queda fuera de esta nota y corresponde al peldaño siguiente sobre gestión de ventanas, sin enlace aquí hasta que exista su nota. Del mismo modo, los elementos de control que pueden aparecer dentro de la ventana, como botones o campos de entrada, se tratan en el peldaño siguiente sobre controles de interfaz, sin enlace aquí hasta que exista su nota.

## Límites de esta explicación
Esta nota no desarrolla cómo el sistema dibuja los bordes, ni cómo se solapan, mueven, dimensionan o cierran las regiones cuando coexisten varias, ni cómo se decide a qué ventana va dirigida cada entrada; eso pertenece al [[software-de-sistema]] a través del [[sistema-operativo]] y, en detalle, a la nota futura de gestión de ventanas. Tampoco trata la estructura interna de cada aplicación ni los caracteres o archivos que muestra, que se tratan en [[formatos-de-archivos]].

## Referencias
- [FTE-0001] *Operating Systems: Three Easy Pieces*, R. H. Arpaci-Dusseau y A. C. Arpaci-Dusseau: contexto general de que el sistema operativo presenta los programas mediante servicios de visualización secuestrados por las aplicaciones.
- [FTE-0002] *Modern Operating Systems*, 4.ª ed., A. S. Tanenbaum (con H. Bos): contexto general de que la ventana es una superficie de presentación de la aplicación cuyos recursos dibuja y arbitra el sistema operativo.
