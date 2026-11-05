---
titulo: "Instrucción privilegiada"
slug: instruccion-privilegiada
rama: software
categoria: sistema
nivel: 9
prerequisitos: [modo-privilegiado]
conduce_a: []
alias: ["instrucción privilegiada", "privileged instruction"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Instrucción privilegiada

## Idea central
Una instrucción privilegiada es una instrucción del procesador que solo puede ejecutarse cuando el procesador está en [[modo-privilegiado]] y que en [[modo-no-privilegiado]] no se ejecuta. Es el peldaño que convierte el estado de privilegio en una comprobación concreta, instrucción a instrucción.

## Antes de empezar
- [[modo-privilegiado]]: el estado en el que el procesador permite acceder sin permiso a toda la memoria y al hardware, estado en el que trabaja [[nucleo-kernel]] dentro de [[espacio-de-kernel]].

## Explicación
[[modo-privilegiado]] explica en qué estado está el procesador, pero no explica qué pasa con cada instrucción concreta que intenta aprovechar ese estado. En [[modo-no-privilegiado]], el procesador revisa cada instrucción antes de ejecutarla: si el programa intenta leer o escribir fuera de su [[espacio-de-usuario]], tocar la zona del núcleo o dirigirse directamente a un dispositivo, la instrucción no llega a completarse, el procesador la detiene y transfiere el control al núcleo, que decide qué hacer con esa petición o con ese error. En [[modo-privilegiado]], en cambio, la misma instrucción completa su operación sin ese freno previo.

Esa diferencia es la definición operativa de instrucción privilegiada (privileged instruction). El procesador no la prohíbe por su contenido en sí, sino por el estado en el que se encuentra al intentarla ejecutarla. Por eso el conjunto concreto de instrucciones privilegiadas varía de una arquitectura a otra, pero su función es siempre la misma: reservar al núcleo la posibilidad de tocar lo que un programa ordinario no debe tocar.

Las instrucciones privilegiadas se agrupan por el tipo de control que ejercen. Unas dan acceso directo al hardware, es decir, permiten enviar órdenes a los dispositivos sin pasar por el núcleo. Otras permiten modificar las estructuras que protegen la memoria, como las tablas que traducen direcciones, de modo que quien las ejecuta puede alterar qué direcciones ve cada programa. Y otras permiten actuar sobre el propio procesador, como detenerlo, cambiar su estado de privilegio o preparar la respuesta a una señal externa. En todos los casos, la condición es idéntica: si el procesador está en [[modo-no-privilegiado]], la instrucción es rechazada; si está en [[modo-privilegiado]], se ejecuta.

Esta reserva explica también por qué el núcleo no puede sustituirse por un programa ordinario, aunque ambos sean instrucciones. Un programa de usuario puede pedir un servicio mediante una [[llamadas-al-sistema]], y el procesador cambia entonces a [[modo-privilegiado]] para ejecutar ese servicio, pero el programa no adquiere por ello la facultad de ejecutar instrucciones privilegiadas por su cuenta. Solo el código que el núcleo autoriza a correr en [[modo-privilegiado]] conserva esa facultad, y lo hace precisamente porque el procesador comprueba el estado antes de cada instrucción.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[modo-privilegiado]] se pasa del estado a la instrucción que lo aprovecha. Saber que el procesador puede estar en modo privilegiado o no explica la existencia de la separación entre [[espacio-de-usuario]] y [[espacio-de-kernel]], pero no dice qué ocurre cuando un programa concreto intenta cruzar esa separación con una instrucción concreta. Este peldaño añade esa comprobación: el procesador no confía en el programa y verifica el estado en cada instrucción privilegiada, de modo que el privilegio se concede o se niega una instrucción cada vez. No se introduce un peldaño siguiente, porque con [[modo-privilegiado]] y esta nota queda cerrado el recorrido del estado y de las instrucciones que lo requieren: ahora está claro en qué estado trabaja quien puede tocar el hardware y qué instrucciones solo ese estado habilita.

## Límites de esta explicación
Esta nota no explica qué registros guarda el estado de privilegio ni cómo el procesador los consulta antes de cada instrucción; esa parte de detalle pertenece a los registros y a la unidad de control, y no se trata aquí. Tampoco cataloga las instrucciones privilegiadas de una arquitectura concreta, materia propia de cada manual de arquitectura, ni el recorrido completo de una petición desde el programa hasta el núcleo, materia de [[llamadas-al-sistema]], ni la suspensión del programa ante una señal del hardware, materia de [[interrupciones]].

## Referencias
- [FTE-0001]: distinción entre instrucciones ordinarias y privilegiadas, y rechazo de estas últimas en modo de usuario.
- [FTE-0002]: concepto de modo protegido, restricciones del modo de usuario y reserva al núcleo de las instrucciones de control del hardware y de la memoria.
