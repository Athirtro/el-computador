---
titulo: "Herramientas de sistema"
slug: herramientas-de-sistema
rama: software
categoria: sistema
nivel: 4
prerequisitos: [software-de-sistema]
conduce_a: []
alias: ["herramientas de sistema", "utilidades de sistema"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Herramientas de sistema

## Idea central
Las herramientas de sistema son programas auxiliares que usan los servicios del [[sistema-operativo]] para observar, mantener y operar el ordenador, sin gestionar directamente el hardware. Son el apoyo práctico que permite diagnosticar fallos, proteger los datos y controlar el sistema mediante órdenes directas.

## Antes de empezar
- [[software-de-sistema]]: qué es el software que gobierna el hardware y crea el entorno para el resto de programas, y en qué se diferencia de las aplicaciones de usuario.
- [[sistema-operativo]]: el entorno integral que ofrece memoria, archivos y dispositivos a los demás programas, y que las herramientas utilizan en lugar de acceder al hardware por su cuenta.

## Explicación
El [[software-de-sistema]] ya describía un cuarto grupo además del sistema operativo, el firmware y los controladores: los programas auxiliares que ayudan a mantener el ordenador en funcionamiento. Una herramienta de sistema no sustituye al [[nucleo-kernel]], que sigue siendo el componente que concede el procesador, la memoria y los dispositivos; la herramienta se ejecuta como un programa más, solicita recursos a través de los servicios del sistema operativo y muestra al usuario el resultado. Su valor está en traducir ese control interno en información y acciones manejables.

La primera familia es la de diagnóstico y mantenimiento. Estas utilidades consultan el estado que el sistema operativo conoce —qué procesos están activos, cuánta memoria se usa, si un disco presenta errores, cómo responde un dispositivo— y lo presentan de forma legible. Cuando algo falla, no reparan el hardware en sentido físico, sino que señalan dónde está el problema para que pueda corregirse, por ejemplo sustituyendo un componente o reconfigurando un ajuste. Observar antes de actuar es su principio común: sin diagnóstico, cualquier reparación sería a ciegas.

La segunda familia es la copia de seguridad (en inglés, *backup*, solo en esta primera aparición). Una copia de seguridad es una duplicación deliberada de los datos, guardada en un soporte distinto del original, para poder recuperarlos si el disco se daña o los archivos se pierden. La herramienta no evita el fallo; garantiza que sus consecuencias no sean irrecuperables. Por eso trabaja sobre el [[sistema-de-archivos]] entendido en sentido general —la organización de carpetas y archivos que el sistema operativo mantiene—, sin necesidad de explicar aquí cómo se implementa esa organización.

La tercera familia es la del intérprete de órdenes, o *shell*. El shell es un programa que lee órdenes escritas en formato de texto, una por línea, y las ejecuta invocando a otras herramientas o solicitando servicios al sistema operativo. Frente a una interfaz gráfica, que presenta botones y ventanas, el shell permite encadenar varias operaciones en una sola secuencia y registrarlas paso a paso. Es el punto de contacto directo entre la persona que opera el sistema y las herramientas que este pone a su disposición, y por eso se agrupa con ellas aunque su función sea invitarlas a actuar y no actuar por sí mismo.

En conjunto, las tres familias comparten una posición: están por encima del núcleo y por debajo de la tarea concreta del usuario. No escriben documentos ni reproducen vídeos, como haría el [[software-de-aplicacion]]; cuidan el terreno sobre el que esas tareas se ejecutan.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-sistema]] se llegaba a las herramientas como el grupo de programas que mantienen el sistema sin gobernarlo. Esta nota desarrolla ese grupo: usan el [[sistema-operativo]] —y, a través de él, el control del [[nucleo-kernel]] sobre los recursos— para diagnosticar, proteger los datos y ejecutar órdenes. No conduce a ninguna nota posterior: es una rama terminal, porque cada herramienta concreta se entiende mejor una vez dominado este panorama general.

## Límites de esta explicación
Esta nota no detalla el funcionamiento de ninguna herramienta concreta, ni la sintaxis de órdenes de un shell concreto, ni las estrategias de copia (qué datos guardar, con qué frecuencia o en qué soporte). Tampoco explica cómo el [[nucleo-kernel]] concede los recursos que las herramientas solicitan; eso se trata en [[gestion-de-recursos]]. El detalle de cada familia queda para notas propias si el orquestador decide abrirlas.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): papel de utilidades del sistema operativo.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): papel de utilidades del sistema operativo.
