---
titulo: "Puente nativo"
slug: puente-nativo
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [componente-web-incorporado]
conduce_a: []
alias: ["puente nativo", "native bridge"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Puente nativo

## Idea central
El puente nativo es la frontera que permite a la parte web de una [[aplicacion-hibrida]] pedir servicios al equipo —archivos, sensores, red, configuración— sin tener acceso directo a ellos. Traduce una petición expresada con los medios de la web (código y mensajes del navegador) a una llamada propia del sistema y devuelve la respuesta en el mismo lenguaje de origen.

## Antes de empezar
- [[componente-web-incorporado]]: el componente incrustado que interpreta y presenta el contenido web dentro del programa instalado, y que comparte con la envoltura el mismo [[proceso]] en [[espacio-de-usuario]].

## Explicación
Desde [[aplicacion-hibrida]] se sabe que el programa está instalado y se ejecuta localmente como un [[proceso]] que solo alcanza los recursos del equipo mediante las [[llamadas-al-sistema]] del núcleo a través del [[sistema-operativo]]. En una aplicación híbrida, la parte web —documento de marcado más código ejecutado en el navegador, en buena medida [[javascript]]— no puede emitir esas llamadas: no ve el sistema por sí misma, solo ve el [[modelo-de-objetos-del-documento]] y la interfaz que le expone su entorno. Por eso el acceso no es directo: la petición web se detiene primero en el borde del componente incorporado y solo continúa si pasa por el puente nativo (native bridge).

El puente funciona como un traductor entre dos vocabularios. Del lado web, el programa pide con un nombre y unos argumentos —por ejemplo, pedir que se guarde un dato o consultar un [[sensor]]— en la forma en que lo haría dentro de un [[navegador-web]]. El puente convierte ese mensaje en la función nativa equivalente de la envoltura: le da forma propia del sistema concreto, empaqueta sus argumentos con tipos que ambos extremos entienden y encola la ejecución en el mismo proceso, sin salir a un programa distinto. Es la envoltura —no la parte web— la que entonces ejecuta la [[llamadas-al-sistema]] correspondiente y recibe el resultado del núcleo. Nada de lo que la web puede hacer atraviesa ese camino sin ser despachado explícitamente por el puente: si un servicio no está expuesto, el puente lo deniega, por mucho que la parte web lo solicite.

A la vuelta, el puente traduce la respuesta nativa al formato que espera la parte web: valores, errores y objetos con un vocabulario común. Así, el código web recibe los datos o el motivo del fallo como si hubiera respondido el propio componente web, sin saber qué llamada al sistema se ejecutó por debajo. Esta ida y vuelta es asimétrica por diseño: la web propone el servicio, el puente decide cómo ejecutarlo con los medios nativos y devuelve solo el resultado, nunca el acceso sin filtros a los mecanismos internos del sistema. De ahí que el puente sea también el punto donde se aplica el criterio de exposición mínima: cada función que lo cruza debe estar inscrita en la envoltura, y todo lo demás queda fuera del alcance de la parte web.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[componente-web-incorporado]] es de especialización dentro de la misma [[aplicacion-hibrida]]: el componente sabe presentar la pantalla, pero no puede hablar con el equipo; el puente es esa lengua común entre la parte web y la envoltura nativa, apoyada en las llamaciones al sistema ya explicadas en el resto de la cadena. Esta nota no abre un concepto siguiente en la cola: explica qué se traduce y en qué sentido en el peldaño `puente-nativo` → `llamadas-al-sistema`, sin entrar en los mecanismos web ni en los del sistema, que ya tienen sus notas.

## Límites de esta explicación
No se trata aquí el detalle del [[componente-web-incorporado]] ni de la [[aplicacion-hibrida]] en su totalidad, de la que ya se ocupan sus notas. Tampoco se detallan las llamadas concretas del sistema, la serialización de datos ni los controles de seguridad del puente, que pertenecen al peldaño siguiente, las [[llamadas-al-sistema]], donde se explica cómo todo programa de usuario en última instancia accede al núcleo. La aplicación web convención que corre en un [[navegador-web]] independiente queda fuera, porque no tiene envoltura ni puente que cruzar, y se trata en [[aplicacion-web]].

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces — respalda que el programa de usuario solo accede a los recursos mediante servicios controlados del núcleo, fundamento de que la parte web cruce necesariamente el puente y la envoltura antes de llegar a las llamadas al sistema.
- [FTE-0002] Modern Operating Systems — respalda la distinción entre programa de usuario y núcleo que gestiona los recursos en su nombre, base para explicar que el lado nativo del puente, y no la web, es quien ejecuta la llamada al sistema.
