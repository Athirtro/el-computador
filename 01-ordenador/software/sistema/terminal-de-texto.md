---
titulo: "Terminal de texto"
slug: terminal-de-texto
rama: software
categoria: sistema
nivel: 6
prerequisitos: [shell]
conduce_a: []
alias: ["terminal", "consola de texto"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Terminal de texto

## Idea central
La terminal de texto es la pantalla de caracteres sobre la que el usuario escribe y lee las órdenes del [[shell]]. Su importancia está en separar el trabajo de presentar texto de la interpretación de las órdenes: el shell decide qué significa cada línea, y la terminal decide cómo se muestra y cómo se introduce.

## Antes de empezar
- [[shell]]: lee órdenes escritas como texto, las interpreta y solicita al [[sistema-operativo]] su ejecución como [[proceso]].

## Explicación
El shell no pinta directamente las letras en la pantalla ni guarda el estado del teclado. Escribe y lee a través de la terminal, que le ofrece una superficie de texto. En esa superficie, cada posición puede contener un carácter visible, y un cursor marca dónde aparecerá la siguiente entrada o dónde está situada la atención del usuario. Cuando el usuario pulsa teclas, la terminal las muestra tal como se introducen; cuando el shell o el programa que ha puesto en marcha produce texto, la terminal lo coloca en la pantalla y desplaza el contenido hacia arriba si la superficie se llena.

Esta división explica por qué el mismo shell puede trabajar sobre terminales muy diferentes. En origen existían terminales físicas, dispositivos dedicados a mostrar caracteres; hoy lo habitual es un emulador de terminal, un programa que reproduce esa misma superficie de texto dentro de una ventana gráfica. Para el shell, la diferencia es irrelevante: en ambos casos recibe caracteres de entrada y entrega caracteres de salida. La terminal tampoco ejecuta las órdenes ni conoce su sintaxis; simplemente transporta texto en ambas direcciones entre el usuario y el shell, con la ayuda de los servicios del [[sistema-operativo]] que gestionan los dispositivos de entrada y salida.

La terminal mantiene además un estado propio de presentación, distinto del de los procesos. Conserva lo que ya se ha mostrado, permite revisar líneas anteriores y retiene la posición del cursor mientras un programa está en ejecución. Ese estado pertenece a la terminal, no al shell: si el shell termina y vuelve a iniciarse, o si cambia de una terminal a otra, la nueva instancia continúa escribiendo sobre la superficie que le haya sido asignada. Por eso el shell puede considerarse independiente de la terminal concreta que utilice en cada momento.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[shell]] se llegaba a la necesidad de un lugar donde escribir las órdenes y leer sus resultados. Esta nota describe ese lugar: la terminal de texto, que presenta los caracteres y los transmite. No conduce a ninguna nota posterior: es una rama terminal, porque el funcionamiento del shell se entiende sabiendo que existe una superficie de texto, sin necesidad de explicar la sintaxis de sus órdenes ni el detalle interno de los dispositivos físicos.

## Límites de esta explicación
Esta nota no explica la sintaxis de ningún shell ni sus órdenes concretas; eso se trata en [[shell]]. Tampoco explica cómo el [[nucleo-kernel]] gestiona los dispositivos físicos de teclado y pantalla, ni el detalle de los controladores que los manejan. La forma exacta de edición de la línea durante la escritura, las redirecciones de entrada y salida y los guiones concretos quedan fuera de este peldaño.

## Referencias
- FTE-0001: Operating Systems: Three Easy Pieces. Respalda la descripción general de los dispositivos de entrada y salida, incluida la terminal como dispositivo con el que el sistema se comunica con el usuario.
- FTE-0002: Modern Operating Systems, 4th Edition. Respalda la misma descripción general de los dispositivos de entrada y salida y el papel de la terminal como interfaz entre usuario y sistema.
