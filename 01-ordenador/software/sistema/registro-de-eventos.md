---
titulo: "Registro de eventos"
slug: registro-de-eventos
rama: software
categoria: sistema
nivel: 6
prerequisitos: [diagnostico-de-sistema]
conduce_a: []
alias: ["registro de eventos", "event log", "log del sistema"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Registro de eventos

## Idea central
El registro de eventos es la memoria cronológica que el [[sistema-operativo]] mantiene de los avisos, errores y actividad relevante que ocurren durante su funcionamiento. Permite diagnosticar un fallo ocurrido en el pasado, y no solo en el momento observable, porque cada hecho quedó anotado con su momento, su origen y su gravedad.

## Antes de empezar
- [[diagnostico-de-sistema]]: procedimiento de observar, comparar y localizar un fallo con las [[herramientas-de-sistema]]. Esta nota explica de dónde obtienen parte de esa información las herramientas.

## Explicación
Diagnosticar, como se vio en [[diagnostico-de-sistema]], empieza por observar el estado del ordenador a través del [[sistema-operativo]]. Pero esa observación tiene un límite: si un fallo ya ocurrió y el sistema volvió a su estado normal, observar el presente no lo mostrará. El registro de eventos existe para salvar esa distancia entre el momento del fallo y el momento del diagnóstico.

A diferencia de observar el estado actual, consultar el registro de eventos es consultar un archivo ya escrito. El [[nucleo-kernel]] y los [[controladores-drivers]] que gestiona, así como otros servicios del sistema, anotan un hecho cuando ocurre: con la hora en que sucedió, el componente que lo originó y una indicación de su importancia, que distingue un simple aviso informativo de un error que impidió una operación. Esas anotaciones se almacenan de forma persistente en el [[sistema-de-archivos]], para que sobrevivan a reinicios y puedan examinarse después.

El valor del registro no está en una entrada aislada, sino en su orden. Al estar ordenado por tiempo, el registro permite reconstruir una secuencia: qué ocurrió inmediatamente antes de que un programa dejara de responder, si varios componentes registraron errores en la misma ventana de tiempo, o si un aviso se repite cada arranque. Esa secuencia es la evidencia que la herramienta de diagnóstico compara con el comportamiento esperado. Sin ella, un síntoma actual habría de explicarse solo por conjeturas; con ella, el diagnóstico se apoya en hechos comprobables.

Esa función explica también por qué el registro es de solo lectura para quien diagnostica. La herramienta de diagnóstico no escribe en el registro para hacer pasar un fallo por normal: lo lee, junto a la información del estado actual que obtiene mediante las [[llamadas-al-sistema]], y cruza ambas fuentes. Cuanto más completo sea el registro, más preciso será ese contraste.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[diagnostico-de-sistema]] se llegaba a la pregunta de dónde encuentra la observación su evidencia cuando el fallo ya pasó. Esta nota cierra esa pregunta: del estado actual observable se pasa a la historia registrada por el [[sistema-operativo]], que es la segunda fuente del diagnóstico. No conduce a ninguna nota posterior: es una rama terminal, porque el detalle de cómo se lee o filtra el registro pertenece a cada herramienta concreta y no forma un peldaño nuevo de abstracción.

## Límites de esta explicación
Esta nota no trata el detalle de ninguna herramienta concreta —ni su sintaxis, ni sus filtros, ni la ubicación exacta del archivo de registro en cada sistema—, que pertenece a la práctica de uso de esas herramientas y no a un concepto general. Tampoco trata otros registros distintos, como el de usuarios o el de cambios de un sistema de archivos, que tienen finalidades propias y se tratarán en sus notas correspondientes. Para las herramientas que consultan el registro, véase [[herramientas-de-sistema]] y [[diagnostico-de-sistema]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): función de observación que el sistema operativo ofrece para el diagnóstico.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): servicios del sistema operativo que registran la actividad del núcleo y sus controladores.
