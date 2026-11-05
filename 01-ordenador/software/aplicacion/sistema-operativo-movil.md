---
titulo: "Sistema operativo móvil"
slug: sistema-operativo-movil
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-movil]
conduce_a: []
alias: ["sistema operativo móvil", "mobile operating system"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Sistema operativo móvil

## Idea central
El sistema operativo móvil (mobile operating system) es la variante del [[sistema-operativo]] orientada a dispositivos portátiles de uso táctil, con sensores integrados y alimentación por batería. Cumple las mismas funciones básicas de gestión del equipo, pero adapta la entrada, la salida y el consumo de recursos a ese entorno.

## Antes de empezar
- [[aplicacion-movil]]: qué es una aplicación móvil, cómo usa la pantalla táctil y los sensores, y por qué depende del sistema para acceder al hardware.

## Explicación
El [[sistema-operativo]] es el software que intermedia entre las aplicaciones y el hardware: gestiona el procesador, la memoria y los dispositivos a través del [[nucleo-kernel]], de modo que una aplicación no necesita manejar directamente esos componentes. El sistema operativo móvil mantiene esa función, pero el equipo al que sirve es distinto del ordenador personal: es compacto, se maneja con las manos, tiene pantalla táctil y funciona con batería.

La primera adaptación afecta a la entrada y a la salida. La aplicación móvil no recibe la entrada de un teclado ni de un ratón, sino los toques y gestos sobre la pantalla, y presenta una [[interfaz-grafica-de-usuario]] en un espacio reducido. El sistema operativo móvil debe por tanto reconocer esos eventos táctiles, entregarlos a la [[aplicacion-movil]] en primer plano y representar su resultado en pantalla. Estos gestos —tocar, desplazar, ampliar— son para el sistema el equivalente de los clics y las teclas en un ordenador de escritorio: el canal de comunicación entre la persona y el programa.

La segunda adaptación afecta a los sensores. El sensor es el componente que capta una magnitud física —posición, orientación, proximidad o aceleración— y la convierte en un dato digital. A diferencia de la aplicación, el sistema operativo móvil coordina el acceso de cada programa a esos sensores a través del [[nucleo-kernel]] y de los [[controladores-drivers]] correspondientes, de manera que varias aplicaciones no compiten directamente por el mismo componente. La aplicación solicita el dato; el sistema lo arbitra.

La tercera adaptación afecta a la gestión de recursos. El sistema operativo móvil trabaja con un procesador y una memoria de tamaño reducido y con batería limitada, por lo que debe decidir qué aplicaciones permanecen activas, cuáles se suspenden y cuánta energía consume cada componente cuando el dispositivo está en uso o en reposo. Esa decisión es una aplicación concreta de la [[gestion-de-recursos]] y de la [[multitarea]]: repartir el procesador y la memoria entre aplicaciones, pero tomando como criterio adicional el consumo de batería, no solo el tiempo de respuesta.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-movil]] se sabe que la aplicación móvil depende del sistema operativo para acceder a la pantalla táctil y a los sensores sin manejar el hardware directamente. Esta nota describe ese sistema desde el otro lado: no es un sistema operativo distinto en su función —sigue mediando entre aplicaciones y hardware—, sino la misma función adaptada a un equipo táctil, con sensores y batería. No conduce a un siguiente peldaño: el detalle de plataformas concretas, de pantallas y de sensores pertenece a notas de hardware y de sistema aún no registradas.

## Límites de esta explicación
Esta nota no desarrolla el [[sistema-operativo]] general, tratado en su propia nota, ni las interioridades del [[nucleo-kernel]], la [[gestion-de-recursos]] y la [[multitarea]], que se enlazan pero no se repiten aquí. Tampoco describe plataformas concretas ni cómo funcionan físicamente la pantalla táctil o los sensores; esos conceptos se definen en una línea y quedan como conceptos nuevos por registrar por el orquestador antes de enlazarlos.

## Referencias
- FTE-0001: respalda la idea general de que el sistema operativo media entre la aplicación y el hardware a través del núcleo y de la gestión de recursos. No es una fuente específica de sistemas operativos móviles.
- FTE-0002: respalda la misma separación entre programa de usuario y gestión del hardware por el sistema. Tampoco es específica de dispositivos móviles.
