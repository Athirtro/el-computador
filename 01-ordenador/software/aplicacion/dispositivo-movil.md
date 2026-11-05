---
titulo: "Dispositivo móvil"
slug: dispositivo-movil
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-movil]
conduce_a: [pantalla-tactil, sensor]
alias: ["dispositivo móvil", "mobile device"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Dispositivo móvil

## Idea central
Un dispositivo móvil es un ordenador portátil pensado para sostenerse y manejarse con una o dos manos y para funcionar sin conexión a la red eléctrica, alimentado por una batería. Su importancia para el libro es que explica por qué la [[aplicacion-movil]] adopta una forma distinta de la aplicación de escritorio: la aplicación es la misma clase de programa, pero el equipo que la ejecuta es pequeño, con autonomía limitada y de uso intermitente.

## Antes de empezar
- [[aplicacion-movil]]: qué es una aplicación móvil y por qué el tipo de equipo condiciona su interfaz y su consumo.

## Explicación
El paso desde [[aplicacion-movil]] hasta el dispositivo consiste en examinar el equipo que esa aplicación presupone. Un ordenador de sobremesa permanece fijo y conectado a la red eléctrica; un dispositivo móvil, por el contrario, se traslada con la persona. Por portátil se entiende aquí un equipo compacto y ligero, de tamaño y peso compatibles con ser sujetado con una mano. Por batería se entenderá en esta nota, en una línea, el acumulador recargable que alimenta al equipo y le otorga autonomía limitada cuando no está conectado a la red eléctrica. Esa autonomía acotada tiene una consecuencia directa de programa: todo lo que el equipo hace consume una reserva que se agota, de modo que el sistema operativo debe administrar el gasto y la aplicación móvil debe limitar el trabajo en segundo plano y el brillo y la actividad de la pantalla. Como en el resto de aplicaciones, la aplicación no gestiona directamente el equipo: solicita los recursos al [[sistema-operativo]], cuyo [[nucleo-kernel]] los arbitra.

El uso con una mano define el segundo rasgo. Al ser el equipo sostenido mientras se opera, la interacción queda reducida a lo alcanzable con el dedo de esa mano, con controles grandes y gestos sencillos, en lugar del puntero y el teclado de un ordenador de escritorio. El tercer rasgo, la portabilidad, significa que el dispositivo cambia de lugar y de contexto de uso a lo largo del día, con sesiones cortas e intermitentes. Por eso la aplicación móvil debe poder detenerse y reanudarse con rapidez y no presupone un puesto de trabajo estable. La conectividad sin cables permanente forma parte de la definición habitual, pero su mecanismo de transmisión no es objeto de esta nota.

La pantalla táctil es, en una línea, la superficie que detecta el contacto del dedo y convierte su posición en órdenes; el sensor es, también en una línea, el componente que capta una magnitud física del entorno y la convierte en un dato digital. Ambos se mencionan aquí solo como rasgos que caracterizan al dispositivo, sin desarrollar su funcionamiento.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-movil]], que trata la aplicación como programa, se desciende un peldaño hasta su soporte físico: el dispositivo móvil. La batería, el tamaño y el uso con una mano explican las restricciones de energía, de interfaz y de sesión que esa aplicación debe respetar, siempre a través del sistema operativo. Hacia adelante, los siguientes peldaños son la pantalla táctil y el sensor, que estudiarán por separado cómo el dispositivo percibe el contacto del dedo y las magnitudes físicas de su entorno.

## Límites de esta explicación
Esta nota no desarrolla el funcionamiento de la pantalla táctil ni de los sensores: son los conceptos nuevos propuestos como siguiente paso. Tampoco trata los sistemas operativos móviles, la composición interna del equipo ni las aplicaciones de escritorio, cuya forma de entrada se estudia en [[aplicacion-grafica]]. Los términos pantalla táctil, sensor y batería se definen aquí en una sola línea, sin enlace, porque aún no existen como notas en la cola de listos.

## Referencias
- FTE-0001: respalda la separación entre programa de usuario y servicios del sistema operativo y del núcleo para acceder al hardware. No es una fuente específica de dispositivos móviles.
- FTE-0002: respalda la misma separación entre aplicación y gestión del hardware por el sistema. Tampoco es específica de dispositivos móviles.
