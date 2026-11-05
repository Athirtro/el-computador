---
titulo: "Gestión de recursos"
slug: gestion-de-recursos
rama: software
categoria: sistema
nivel: 5
prerequisitos: [nucleo-kernel]
conduce_a: [gestor-de-procesos, gestor-de-memoria]
alias: ["gestión de recursos", "resource management"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Gestión de recursos

## Idea central
La gestión de recursos es la parte de la actividad del [[nucleo-kernel]] que decide qué programa usa cada recurso del ordenador, en qué momento y durante cuánto tiempo. Existe porque los recursos son limitados y varios programas los solicitan a la vez; sin reparto ordenado, un programa podría impedir que los demás funcionaran.

## Antes de empezar
- [[nucleo-kernel]]: el centro siempre activo del [[sistema-operativo]] que controla directamente el [[hardware]] y coordina los recursos.

## Explicación
Un recurso es cualquier elemento del equipo que los programas necesitan para trabajar y que no puede atender a todos a la vez sin coordinación: el tiempo de [[procesador]], la capacidad de la [[memoria-ram]] y el uso de un dispositivo conectado. La gestión de recursos sigue siempre el mismo ciclo. Un programa solicita un recurso; el núcleo comprueba si está libre, si puede compartirse o si hay que esperar; lo asigna al solicitante; y, cuando el programa lo deja de necesitar o termina, lo recupera para ponerlo a disposición de la siguiente petición. La nota siguiente a esta describe qué forma toma ese ciclo para cada tipo de recurso, pero el esquema general es uno solo.

La necesidad de ordenar desde el principio no es solo repartir fragmentos. Hay recursos que exigen uso exclusivo en cada instante, como un dispositivo que solo puede escribir en un momento dado, y recursos que pueden compartirse dividiendo el tiempo, como el procesador entre varios programas. Entre ambos extremos se sitúan decisiones de espera: un programa que ha solicitado un recurso ocupado no desaparece, sino que queda apartado hasta que el núcleo se lo conceda. Si el núcleo lo conservara permanentemente, el ordenador seguiría funcionando para los demás pero ese programa no avanzaría nunca.

Por eso la gestión no se limita a conceder según el orden de llegada. El núcleo aplica criterios de prioridad, entendiendo por prioridad la preferencia que concede a una petición frente a otra cuando no puede atenderlas todas. Dicha preferencia puede atender a la importancia declarada de la tarea, al tiempo que lleva esperando o a la necesidad de que todas las peticiones reciban servicio en algún momento, y no solo las primeras. Un criterio mal aplicado puede producir el efecto contrario al deseado: si las peticiones nuevas aventajan siempre a las antiguas, alguna podría quedar indefinidamente sin recurso. Del mismo modo, conceder un recurso a un programa que no lo utilizará enseguida bloquea a quien sí podría avanzar. Gestionar es, en consecuencia, equilibrar cuatro exigencias a la vez —que el recurso se aproveche, que se respete la preferencia establecida, que nadie quede esperando para siempre y que un programa no retenga lo que otros necesitan—.

Ese equilibrio se ejerce sobre los tres tipos de recursos mencionados. Sobre el procesador, decidir a qué programa corresponde cada turno de ejecución. Sobre la memoria, decidir cuánto espacio tiene disponible cada programa mientras trabaja. Sobre los dispositivos, decidir quién puede usar cada uno y en qué orden. En los tres casos, la decisión se toma antes de que el programa use efectivamente el recurso, y puede modificarse después si la situación de los demás solicitantes cambia.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[nucleo-kernel]] se pasa de la coordinación de recursos como función general a esta nota, que expone su ciclo común —solicitud, concesión, espera, uso y recuperación— y los criterios con los que se resuelven los conflictos entre solicitantes. El siguiente paso divide ese esquema en dos tareas especializadas: [[gestor-de-procesos]], que trata la asignación del procesador y la organización de los programas en ejecución, y [[gestor-de-memoria]], que trata la asignación de la memoria.

## Límites de esta explicación
Esta nota no detalla los mecanismos con que se asigna el procesador entre programas en ejecución ni los que reparten la memoria disponible; eso se trata en [[gestor-de-procesos]] y en [[gestor-de-memoria]], respectivamente, junto con la [[memoria-virtual]], la abstracción con que el sistema amplía el espacio disponible para cada programa. Tampoco explica cómo se comunica el núcleo con cada dispositivo concreto, tarea de los [[controladores-drivers]], ni los criterios de acceso reservado a zonas de memoria del sistema.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): ciclo de asignación de recursos y criterios de prioridad.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): ciclo de asignación de recursos y criterios de prioridad.
