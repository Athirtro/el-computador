---
titulo: "Software"
slug: software
rama: software
categoria: ""
nivel: 1
prerequisitos: [ordenador]
conduce_a: [software-de-sistema, software-de-aplicacion, software-de-programacion, software-malicioso]
alias: ["software", "programa"]
estado: borrador
fuentes: []
---

# Software

## Idea central
El software es el componente intangible del ordenador: las instrucciones y los datos que indican al hardware qué debe hacer. Sin software, el hardware no tiene propósito; sin hardware, el software no tiene cuerpo sobre el que ejecutarse.

## Antes de empezar
- [[ordenador]]: qué es el ordenador y por qué se distingue entre lo físico y lo intangible.
- [[hardware]]: los componentes físicos que el software controla.

## Explicación
El hardware —procesadores, memorias, dispositivos y circuitos— solo cambia de estado cuando recibe instrucciones. El software es ese conjunto de instrucciones y datos. No se puede tocar, pero produce efectos reales: mueve información de un lugar a otro, realiza cálculos y presenta resultados en formas comprensibles para otras personas o sistemas. La distinción no es entre "real" e "irreal", sino entre lo físico, que lo forma [[hardware]], y lo lógico, que lo forma el software.

El ejemplo más visible es el [[sistema-operativo]], el [[software-de-sistema]] que permite interactuar con el ordenador. En su centro se encuentra el [[nucleo-kernel]] (kernel), el componente de software más cercano al hardware: coordina sus recursos y decide qué ocurre con cada petición. Esta nota no desarrolla cómo lo hace; solo establece que existe un software cuya función es gestionar el hardware mismo. El detalle se trata en [[software-de-sistema]], [[sistema-operativo]] y [[nucleo-kernel]].

Otro ejemplo, menos inmediato, es un programa escrito por una persona. Un programa expresa una tarea en un [[lenguajes-de-programacion]] —un lenguaje formal con el que se describen operaciones— y el ordenador la ejecuta. Considérese la operación matemática factorial: multiplicar un número por todos los enteros menores que él hasta llegar a uno. Describirla en un lenguaje de programación parece sencillo, pero plantea un enigma de fondo: cómo pasa el hardware de ejecutar instrucciones elementales a producir el resultado de una operación abstracta. Explicar esa cadena —cómo un lenguaje se traduce hasta el código que el procesador evalúa— es tarea de la programación y de los niveles inferiores, no de esta nota. Se desarrolla en [[software-de-programacion]] y [[lenguajes-de-programacion]].

Tampoco todo software es un programa que se ejecuta en un momento dado. Una imagen, un documento o una página web son información que solo cobra sentido mediante software que lo interprete: son [[estructuras-de-datos]] y [[formatos-de-archivos]] que necesitan un visor, un navegador o un reproductor para mostrarse. Decir que un archivo "es" software es confuso; lo correcto es decir que está organizado según una estructura y un formato, y que requiere software para usarse.

Por su función, el consenso clasifica el software en cuatro grupos. El [[software-de-sistema]] gestiona y controla el hardware; lo integran el sistema operativo, el núcleo, el firmware y los controladores. El [[software-de-aplicacion]] está dirigido a tareas concretas del usuario, como editar texto, navegar o reproducir contenido. El [[software-de-programacion]] abarca las herramientas que permiten crear otros programas, desde los lenguajes hasta compiladores e intérpretes. El [[software-malicioso]] reúne los programas diseñados para dañar, espiar o aprovechar errores del sistema, y se trata desde el punto de vista técnico y defensivo. Esta clasificación sirve para ordenar el libro, no para encerrar cada programa en una sola caja: un mismo programa puede combinar funciones de más de un grupo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[ordenador]] se llega al software del mismo modo que se llega al hardware: el ordenador tiene dos caras, una física y una lógica. Esta nota aporta la segunda y prepara el recorrido. Desde aquí, el paso natural es el [[software-de-sistema]] y el [[sistema-operativo]], para seguir hacia el [[nucleo-kernel]] y la gestión de recursos. Las otras tres ramas —[[software-de-aplicacion]] para el uso cotidiano, [[software-de-programacion]] para crear software y [[software-malicioso]] para comprender sus abusos— parten de la misma distinción inicial.

## Límites de esta explicación
Esta nota no explica cómo el sistema operativo gestiona procesos y memoria, ni cómo un lenguaje de programación se traduce en [[compilacion]], [[lenguaje-ensamblador]] y [[codigo-maquina]]. Tampoco detalla los tipos de aplicación ni las técnicas del software malicioso. Cada uno de esos temas tiene su nota canónica.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
