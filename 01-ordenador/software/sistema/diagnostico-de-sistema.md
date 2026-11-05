---
titulo: "Diagnóstico de sistema"
slug: diagnostico-de-sistema
rama: software
categoria: sistema
nivel: 5
prerequisitos: [herramientas-de-sistema]
conduce_a: []
alias: ["diagnóstico de sistema", "herramienta de diagnóstico"]
estado: borrador
fuentes: [FTE-0005]
---

# Diagnóstico de sistema

## Idea central
El diagnóstico de sistema es el uso de las herramientas de sistema para observar el estado del ordenador, comparar lo observado con lo esperado y localizar el origen de un fallo. No repara el hardware: produce un indicio fiable para decidir qué debe repararse, sustituirse o reconfigurarse.

## Antes de empezar
- [[herramientas-de-sistema]]: qué son las herramientas de sistema, qué familias forman y por qué actúan a través del [[sistema-operativo]] y no directamente sobre el hardware.

## Explicación
Diagnosticar empieza por observar. La información disponible no viene del componente sospechoso en bruto, sino del [[sistema-operativo]], que la ha recogido al gestionar los recursos: qué [[proceso|procesos]] están activos y consumiendo procesador, cuánta memoria está en uso según el [[gestor-de-memoria]], si el [[sistema-de-archivos]] ha registrado errores al leer o escribir, o si un [[controladores-drivers|controlador]] ha dejado de responder. La herramienta de diagnóstico pregunta a esos servicios mediante las [[llamadas-al-sistema]] y presenta la respuesta de forma legible, sin gobernar por sí misma el [[nucleo-kernel]].

El segundo paso es comparar. Un dato aislado —por ejemplo, un uso elevado de memoria— no es todavía un diagnóstico: hay que contrastarlo con el comportamiento normal y con los síntomas descritos por el usuario. Si un programa concreto consume recursos de forma sostenida, el origen probable es ese programa; si el fallo aparece con cualquier programa y el sistema operativo señala errores de lectura, el origen probable está en el almacenamiento o en su controlador. Esa comparación entre síntoma, estado observado y funcionamiento esperado es lo que separa diagnosticar de simplemente mirar cifras.

El tercer paso es localizar, entendido como acotar el origen hasta un componente o función concreta. El diagnóstico distingue, en la medida de lo posible, entre un fallo de software —un proceso que se cuelga, un sistema de archivos dañado, un controlador defectuoso— y un fallo de hardware —un disco que devuelve errores, una memoria que produce datos incorrectos—. Esa distinción es su resultado práctico: una vez localizado el origen, la reparación deja de ser un ensayo a ciegas y pasa a ser una intervención concreta, que ya pertenece a otra fase. Por eso el principio de las herramientas de diagnóstico es observar antes de actuar.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[herramientas-de-sistema]] se llegaba al diagnóstico como una de sus tres familias, junto a la copia de seguridad y el intérprete de órdenes. Esta nota desarrolla solo esa familia: cómo las herramientas usan la información que el [[sistema-operativo]] posee gracias a la [[gestion-de-recursos]] para observar el estado, compararlo con lo esperado y acotar el fallo. No conduce a ninguna nota posterior: es una rama terminal, porque el diagnóstico completo de un componente concreto se entiende mejor una vez dominado este procedimiento general.

## Límites de esta explicación
Esta nota no trata la reparación física —sustituir un disco, una memoria o cualquier otro componente—, que pertenece a las notas de hardware correspondientes, ni la reparación de software concreta, como reinstalar un programa o corregir los daños de un sistema de archivos. Tampoco detalla el funcionamiento interno de ninguna herramienta concreta ni la sintaxis de sus órdenes. Para la copia de seguridad y el intérprete de órdenes, véase [[herramientas-de-sistema]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): marco general de observación del sistema operativo para diagnóstico.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): marco general de observación del sistema operativo para diagnóstico.
