---
titulo: "Sincronización de hilos"
slug: sincronizacion-de-hilos
rama: software
categoria: sistema
nivel: 9
prerequisitos: [hilos-concurrencia]
conduce_a: []
alias: ["sincronización", "synchronization", "coordinación de hilos"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Sincronización de hilos

## Idea central
La sincronización de hilos son las reglas que coordinan a los hilos de un mismo proceso cuando comparten memoria, de modo que lo que uno escribe no sea sobrescrito ni leído a medias por otro. Su mecanismo central es la exclusión mutua: garantizar que solo un hilo acceda a la vez a un dato compartido.

## Antes de empezar
- [[hilos-concurrencia]]: varios flujos de ejecución dentro de un [[proceso]], que comparten código, [[memoria-ram]] asignada y recursos, pero avanzan cada uno por separado con su propia [[pila]] y su propio punto de ejecución.

## Explicación
En [[hilos-concurrencia]] se estableció que los hilos de un proceso comparten memoria. Esa compartición es útil porque permite repartir el trabajo, pero también introduce un problema: si dos hilos modifican el mismo dato a la vez, el resultado final depende de cuál acabe antes, y ese resultado puede ser incorrecto. A esa dependencia no deseada del orden de ejecución se la llama condición de carrera: un fallo que no aparece siempre, sino solo cuando los hilos se intercalan en un orden concreto.

La sincronización resuelve ese problema imponiendo orden donde antes había intercalación libre. El caso básico es la región crítica: el tramo de código que accede a un dato compartido y que solo puede ejecutar un hilo en cada momento. La exclusión mutua establece exactamente eso, que en cualquier instante solo un hilo esté en la región crítica de un dato dado, aunque los demás hilos sigan ejecutándose fuera de ella.

Para conseguirla, los sistemas ofrecen mecanismos de cerrojo. Un cerrojo de exclusión mutua concede el acceso a un único hilo y bloquea a los demás hasta que lo libera; el hilo que lo solicita queda en espera, y el [[planificador]] pasa el [[procesador]] a otro hilo mientras tanto. El semáforo generaliza esa idea con un contador: permite un número fijado de accesos simultáneos y bloquea el exceso. Las variables de condición completan el repertorio y responden a otra necesidad, la de esperar un hecho concreto, no solo de excluir: un hilo puede esperar hasta que otro hilo le avise de que la condición que aguardaba se ha hecho verdadera.

Conviene distinguir excluir de coordinar. Excluir evita el acceso simultáneo; coordinar ordena el avance, por ejemplo haciendo que un hilo que produce un resultado se detenga hasta que otro hilo lo consume. Ambos problemas nacen de la misma causa, varios hilos compartiendo memoria, y ambos se resuelven con los mismos mecanismos, combinando cerrojos para excluir y esperas con aviso para ordenar.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[hilos-concurrencia]] se sabía que los hilos comparten memoria y que el [[planificador]] intercala sus turnos. Esta nota da el paso inmediato siguiente: si comparten memoria, necesitan reglas para no pisarse, y esas reglas son la exclusión mutua mediante cerrojos y la coordinación mediante espera y aviso. Queda así cerrado el problema de la concurrencia dentro de un proceso; qué ocurre cuando los que compiten son procesos distintos queda fuera de este peldaño.

## Límites de esta explicación
Esta nota no trata la organización de varios procesos a la vez; eso corresponde a [[multitarea]]. Tampoco detalla la implementación interna de los cerrojos, qué hace el núcleo o el hardware cuando un hilo se bloquea, ni los fallos que pueden surgir si la sincronización se usa mal, como que dos hilos esperen cada uno lo que tiene el otro o que un hilo no llegue a ejecutarse nunca. Esos temas requieren notas propias posteriores.

## Referencias
- FTE-0001 (OSTEP): hilos que comparten memoria, condición de carrera por accesos concurrentes a datos compartidos, exclusión mutua y mecanismos de cerrojo y semáforo.
- FTE-0002 (Tanenbaum, *Modern Operating Systems*): distinción entre proceso e hilo, necesidad de sincronización cuando los hilos comparten memoria y mecanismos de exclusión mutua y espera coordinada.
