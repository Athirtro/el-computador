---
titulo: "Procesador de texto"
slug: procesador-de-texto
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-grafica]
conduce_a: []
alias: ["procesador de texto", "editor de documentos"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Procesador de texto

## Idea central
Un procesador de texto es una aplicación gráfica especializada en crear y editar documentos donde el contenido va unido a su presentación, de modo que lo que se ve en pantalla es lo que se obtiene en la impresión. Sin esta unión, el texto sería solo una cadena de caracteres que leerá la computadora; con ella, la persona decide cómo se ordena, se presenta y se entrega el documento.

## Antes de empezar
- [[aplicacion-grafica]]: qué es una aplicación gráfica y cómo se presenta el trabajo en una ventana.

## Explicación
Desde [[aplicacion-grafica]] se sabe que el trabajo se realiza en una ventana y que la aplicación se apoya en el [[software-de-sistema]] para acceder a los recursos del ordenador, sin ocuparse de los detalles físicos de esas operaciones. El procesador de texto es un peldaño más concreto de esa familia: su tarea es elaborar documentos, no cualquier trabajo visual.

Un documento queda representado dentro del programa como texto acompañado de formato, es decir, de instrucciones sobre cómo debe presentarse cada parte. Esas instrucciones indican qué pasajes se destacan en negrita o en cursiva, qué tamaño y qué familia tipográfica usan, dónde empiezan y terminan los párrafos, cómo se alinean los títulos y las listas y cómo se distribuye el contenido en páginas. La aplicación aplica esas instrucciones al dibujar el documento en la ventana, de forma que la persona comprueba al instante el efecto de cada cambio que realiza.

Esa capacidad de componer el documento distingue al procesador de texto de un editor de texto plano. En un editor plano solo se almacenan caracteres y el efecto visual es el mismo para todo el texto, porque todo está en la misma tipografía como si se escribiera en una máquina de escribir. En un procesador de texto cada fragmento lleva sus propias propiedades de presentación y, además, pueden aplicarse estilos, es decir, conjuntos de propiedades definidos una vez y reutilizados en todo el documento, para que los títulos y el cuerpo atengan a una misma forma. La organización en páginas, márgenes y encabezados forma parte de ese mismo trabajo de presentación, pensado para su salida en papel o en pantalla.

Al terminar, el documento se guarda como un archivo mediante los servicios del [[sistema-de-archivos]], según los [[formatos-de-archivos]] que el programa soporta, y se recupera después con su formato intacto. La aplicación no gestionar directamente el almacenamiento físico: lo hace a través del sistema operativo, del mismo modo que para mostrar los caracteres y para preparar su impresión. El procesador de texto sigue siendo, en esencia, una aplicación en el sentido de [[software-de-aplicacion]]: existe para que la persona realice una tarea concreta, en este caso, producir documentos con presentación cuidada.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-grafica]], que describe la presentación visual mediante ventanas, se desciende a un tipo definido por su tarea: el procesador de texto es una aplicación gráfica cuyo trabajo es componer documentos añadiendo formato a un texto. Esta nota abre una rama convergente dentro de las aplicaciones gráficas, sin dar paso a un nuevo peldaño lineal en el libro.

## Límites de esta explicación
Esta nota no desarrolla el detalle de cada tipo de formato concreto ni los comandos de formato disponibles, porque eso pertenece al estudio de cada programa concreto; aquí solo se trata su función general dentro del documento. Tampoco trata cómo el sistema dibuja la fuente tipográfica en pantalla o gestiona la impresora, que corresponden al [[software-de-sistema]], ni la estructura interna de los archivos del documento, que se trata en [[formatos-de-archivos]].

## Referencias
- FTE-0001: respaldo general de la afirmación de que la aplicación se apoya en los servicios del sistema operativo para archivos y salida.
- FTE-0002: respaldo general de la misma afirmación sobre la dependencia de la aplicación respecto a los servicios del sistema.
