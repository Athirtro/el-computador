---
titulo: "Intérprete del navegador"
slug: interprete-del-navegador
rama: software
categoria: aplicacion
nivel: 8
prerequisitos: [javascript]
conduce_a: []
alias: ["intérprete del navegador", "browser interpreter"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Intérprete del navegador

## Idea central
El intérprete del navegador es el componente del [[navegador-web]] que lee el código de la [[lenguaje-de-programacion-web]] y lo ejecuta en el cliente web, sin traducirlo antes a código nativo del sistema. Es el peldaño que convierte instrucciones escritas en programa vivo dentro de la página.

## Antes de empezar
- [[javascript]]: el lenguaje que el navegador ejecuta en el lado del cliente y que accede al modelo de objetos para leerlo y modificarlo.

## Explicación
El navegador no reconoce por sí mismo el código que acompaña a la página: necesita un intérprete. Ese intérprete lee el texto del programa, lo interpreta instrucción a instrucción y lo ejecuta en el entorno del navegador, no en el sistema operativo. La página deja de ser un documento fijo y su código puede reaccionar como un programa dentro de la propia página.

El intérprete no actúa sobre la descripción de la página, sino sobre su representación viva en memoria. Cuando el código modifica un nodo, el intérprete convierte esa modificación en un cambio de la presentación que la persona percibe sin recargar la página. De este modo, la ejecución del código y la presentación de la página comparten el mismo estado en memoria, y el navegador actualiza lo visible sin pedir de nuevo el documento al servidor.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[javascript]] se desciende a este peldaño porque el lenguaje describe qué instrucciones se ejecutan, mientras que el intérprete describe quién las ejecuta dentro del navegador. La nota cierra esta rama: al no tener continuidad asignada, no conduce a ningún concepto posterior del libro.

## Límites de esta explicación
Esta nota no desarrolla la sintaxis de [[javascript]] ni los detalles de la construcción interna por los que [[navegador-web]] dibuja los nodos modificados en pantalla. Tampoco desarrolla el [[modelo-de-objetos-del-documento]] más allá de lo necesario para explicar la ejecución.

## Referencias
- FTE-0001: respalda únicamente que el navegador, como cualquier aplicación, se ejecuta como proceso protegido por el sistema operativo y depende de los servicios que este le ofrece para usar los recursos del ordenador.
- FTE-0002: respalda únicamente el contexto general de sistema operativo como entorno en el que se ejecutan las aplicaciones.
