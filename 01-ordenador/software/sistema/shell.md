---
titulo: "Shell"
slug: shell
rama: software
categoria: sistema
nivel: 5
prerequisitos: [herramientas-de-sistema]
conduce_a: []
alias: ["intérprete de órdenes", "shell"]
estado: borrador
fuentes: [FTE-0002]
---

# Shell

## Idea central
El shell es un programa que lee órdenes escritas como texto, las interpreta y hace que el [[sistema-operativo]] las ejecute. Su importancia está en servir de punto de contacto directo entre quien opera el sistema y las herramientas que este pone a su disposición, tanto en uso interactivo como en secuencias automatizadas.

## Antes de empezar
- [[herramientas-de-sistema]]: las herramientas de sistema son programas auxiliares que usan los servicios del [[sistema-operativo]] para diagnosticar, mantener y operar el ordenador.

## Explicación
El shell se sitúa entre la persona que escribe una orden y el resto de programas del sistema. Cuando escribe una línea, el shell la analiza para reconocer qué programa se quiere ejecutar y con qué datos de entrada; después solicita al sistema operativo que lo ponga en marcha como un [[proceso]] y espera o no su finalización según la forma de la orden. El resultado visible procede de ese programa ejecutado o de los servicios del sistema operativo, no de un acceso directo del shell al hardware.

Ese ciclo de lectura, interpretación y ejecución convierte al shell en un [[interprete]] especializado: no traduce un programa completo antes de ejecutarlo, como ocurre con un compilador, sino que va leyendo y ejecutando las órdenes de una en una. Por eso el usuario puede corregir una orden antes de ejecutarla, ver enseguida el efecto de cada paso y repetir el mismo procedimiento sin tener que construir ni compilar ningún programa nuevo.

La misma lectura orden por orden permite otra forma de uso: guardar una secuencia de órdenes en un archivo y entregárselo al shell para que las ejecute en conjunto. Ese archivo recibe el nombre de guion, y el conjunto de guiones forma lo que se llama *scripting*: automatizar tareas repetitivas, como preparar un entorno de trabajo, copiar o renombrar muchos archivos, o ejecutar varias herramientas en un orden fijo. La diferencia con el uso interactivo no está en el tipo de órdenes, sino en quién las introduce: en un caso, la persona línea a línea; en el otro, el autor del guion una sola vez, que puede volver a ejecutarse cuando sea necesario.

El shell tampoco sustituye a las herramientas que invoca. Si la orden pide información sobre el estado del sistema, el shell solicita el servicio correspondiente y transmite el resultado; si pide ejecutar una utilidad de diagnóstico o de copia, la pone en marcha y se limita a recoger su salida o su código de finalización. Su función propia es interpretar, encadenar y registrar órdenes, mientras que el trabajo especializado sigue correspondiendo a cada herramienta concreta dentro de las [[herramientas-de-sistema]].

## Cómo se conecta con lo anterior y lo siguiente
Desde [[herramientas-de-sistema]] se llegaba al shell como una de las familias de herramientas, la encargada de ejecutar órdenes directas frente a otras familias dedicadas al diagnóstico o a la copia de seguridad. Esta nota desarrolla esa familia: el shell actúa vía [[sistema-operativo]] y a través de [[proceso]], sin gobernar directamente el hardware como hace el [[nucleo-kernel]]. No conduce a ninguna nota posterior: es una rama terminal, porque su funcionamiento general se entiende sin necesidad de explicar la sintaxis de ningún shell concreto.

## Límites de esta explicación
Esta nota no explica la sintaxis concreta de ningún shell, ni los comandos específicos de cada sistema, ni el detalle de las formas de encadenar órdenes que un shell concreto ofrece. Tampoco explica cómo el [[nucleo-kernel]] crea los [[proceso]] que el shell solicita; eso se trata en [[gestion-de-recursos]]. El detalle de terminales de texto, redirecciones y guiones concretos queda para notas propias si el orquestador decide abrirlas.

## Referencias
- FTE-0002: Modern Operating Systems, 4th Edition. Respalda la descripción general del shell como intérprete de órdenes y su papel frente a los servicios del sistema operativo.
