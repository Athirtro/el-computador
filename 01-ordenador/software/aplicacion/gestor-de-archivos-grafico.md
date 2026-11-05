---
titulo: "Gestor de archivos gráfico"
slug: gestor-de-archivos-grafico
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-grafica]
conduce_a: []
alias: ["gestor de archivos gráfico", "explorador de archivos", "file manager"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Gestor de archivos gráfico

## Idea central
El gestor de archivos gráfico es una aplicación gráfica especializada en mostrar y organizar los archivos y las carpetas del ordenador. Permite recorrer la jerarquía de carpetas, ver el contenido de cada una y realizar las operaciones cotidianas sobre los elementos, sin que la persona tenga que escribir órdenes de texto.

## Antes de empezar
- [[aplicacion-grafica]]: qué es una aplicación gráfica, qué es una ventana y cómo se interactúa señalando elementos visuales.

## Explicación
El gestor de archivos gráfico es un caso concreto de [[aplicacion-grafica]]: una aplicación que realiza su tarea en una ventana con menús, botones e iconos, y no con órdenes escritas. Su tarea concreta es la organización de archivos. Un archivo es un conjunto de datos con un nombre que el sistema trata como una unidad; una carpeta es un contenedor con nombre que agrupa archivos y otras carpetas, y su conjunto forma una jerarquía en la que cada elemento se sitúa dentro de una carpeta. En una línea, el gestor muestra esa jerarquía como una navegación por carpetas: la ventana presenta la carpeta actual con sus elementos y permite bajar a una carpeta, subir a la carpeta que la contiene o ir a una ruta concreta, es decir, a la secuencia de carpetas que lleva hasta un elemento.
Dentro de una carpeta, el gestor puede mostrar los elementos en vista de iconos, donde cada archivo o carpeta se representa por un pictograma con su nombre, o en vista de lista, donde cada elemento ocupa una fila con varias columnas de información. Esas columnas muestran los metadatos del elemento, es decir, los datos que describen al archivo y no forman parte de su contenido, como su nombre, su tipo, su tamaño o su fecha de modificación. La información visible depende de la vista elegida, pero lo que se muestra es siempre la descripción que el sistema de archivos mantiene para cada elemento, no el contenido completo del archivo. Al activar un elemento, el gestor puede abrirlo con la aplicación asociada en función de su tipo, mostrar sus propiedades o ejecutar operaciones sobre él, como crear una carpeta nueva, renombrar, copiar, mover, eliminar o recuperar un elemento eliminado recientemente de la papelera, que es la carpeta temporal donde el sistema aparta los elementos eliminados hasta que se vacía. Todas esas operaciones se ordenan mediante menús y botones, con confirmación cuando la operación es destructiva. El gestor no lee ni escribe directamente los datos en el dispositivo de almacenamiento: pide esas acciones al sistema de archivos a través de los servicios del sistema operativo, sin ocuparse de dónde quedan guardados físicamente.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-grafica]] se desciende a una aplicación gráfica concreta definida por su tarea: si la aplicación gráfica es el programa que se usa señalando elementos visuales, el gestor de archivos gráfico es el que se usa para ver y organizar archivos y carpetas. Es una rama terminal: las aplicaciones gráficas no forman una cadena lineal, sino un conjunto de tareas paralelizables, del que esta nota muestra una tarea de organización sin abrir un siguiente peldaño.

## Límites de esta explicación
Esta nota no explica cómo el sistema de archivos guarda y recupera los datos en el dispositivo, cómo representa los archivos internamente ni qué permisos puede tener cada usuario sobre ellos; eso se trata en [[sistema-de-archivos]]. Tampoco trata cómo se dibujan las ventanas ni cómo se escuchan los dispositivos de entrada, que pertenecen al [[software-de-sistema]]. El contenido y el formato de un archivo concreto no se detalla aquí; su representación se trata en [[formatos-de-archivos]].

## Referencias
- [FTE-0001, FTE-0002]: respaldan que archivos, carpetas y jerarquía son una abstracción del sistema de archivos que el sistema operativo ofrece a las aplicaciones, y que los metadatos que el gestor muestra son los que el sistema mantiene para cada elemento. No documentan la interfaz gráfica concreta de ningún gestor, por lo que la descripción de vistas, operaciones y papelera se presenta como funcionamiento general observado, no como afirmación respaldada por estas fuentes.
