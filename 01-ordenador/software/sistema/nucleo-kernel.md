---
titulo: "Núcleo (kernel)"
slug: nucleo-kernel
rama: software
categoria: sistema
nivel: 4
prerequisitos: [sistema-operativo]
conduce_a: [gestion-de-recursos]
alias: ["kernel", "núcleo"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Núcleo (kernel)

## Idea central
El núcleo es el componente del [[sistema-operativo]] que permanece activo mientras el ordenador está encendido y controla directamente el hardware. Coordina los recursos para que cada programa reciba su uso en el momento adecuado y ninguno impida el funcionamiento de los demás.

## Antes de empezar
- [[sistema-operativo]]: el programa de sistema que ofrece un entorno integral y coordina el uso del [[hardware]] para el resto del software.

## Explicación
El sistema operativo descrito en la nota anterior no actúa como un todo homogéneo: tiene un centro siempre activo, el núcleo, que es quien realmente accede a los recursos físicos. Las aplicaciones y las partes visibles del entorno le piden servicios, por ejemplo usar el procesador, acceder a la [[memoria-ram]] o escribir en un dispositivo, y es el núcleo quien los atiende en un determinado orden o deniega y aplaza una petición que no puede cumplirse entonces. Ese control directo es lo que lo distingue del conjunto de servicios y herramientas que lo rodean para hacerlo utilizable.

Que permanezca activo es esencial. Cuando el ordenador está encendido, el núcleo no se detiene entre una aplicación y otra, sino que supervisa continuamente qué programa está usando cada recurso y recupera el control cuando un programa deja de usarlo o solicita un servicio nuevo. Sin esa presencia continua no habría intermediación ni coordinación: cada programa tendría que competir directamente por los mismos recursos.

El núcleo coordina, pero no realiza la tarea de cada aplicación. No redacta documentos ni reproduce contenidos; decide el reparto y la secuencia con la que se atienden las peticiones. Tampoco enseña al sistema a manejar un periférico concreto: para ello se apoya en piezas externas que le permiten hablar con cada dispositivo, sin que esta nota entre en su funcionamiento.

La coordinación de recursos que aquí se señala a grandes rasgos es, en realidad, un conjunto de tareas propias. Saber que el núcleo asigna y recupera el procesador, la memoria y los dispositivos basta como idea de este peldaño; cómo reparte cada recurso, con qué criterios de prioridad y con qué mecanismos de protección, corresponde a la nota siguiente.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sistema-operativo]] se pasa del entorno integral —qué hace el conjunto del sistema— a su centro —qué parte está siempre activa y controla directamente el hardware—. El siguiente paso natural es [[gestion-de-recursos]], que detalla cómo el núcleo reparte los recursos en lugar de limitarse a señalar que los coordina.

## Límites de esta explicación
Esta nota no explica cómo se asignan en concreto el procesador, la memoria o los dispositivos, ni cómo se organizan los programas en ejecución; eso se trata en [[gestion-de-recursos]] y, dentro de ella, en [[gestor-de-procesos]]. Tampoco detalla la relación con los [[controladores-drivers]], los programas que enseñan a manejar cada periférico, ni la distinción entre las zonas de memoria del núcleo y de los programas, tratada en [[espacio-de-kernel]] y [[espacio-de-usuario]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
