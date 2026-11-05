---
titulo: "Modo privilegiado"
slug: modo-privilegiado
rama: software
categoria: sistema
nivel: 8
prerequisitos: [espacio-de-kernel]
conduce_a: []
alias: ["modo privilegiado", "privileged mode", "modo kernel", "modo supervisor"]
estado: borrador
fuentes: [FTE-0001, FTE-0002, FTE-0004]
---

# Modo privilegiado

## Idea central
El modo privilegiado es el estado de ejecución en el que el procesador permite al programa en curso acceder sin permiso a toda la memoria y al hardware. Es el estado en el que trabaja [[nucleo-kernel]] dentro de [[espacio-de-kernel]], y no el estado ordinario de los programas de usuario.

## Antes de empezar
- [[espacio-de-kernel]]: la zona del espacio virtual reservada solo al núcleo, separada de la zona de los programas ordinarios.

## Explicación
El ordenador no otorga el mismo permiso a todo el programa que se ejecuta. La mayoría de los programas trabaja en modo no privilegiado, llamado también modo de usuario: solo puede entrar en su propio [[espacio-de-usuario]], y si intenta tocar la zona del núcleo o escribir directamente en un dispositivo, el procesador lo detiene y no le deja seguir. Esa primera limitación, que protege al sistema de los fallos y de la curiosidad de los programas ordinarios, ya quedó planteada en [[espacio-de-kernel]].

El modo privilegiado (privileged mode) es el estado contrario. Cuando el procesador está en este estado, el código en ejecución puede leer y escribir cualquier dirección de memoria, entrar en el [[espacio-de-kernel]], y enviar órdenes a los dispositivos sin que el procesador le ponga freno. No es un programa especial ni un lugar especial del disco: es una condición del procesador mientras ejecuta unas instrucciones concretas. Por eso el núcleo es el único programa que permanece en ese estado de forma estable, porque necesita revisar, repartir o proteger la memoria y hablar con el hardware en nombre de todos.

El procesador pasa de un modo a otro sin que el programa de usuario decida el paso. Cuando un programa necesita un servicio que solo el núcleo puede ofrecer en modo privilegiado, pide ayuda por un cauce controlado, como una [[llamadas-al-sistema]], y el procesador cambia a este estado, ejecuta el servicio dentro de [[espacio-de-kernel]] y, al terminar, vuelve al estado no privilegiado para devolver el control al programa. El programa no se ha trasladado a la zona del núcleo: solo ha solicitado el trabajo, ha esperado su término y ha recibido el resultado.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[espacio-de-kernel]] se pasa del dónde al en qué estado. El espacio reservado existe como zona, pero solo cobra sentido si el procesador distingue quién puede entrar en ella y quién no. Este peldaño aporta ese cómo sin entrar en los registros concretos: el procesador mantiene el estado de privilegio mientras ejecuta y lo cambia al entrar y al salir del servicio del núcleo. No se introduce un peldaño siguiente, porque con [[espacio-de-kernel]] y esta nota queda cerrado el recorrido de la separación entre zona de usuario y zona de núcleo: ahora está claro qué zona es privilegiada y en qué estado trabaja quien puede usarla.

## Límites de esta explicación
Esta nota no explica qué registros guarda el estado de privilegio ni cómo se cambia el bit que lo representa; esa parte de detalle pertenece a los registros y a la unidad de control, y no se trata aquí. Tampoco explica el recorrido completo de una petición desde el programa hasta el núcleo, materia de [[llamadas-al-sistema]], ni la suspensión del programa ante una señal del hardware, materia de [[interrupciones]]. La composición de la zona de usuario pertenece a [[espacio-de-usuario]].

## Referencias
- [FTE-0001]: distinción entre modo usuario y modo núcleo, y cambio ordenado de modo al invocar un servicio del sistema operativo.
- [FTE-0002]: concepto de modo protegido, restricciones del modo de usuario y salto al modo privilegiado del núcleo.
- [FTE-0004]: descripción del núcleo Linux como componente que trabaja con acceso completo al hardware y al espacio del núcleo.
