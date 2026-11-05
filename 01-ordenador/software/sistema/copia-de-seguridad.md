---
titulo: "Copia de seguridad"
slug: copia-de-seguridad
rama: software
categoria: sistema
nivel: 5
prerequisitos: [herramientas-de-sistema]
conduce_a: []
alias: ["copia de seguridad", "backup"]
estado: borrador
fuentes: [FTE-0005]
---

# Copia de seguridad

## Idea central
La copia de seguridad es la duplicación deliberada de los datos en un soporte distinto del original, para poder restaurarlos si se pierden o se dañan. No evita el fallo: garantiza que sus consecuencias no sean irrecuperables, a cambio de espacio, tiempo y una política de conservación decidida de antemano.

## Antes de empezar
- [[herramientas-de-sistema]]: qué son los programas auxiliares que usan los servicios del sistema operativo para mantener el ordenador, y en qué familia se sitúa la copia de seguridad.
- [[sistema-de-archivos]]: la organización persistente de archivos y carpetas sobre la que trabaja la copia, sin entrar en los tipos concretos.

## Explicación
La copia de seguridad parte de una separación sencilla: el original vive en un soporte, y la copia debe vivir en otro, de modo que lo que destruye al primero —un disco dañado, un borrado accidental, una sobrescritura— no destruya también a la segunda. Esa separación física es lo que distingue una copia de seguridad de un simple duplicado en el mismo disco: dos archivos idénticos en el mismo soporte se pierden juntos. La copia solo cumple su función cuando puede restaurarse, es decir, cuando los datos pueden volver a ponerse en su lugar tras la pérdida; una copia que nunca se ha probado en una restauración es una promesa sin verificar.

Las estrategias se diferencian en cuánto se copia cada vez. En la copia completa se duplica todo el conjunto en cada ciclo: restaurar es directo, porque basta con aplicar la última copia, pero ocupa mucho espacio y tarda mucho en producirse. En la copia incremental solo se duplican los datos modificados desde la copia anterior, sea completa o incremental: ocupa poco y es rápida de hacer, pero restaurar exige aplicar en orden la copia completa y todas las incrementales posteriores, de modo que si falta una eslabón, las siguientes quedan inutilizables. En la copia diferencial solo se copia lo modificado desde la última copia completa, acumulando cambios: restaurar requiere la completa y como máximo una diferencial, a cambio de que cada diferencial crece con el tiempo hasta la siguiente completa. La elección entre ellas es un compromiso entre espacio y tiempo de copia, frente a tiempo y fragilidad de la restauración, y no existe una estrategia óptima en abstracto: depende de cuánto se puede perder entre dos copias y cuánto vale el tiempo de recuperación.

Ese compromiso se fija en una política, que decide qué datos merecen copia, con qué frecuencia y durante cuánto tiempo se conservan las copias antiguas. Conservar solo la última copia protege del borrado reciente, pero no de un error descubierto tarde, cuando el original erróneo ya ha sustituido a la copia buena; conservar varias generaciones permite volver a estados anteriores, a cambio de más espacio. La política también decide dónde se guardan las copias: al menos una debe estar separada físicamente del equipo, porque un incendio, un robo o un fallo eléctrico afecta a todo lo que está en el mismo lugar. Y las copias heredan las exigencias de los datos originales: si en el [[sistema-de-archivos]] un archivo solo es legible por su propietario, según lo descrito en [[permisos-de-archivos]], la copia debe preservar esa condición o dejar de proteger lo que debía proteger.

Hay que distinguir, además, la copia de seguridad del diario de cambios del propio sistema de archivos. El [[journaling]] registra las modificaciones recientes para que, ante un corte de energía, el sistema pueda completar o deshacer lo que estaba a medias y volver a un estado consistente; protege la integridad del sistema de archivos, no los datos frente a su pérdida. La copia de seguridad no forma parte de ese mecanismo: es una herramienta externa al [[sistema-de-archivos]], ejecutada por un programa de [[herramientas-de-sistema]], que duplica los datos para una eventual restauración. Una cosa es recuperar un sistema consistente tras un corte, y otra muy distinta es recuperar un documento borrado hace una semana.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[herramientas-de-sistema]] se llegaba a la copia de seguridad como una de las tres familias de herramientas, definida en una línea como duplicación de los datos en un soporte distinto. Esta nota desarrolla exactamente esa línea: qué significa duplicar, qué estrategias de duplicación existen y qué compromisos entrañan, y por qué una copia solo vale si se puede restaurar. No conduce a ninguna nota posterior: es una rama terminal, porque la restauración y las políticas concretas de conservación se aplican a cada caso y no requieren un peldaño conceptual nuevo.

## Límites de esta explicación
Esta nota no describe el funcionamiento interno del [[journaling]], ni los [[tipos-de-sistema-de-archivos]] concretos sobre los que se copia, ni la sintaxis de ninguna herramienta de copia en particular. Tampoco trata de la cifrado de las copias ni de la protección frente a programas maliciosos que las borren; eso corresponde, en su caso, a [[defensa-malware]], aún no redactada.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): marco general de sistemas de archivos y persistencia.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): marco general de sistemas de archivos y persistencia.
