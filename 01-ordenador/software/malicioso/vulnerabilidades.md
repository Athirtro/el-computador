---
titulo: "Vulnerabilidades"
slug: vulnerabilidades
rama: software
categoria: malicioso
nivel: 3
prerequisitos: [software-malicioso]
conduce_a: [exploits]
alias: ["vulnerabilidad", "vulnerability"]
estado: borrador
fuentes: []
---

# Vulnerabilidades

## Idea central
Una vulnerabilidad es un defecto de un programa, de su configuración o de la forma en que se concede acceso a sus recursos que permite un uso distinto del previsto por quien lo diseñó. Por sí sola no ataca a nadie: es la condición que hace posible el ataque. Importa porque separa el fallo del aprovechamiento y explica por qué el mismo programa puede ser seguro en un contexto y expuesto en otro.

## Antes de empezar
- [[software-malicioso]]: distinción entre el programa dañino, el defecto que lo hace posible y la técnica que lo aprovecha.

## Explicación
Toda vulnerabilidad presupone lo mismo que presupone cualquier [[software]]: instrucciones que el procesador ejecuta y recursos —datos, archivos, dispositivos, privilegios— sobre los que esas instrucciones operan. El defecto aparece cuando el programa no controla como debería una de esas dos cosas. Puede tratarse de un error de programación, como aceptar una entrada sin comprobar que respeta el formato esperado y dejar así que quien la envía altere el comportamiento del programa; de un diseño con privilegios excesivos, cuando el programa concede a quien lo usa más capacidad de la necesaria para su tarea; o de una configuración insegura, cuando el programa es correcto en su código pero se instala con opciones por defecto que lo dejan expuesto. A esas causas se suma la gestión: un programa que en su momento fue correcto puede volverse vulnerable cuando se descubre un error en él y no se corrige, o cuando se mantiene en uso una versión antigua que ya no recibe correcciones.

De este origen se sigue una consecuencia práctica: la vulnerabilidad no es una propiedad absoluta del programa, sino una relación entre el defecto, el contexto de uso y lo que un tercero puede alcanzar. Un mismo error puede no tener efecto si la parte defectuosa nunca recibe entradas de fuera, y ser grave si el programa está expuesto a la red. Por eso su importancia depende de tres factores juntos: si el defecto es alcanzable por alguien no autorizado, qué privilegios obtiene quien lo alcanza y qué puede hacer con ellos sobre la confidencialidad, la integridad o la disponibilidad de la información. No basta con saber que existe un defecto; hace falta saber dónde está el programa, quién puede llegar a él y con qué permisos.

Conviene fijar con precisión las tres piezas que [[software-malicioso]] anunció. La vulnerabilidad es el defecto. El programa o técnica que lo aprovecha en concreto es el exploit, y pertenece ya a [[exploits]]. El software que, después de entrar, persigue su objetivo —robar datos, espiar, cifrar archivos— es el [[malware]]. Las tres piezas son independientes: puede existir una vulnerabilidad que nadie ha aprovechado todavía, puede haber un exploit que no instala malware sino que solo demuestra el fallo, y puede haber malware que no necesita ningún exploit porque se limita a engañar a la persona usuaria para que lo ejecute. Confundirlas lleva a buscar la defensa en el lugar equivocado: corregir el defecto elimina la vulnerabilidad aunque el exploit ya haya circulado, y eliminar un programa concreto no corrige los demás que comparten el mismo defecto.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-malicioso]] se llega aquí bajando un nivel: aquel panorama definió la vulnerabilidad en una sola línea como el defecto que permite un uso no previsto, y esta nota desarrolla exactamente esa línea. El paso siguiente es [[exploits]], donde el defecto deja de ser una descripción y se convierte en un aprovechamiento concreto, con su técnica y sus condiciones de éxito.

## Límites de esta explicación
Esta nota no describe cómo se construyen ni cómo funcionan los exploits, materia de [[exploits]]; no clasifica los programas dañinos concretos, materia de [[malware]]; ni detalla las medidas para corregir defectos o reducir la exposición, materia de [[defensa-malware]]. Tampoco ofrece ejemplos de productos concretos ni un catálogo formal de defectos conocidos.

## Referencias
Sin referencias registradas aún en `_registro/fuentes.md`. Las fuentes consultadas para redactar esta nota se proponen en la entrega para su registro con ID estable; hasta entonces, ninguna afirmación debe darse por respaldada en el registro del libro.
