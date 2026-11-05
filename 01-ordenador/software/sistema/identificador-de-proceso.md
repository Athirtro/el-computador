---
titulo: "Identificador de proceso"
slug: identificador-de-proceso
rama: software
categoria: sistema
nivel: 7
prerequisitos: [proceso]
conduce_a: []
alias: ["identificador de proceso", "process identifier", "PID"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Identificador de proceso

## Idea central
El identificador de proceso (process identifier, PID) es un número que asigna el [[nucleo-kernel]] a cada [[proceso]] cuando lo crea, para distinguirlo sin ambigüedad de los demás procesos que existen a la vez. Sin ese nombre numérico, el núcleo y el resto del sistema no podrían referirse a una instancia concreta de ejecución, sino solo a «un programa en ejecución».

## Antes de empezar
- [[proceso]]: programa en ejecución con estado propio que puede interrumpirse y reanudarse; dos procesos pueden provenir del mismo programa y, aun así, ser instancias distintas.

## Explicación
Desde [[proceso]] ya se sabe que el código de un programa no basta para identificar una ejecución concreta: el mismo programa puede estar en ejecución varias veces a la vez, y cada una de esas ejecuciones tiene su propio avance y su propia memoria asignada. Si todas se llamaran solo por el nombre del programa, no habría forma de decir cuál de ellas se quiere detener, consultar o eliminar.

Para resolverlo, cuando el núcleo crea un proceso le asigna un identificador numérico, el PID. Ese número es único entre los procesos que existen en el mismo momento: dos procesos vivos nunca comparten el mismo identificador. Mientras un proceso vive, su identificador permanece ligado a esa instancia concreta, de modo que al referirse a él se sabe exactamente de cuál se habla, aunque comparta programa con otros.

El identificador no forma parte del programa que se ejecuta ni cambia lo que el programa hace; es una etiqueta que el núcleo pone por fuera para gestionar la instancia. Gracias a ella, el núcleo puede mantener ordenados los procesos que tiene activos, dirigirle a cada uno lo que le corresponde y distinguirlos cuando hay varios con el mismo origen. Es, en síntesis, el nombre que convierte una ejecución genérica en un objeto gestionable e identificable.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[proceso]] se definió el objeto gestionable: una ejecución con estado propio. Esta nota da el paso inmediato siguiente: explicar cómo se distingue ese objeto de los demás cuando hay varios a la vez. El identificador es el nombre numérico que recibe cada instancia, y esa unicidad entre procesos vivos es lo que permite hablar de un proceso concreto en lugar de hablar del programa del que procede.

## Límites de esta explicación
Esta nota no explica qué datos guarda el núcleo junto al identificador ni cómo se conserva el estado al interrumpir un proceso; eso se trata en [[bloque-de-control-de-proceso]]. Tampoco explica qué criterios usa el núcleo para decidir a qué proceso le toca ejecutarse después ni cómo se sustituye un proceso por otro en el [[procesador]]; eso corresponde a [[planificador]] y a [[cambio-de-contexto]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): proceso como programa en ejecución y necesidad de distinguir instancias.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): proceso como programa en ejecución con estado propio e identificación por el sistema.
