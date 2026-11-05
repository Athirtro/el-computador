---
titulo: "Multitarea preventiva"
slug: multitarea-preventiva
rama: software
categoria: sistema
nivel: 8
prerequisitos: [multitarea]
conduce_a: [interrupciones]
alias: ["multitarea preventiva", "preemptive multitasking"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Multitarea preventiva

## Idea central
La multitarea preventiva es la forma de multitarea en la que el núcleo retoma el control del procesador aunque el proceso en ejecución no ceda voluntariamente. Importa porque impide que un programa acapare el procesador y deje sin avanzar al resto de procesos.

## Antes de empezar
- [[multitarea]]: la propiedad de que varios procesos avanzan compartiendo los recursos de un mismo ordenador, aunque un único procesador solo pueda ejecutar una instrucción en cada instante.

## Explicación
En la multitarea cooperativa, el procesador cambia de proceso cuando el proceso en curso cede de forma voluntaria. Si un proceso nunca cede, ningún otro proceso listo puede avanzar, aunque esté esperando el procesador. La multitarea preventiva elimina esa dependencia de la buena voluntad del proceso en curso.

El mecanismo es la interrupción forzada. Una señal generada por el hardware interrumpe la ejecución del proceso en curso y entrega el control al núcleo, es decir, al [[nucleo-kernel]], que pasa a ejecutarse con [[modo-privilegiado]]. El proceso interrumpido no puede negarse a esa retirada, porque la interrupción no es una petición que él pueda ignorar: es el hardware quien suspende su ejecución y cede el control. El detalle de cómo se genera y se atiende esa señal corresponde a [[interrupciones]].

Una vez en el núcleo, el [[planificador]] decide qué proceso listo ocupará el procesador a continuación. Si es otro proceso, el núcleo realiza un [[cambio-de-contexto]]: guarda el estado del proceso interrumpido y carga el estado del proceso elegido, de modo que este último pueda continuar su ejecución. Cuando el proceso interrumpido vuelva a ser elegido, se restaurará su estado y seguirá donde lo dejó, como si nadie lo hubiera detenido.

La multitarea preventiva protege así el avance del resto de procesos frente a un programa que no cede, y permite que los programas interactivos reciban procesador aunque haya procesos de cálculo que nunca se detengan voluntariamente. Su coste es que cada interrupción forzada obliga a guardar y restaurar estado, con el consiguiente tiempo perdido en el propio cambio de proceso.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[multitarea]] se pasa del efecto general de que varios procesos avanzan a la vez a la forma en que ese avance puede forzarse sin cooperación del proceso en curso. La multitarea preventiva es el peldaño ineludible entre la idea de alternar procesos y el mecanismo hardware que hace posible esa alternación forzada: sin interrupciones, el núcleo no podría retomar el control de un proceso que no cede, y la preventiva quedaría sin fundamento. Por eso el siguiente paso es [[interrupciones]], que explica la señal hardware que suspende la ejecución y cede el control al núcleo.

## Límites de esta explicación
Esta nota no trata la multitarea cooperativa, en la que cada proceso cede el procesador de forma voluntaria; eso corresponde a [[multitarea-cooperativa]]. Tampoco trata cómo el planificador ordena a los procesos listos ni con qué criterios elige entre ellos; eso corresponde a [[planificador]]. El detalle de guardar y restaurar el estado de cada proceso en un cambio corresponde a [[cambio-de-contexto]], y el de la señal hardware que interrumpe la ejecución, a [[interrupciones]].

## Referencias
- FTE-0001: Operating Systems: Three Easy Pieces, de Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau. Respalda la multitarea preventiva como control forzado del núcleo sobre el proceso en ejecución y el cambio de proceso asociado.
- FTE-0002: Modern Operating Systems, 4th Edition, de Andrew S. Tanenbaum (4ª ed. con Herbert Bos). Respalda la distinción entre multitarea cooperativa y preventiva y el papel del núcleo en retomar el procesador frente a procesos que no ceden.
