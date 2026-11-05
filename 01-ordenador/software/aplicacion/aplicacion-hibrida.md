---
titulo: "Aplicación híbrida"
slug: aplicacion-hibrida
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-de-escritorio]
conduce_a: []
alias: ["aplicación híbrida", "hybrid application"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Aplicación híbrida

## Idea central
La aplicación híbrida es una aplicación instalada en un equipo que se presenta como una [[aplicacion-de-escritorio]] o como una aplicación móvil, pero cuya interfaz y parte de su lógica están escritas con tecnologías web y se ejecutan dentro de un componente incrustado que interpreta contenido web. Se crea una sola vez para varios sistemas y se empaqueta como programa nativo.

## Antes de empezar
- [[aplicacion-de-escritorio]]: qué es una aplicación instalada que se ejecuta localmente como un programa del sistema operativo.

## Explicación
Desde [[aplicacion-de-escritorio]] se sabe que el programa está instalado en el equipo, se lanza desde el sistema y trabaja como [[proceso]] en [[espacio-de-usuario]], pidiendo recursos al sistema mediante [[llamadas-al-sistema]]. Una aplicación híbrida mantiene exactamente esa forma de ejecución: se instala, tiene icono, se ejecuta localmente y sigue siendo un proceso de usuario sujeto a las mismas reglas del [[sistema-operativo]]. Lo que cambia no es dónde se ejecuta, sino cómo se construye por dentro.

En una aplicación híbrida, la mayor parte de la pantalla no está escrita con los controles propios de cada sistema, sino con los mismos recursos que usa una [[aplicacion-web]]: un documento descrito con un lenguaje de marcado y comportamiento programado para el navegador. Ese contenido no se abre en un [[navegador-web]] completo e independiente, sino dentro de un componente incrustado —una vista web incorporada en el programa— que interpreta y presenta el contenido web como si fuera una pantalla más de la aplicación instalada. Por eso el usuario ve una ventana o pantalla normal de su sistema, pero el interior de esa pantalla lo está renderizando ese componente web.

Alrededor de esa parte web se coloca una envoltura nativa: es la parte escrita para el sistema concreto donde se instala y la que permite que el programa tenga icono, se instale como los demás programas y acceda a funciones propias del equipo. Entre la parte web y esa envoltura hay un puente que traduce las peticiones de la parte web —por ejemplo, guardar un dato o consultar un dispositivo— a las llamadas que el sistema entiende, y devuelve la respuesta. La parte web, por sí sola, no puede acceder directamente a todo el equipo; el acceso pasa por ese puente y, en última instancia, por las llamadas al sistema ordinarias.

Así, la lógica de negocio y la interfaz se escriben una sola vez con tecnología web y se reutilizan en varios equipos, mientras que la envoltura y el puente se adaptan a cada sistema. El coste es una dependencia del componente web incorporado y una capa de traducción adicional; la ventaja es no duplicar toda la aplicación para cada plataforma.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[aplicacion-de-escritorio]] es de especialización dentro de la misma forma de ejecución local: se conserva el programa instalado que es un proceso del sistema, pero se divide su construcción en una parte web reutilizable y una envoltura propia de cada sistema, unidas por un puente. Esta nota no abre un peldaño siguiente en la cola: es una rama terminal que clasifica una estrategia de construcción, sin desarrollar el componente web incorporado ni el puente, que quedan propuestos como conceptos nuevos.

## Límites de esta explicación
Esta nota no trata la aplicación nativa pura, escrita por completo con los medios propios de un solo sistema sin parte web ni componente incorporado; tampoco desarrolla el componente web incorporado ni el puente que comunica la parte web con el sistema, que se proponen como conceptos nuevos. La aplicación web que se ejecuta en un navegador independiente queda fuera, porque no está instalada como programa local, y se trata en [[aplicacion-web]].

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces — respalda que un programa de usuario se ejecuta como proceso en espacio de usuario y solo accede a los recursos mediante servicios controlados del sistema operativo, lo que se aplica también a la envoltura híbrida.
- [FTE-0002] Modern Operating Systems — respalda la distinción entre programa de usuario y núcleo que gestiona los recursos en nombre de aquel, base para explicar que el acceso de la parte web al equipo pasa por la envoltura y el sistema.
