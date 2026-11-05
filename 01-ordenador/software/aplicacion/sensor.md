---
titulo: "Sensor"
slug: sensor
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [dispositivo-movil]
conduce_a: []
alias: ["sensor"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Sensor

## Idea central
Un sensor es el componente que capta una magnitud física del entorno —movimiento, orientación, luz, proximidad, posición— y la convierte en una señal eléctrica que, tras su digitalización, llega al programa como un dato numérico. Es el peldaño que permite que una [[aplicacion-movil]] perciba el mundo sin que la persona teclee o toque nada.

## Antes de empezar
- Dispositivo móvil: ordenador compacto alimentado por batería que se sostiene con una o dos manos, con pantalla táctil, sensores integrados y conectividad permanente. Sin este concepto no hay contexto en el que el sensor importe: no es un periférico enchufado al azar, sino un componente interno del equipo.
- [[software-de-aplicacion]]: qué es una aplicación y en qué se distingue del software de sistema y del de programación.
- [[sistema-operativo]]: qué es el sistema que arbitra el acceso al hardware en lugar del programa.

## Explicación
El sensor cierra un circuito que va del mundo físico al programa. En el extremo físico hay un fenómeno —por ejemplo, una aceleración, un campo magnético o una variación de luz—; en el extremo lógico hay un número que el programa puede comparar, promediar o registrar. El sensor es el eslabón que traduce el primero en el segundo.

Esa traducción ocurre en tres pasos que conviene no confundir. Primero, el elemento sensible reacciona al fenómeno y produce una señal eléctrica analógica, es decir, de valor continuo: a más aceleración, más voltaje. Segundo, esa señal se digitaliza en un número, con una resolución y una frecuencia de muestreo determinadas. Tercero, el dato llega a la aplicación a través del [[sistema-operativo]], que la application no accede al hardware directamente, sino que lo solicita al sistema y el [[nucleo-kernel]] lo arbitra. De este modo la aplicación móvil puede saber que el dispositivo se mueve, cambia de orientación o se encuentra cerca de un obstáculo, porque recibe esos datos ya normalizados del sistema, no del sensor desnudo.

En un dispositivo móvil el sensor es un componente integrado, no un enchufe externo. Por ello su uso es continuo y consumible: si la aplicación muestrea mucho y a menudo, gasta batería, y por eso los sistemas operativos limitan el ritmo y el consumo. Que la aplicación no pueda tocar el sensor directamente no es un capricho de seguridad: es lo que permite a varias aplicaciones compartir el mismo sensor y al sistema decidir quién lo usa y cuándo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-aplicacion]] se avanza a una aplicación concreta, la móvil. Pero el sensor añade un peldaño más: el que separa lo que la persona hace —tocar, desplazar— de lo que el entorno hace —mover el dispositivo, girarlo, acercarlo a la luz—. La nota es terminal: no conduce a un siguiente peldaño, porque el detalle de cómo está construido físicamente cada tipo de sensor pertenece a una capa de hardware más profunda, aún no registrada en el libro.

## Límites de esta explicación
Esta nota no explica cómo detecta el dedo la pantalla táctil ni qué principio físico usa cada tipo de sensor —acelerómetro, brújula, sensor de luz—; tampoco explica por qué el sistema limita el muestreo. Esos conceptos —pantalla táctil y tipos de sensor— figuran en la cola de pendientes, no en la de listos, así que aquí se nombran en una línea sin enlace, según la regla de aislamiento. Tampoco se tratan aquí los controladores que enseñan al sistema a manejar cada sensor; para ello se enlaza a [[controladores-drivers]] como vía de acceso, sin expandir su contenido.

## Referencias
- FTE-0001: respalda que el acceso al hardware se intermedia por el sistema operativo y el núcleo. No es una fuente específica de sensores en dispositivos móviles.
- FTE-0002: respalda la misma separación entre programa de usuario y gestión del hardware por el sistema. Tampoco es específica de sensores.
