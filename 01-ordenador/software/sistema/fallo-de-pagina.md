---
titulo: "Fallo de página"
slug: fallo-de-pagina
rama: software
categoria: sistema
nivel: 9
prerequisitos: [paginacion]
conduce_a: []
alias: ["fallo de página", "page fault"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Fallo de página

## Idea central
El fallo de página es el momento en que un programa accede a una página virtual que no está cargada en ningún marco físico y el sistema debe traerla antes de poder continuar. Es el paso que convierte la posibilidad, ya descrita en la [[paginacion]], de tener cargadas solo algunas páginas en un mecanismo concreto de carga bajo demanda.

## Antes de empezar
- [[paginacion]]: la división del espacio virtual en páginas de tamaño fijo y la traducción de cada dirección virtual al marco físico que contiene la página, o a la constatación de que esa página no está cargada.

## Explicación
Cuando un programa usa una dirección virtual, la traducción sustituye el número de página virtual por el número del marco físico donde reside esa página y conserva el desplazamiento dentro de ella. Si la página pedida no está en ningún marco, la traducción no puede formar la dirección física: se produce un fallo de página (*page fault*). No es un error del programa en sí, sino la señal de que falta un dato que el sistema sí puede conseguir.

Al detectarse, la ejecución del programa se interrumpe y el control pasa al núcleo, que es quien gestiona la memoria a través del [[gestor-de-memoria]]. El núcleo localiza el contenido de la página, que esperaba en el almacenamiento asociado a la [[memoria-virtual]], elige un marco libre para cargarla o, si no los hay, libera otro marco cuya página se aparta, y copia el contenido de la página al marco elegido. Solo entonces queda registrada la nueva correspondencia entre esa página virtual y ese marco físico.

Una vez cargada, la traducción se repite y el acceso original se completa como si el fallo no hubiera ocurrido. El programa no necesita saber que su página ha estado ausente: solo experimenta, en el peor caso, una pausa. Esta es la razón por la que un espacio virtual puede ser mucho mayor que la memoria física, porque en cada momento solo hace falta tener cargadas las páginas que se están usando.

No todos los fallos se resuelven trayendo la página. Si la dirección virtual pedida no pertenece a ningún espacio asignado al programa —por ejemplo, porque apunta fuera de sus páginas válidas—, no hay contenido que traer. En ese caso el sistema no puede completar el acceso y debe señalar el error al programa, que en general termina sin poder continuar. La diferencia entre estas dos situaciones es la que separa un fallo de página normal, que el sistema resuelve, de un acceso inválido, que el sistema rechaza.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[paginacion]] se conocía la traducción y la posibilidad de que una página no estuviera cargada. Esta nota describe paso a paso qué ocurre en ese caso: se interrumpe la ejecución, el núcleo trae la página a un marco y la traducción se repite. Sin este peldaño, la exigencia de traer la página quedaba como un enunciado sin mecanismo.

## Límites de esta explicación
Esta nota no explica cómo se organiza internamente el registro de correspondencias entre páginas y marcos; eso se trata en el detalle de la [[tabla-de-paginas]]. Tampoco explica qué página se aparta cuando no hay marcos libres ni cómo se lee el contenido desde el dispositivo de almacenamiento; son peldaños posteriores. No trata los mecanismos que aceleran la traducción en el caso habitual de página ya cargada.

## Referencias
- FTE-0001: descripción del fallo de página como interrupción del acceso, carga de la página en un marco y reanudación de la traducción, y distinción con el acceso a una dirección inválida.
- FTE-0002: tratamiento del fallo de página como mecanismo de la paginación y de la memoria virtual, con el papel del sistema operativo en cargar la página ausente.
