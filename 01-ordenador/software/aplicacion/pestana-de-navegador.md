---
titulo: "Pestaña de navegador"
slug: pestana-de-navegador
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [navegador-web]
conduce_a: []
alias: ["pestaña del navegador", "tab"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Pestaña de navegador

## Idea central
La pestaña de navegador (tab) es cada uno de los documentos independientes que un [[navegador-web]] puede tener abiertos a la vez dentro de la misma [[ventana]]: cada pestaña mantiene su propio documento, su propia dirección y su propio historial, y la persona cambia de una a otra sin cerrar las demás. Su valor está en pasar de «una página visible por ventana» a «varias páginas conviviendo en una sola ventana» sin perder el contexto de ninguna.

## Antes de empezar
- [[navegador-web]]: qué es un navegador web, cómo interpreta y presenta un documento recibido del servidor, y cómo organiza su contenido en ventanas y direcciones.

## Explicación
Desde [[navegador-web]] se sabe que el navegador presenta un documento en una ventana con una zona de dirección y una zona principal. La pestaña es el peldaño siguiente de esa organización en la presentación: en lugar de limitarse a un único documento por ventana, el navegador mantiene varios contenedores de documento simultáneos dentro de la misma ventana, mostrados habitualmente como una fila de etiquetas seleccionables. Solo una pestaña se ve en cada momento en la zona principal, pero las demás siguen abiertas: al cambiar de pestaña, la ventana deja de mostrar un documento y pasa a mostrar otro.

La independencia de cada pestaña es su rasgo definitorio. Cada una conserva su propio documento y el estado propio de su presentación —qué dirección se pidió, qué parte del documento se está viendo, qué se ha escrito en sus campos—, de modo que al volver a ella se la encuentra tal como se la dejó. Esa independencia explica sus dos diferencias frente a los conceptos vecinos: frente a la [[ventana]] nueva, no crea una ventana adicional ni duplica la barra de herramientas, solo añade un documento más dentro de la misma; frente a las páginas del historial, cerrar una pestaña descarta su documento abierto, mientras que el historial conserva las direcciones visitadas para poder volver a pedirlas.

Esa independencia es de presentación, no de ejecución. Todas las pestañas pertenecen al mismo navegador, que se ejecuta como un único [[proceso]] protegido por el sistema operativo y depende de los servicios que este le ofrece para usar la memoria, los archivos y la red del ordenador; la distribución interna de recursos entre pestañas es un detalle de implementación que no cambia lo que la pestaña significa para quien la usa: un documento con vida propia dentro de una ventana compartida.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[navegador-web]] se desciende a este peldaño por la organización de la presentación: si un navegador presenta documentos en una ventana, la pestaña es la unidad que permite presentar varios documentos independientes en esa misma ventana y cambiar entre ellos sin cerrar ninguno. Esta nota describe qué es una pestaña, en qué se diferencia de una ventana nueva y de una entrada del historial, y deja atrás la interpretación del contenido, ya explicada en el prerequisito. Con ello se cierra esta rama: al no tener continuidad asignada, no conduce a ningún concepto posterior del libro.

## Límites de esta explicación
Esta nota no desarrolla cómo viajan los documentos entre el navegador y el servidor, ni los protocolos, lenguajes de descripción o programas que las páginas pueden ejecutar; esos temas quedan excluidos del alcance y pertenecen a sus propias notas. Tampoco desarrolla la gestión de ventanas en general, que se trata en [[ventana]] y [[gestion-de-ventanas]], ni el ciclo de petición y respuesta, ya descrito en [[aplicacion-web]].

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar la memoria, los archivos y la red del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones. No constituye respaldo específico de las afirmaciones sobre pestañas, ventanas o protocolos de comunicación.
