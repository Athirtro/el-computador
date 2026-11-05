---
titulo: "Modo no privilegiado"
slug: modo-no-privilegiado
rama: software
categoria: sistema
nivel: 8
prerequisitos: [espacio-de-usuario]
conduce_a: []
alias: ["modo no privilegiado", "user mode", "modo usuario"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Modo no privilegiado

## Idea central
El modo no privilegiado es el estado de ejecución en el que trabaja todo programa ordinario dentro de [[espacio-de-usuario]]. En este estado el procesador le permite usar su propia memoria y sus instrucciones, y le niega el acceso directo al núcleo y al hardware.

## Antes de empezar
- [[espacio-de-usuario]]: la zona del espacio virtual reservada a los programas ordinarios, separada de la zona del núcleo.

## Explicación
Estar en el [[espacio-de-usuario]] implica trabajar dentro de un límite, y el modo no privilegiado es la forma en que el procesador hace cumplir ese límite mientras el programa se ejecuta. Es el estado por defecto de todo [[proceso]] de usuario: un editor, un navegador o cualquier aplicación nace en este estado y permanece en él durante casi todo su trabajo.

El modo no privilegiado (user mode) significa, en la práctica, tres restricciones. En primer lugar, el programa solo puede leer, escribir y ejecutar direcciones de su propio espacio de usuario; si intenta alcanzar memoria de otro proceso o la zona del núcleo, el procesador lo detiene y no realiza el acceso. En segundo lugar, no puede hablar directamente con los dispositivos: no puede ordenar encender, apagar o leer de un disco u otro periférico por su cuenta. En tercer lugar, no puede ejecutar determinadas instrucciones que cambian el estado del procesador o que le darían control sobre el conjunto del sistema; esas instrucciones están reservadas a un estado de mayor privilegio.

Estas restricciones no son una limitación accidental, sino una protección deliberada. Gracias a ellas, un error de un programa no puede dañar directamente al [[nucleo-kernel]] ni a los demás programas, y un programa malintencionado no puede adueñarse del ordenador por la simple vía de ejecutar el código que desee. El procesador actúa como guardián: detecta el intento de acceso no permitido y transfiere el control al núcleo, que decide qué hacer con el programa, en lugar de entregar lo que se pedía.

El programa no queda por ello atrapado en su espacio. Cuando necesita algo que solo puede hacerse con más privilegio, como leer un archivo o escribir en la pantalla, lo solicita mediante un cauce controlado, como una [[llamadas-al-sistema]]. Solo entonces el procesador cambia de estado para que el núcleo realice el servicio, y al terminar vuelve al modo no privilegiado para devolver el control al programa. Así, el programa ordinario siempre ejecuta con permiso limitado y solo accede a servicios protegidos a través del núcleo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[espacio-de-usuario]] se pasa del dónde al en qué estado. El espacio de usuario es la zona donde vive cada programa ordinario, y el modo no privilegiado es el estado en que el procesador lo mantiene mientras trabaja en esa zona: con acceso solo a lo suyo y sin camino directo al hardware. El estado contrario, con acceso sin permiso, se trata en [[modo-privilegiado]]. No se introduce un peldaño siguiente, porque con [[espacio-de-kernel]] y [[modo-privilegiado]] queda cerrada la separación entre zona y estado a ambos lados: espacio de usuario con modo no privilegiado, espacio de núcleo con modo privilegiado.

## Límites de esta explicación
Esta nota no explica el estado contrario, el [[modo-privilegiado]], ni el detalle de las instrucciones que solo son válidas en ese estado; eso pertenece a [[modo-privilegiado]] y a los registros y la unidad de control. Tampoco explica el recorrido completo de una petición desde el programa hasta el núcleo, materia de [[llamadas-al-sistema]], ni la suspensión del programa ante una señal del hardware, materia de [[interrupciones]]. La composición de la zona de usuario pertenece a [[espacio-de-usuario]].

## Referencias
- [FTE-0001]: distinción entre modo usuario y modo núcleo, y denegación por el hardware de accesos no privilegiados con transferencia al sistema operativo.
- [FTE-0002]: concepto de modo protegido, restricciones del modo de usuario y necesidad de llamar al núcleo para acceder a servicios protegidos.
