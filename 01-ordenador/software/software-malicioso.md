---
titulo: "Software malicioso"
slug: software-malicioso
rama: software
categoria: malicioso
nivel: 2
prerequisitos: [software]
conduce_a: [malware, vulnerabilidades, exploits, defensa-malware]
alias: ["software malicioso", "malware"]
estado: borrador
fuentes: []
---

# Software malicioso

## Idea central
El software malicioso es el software introducido o incluido intencionadamente en un sistema con un fin perjudicial: afecta a la confidencialidad, la integridad o la disponibilidad de la información o del propio equipo. No es un tipo de programa distinto en su construcción; es software ordinario —instrucciones que el procesador puede ejecutar— usado sin autorización y contra los intereses de quien lo ejecuta.

## Antes de empezar
- [[software]]: qué es el software y sus cuatro grupos.
- [[software-de-sistema]]: el sistema operativo y sus controles de acceso, porque el software malicioso los elude o los aprovecha.

## Explicación
Parte de la misma base que todo [[software]]: instrucciones y datos que el hardware ejecuta. La diferencia no está en el lenguaje ni en el formato del archivo, sino en la intención y en la falta de autorización. Un programa que cifra los archivos de un usuario y después exige dinero para entregar la clave de descifrado, otro que recoge pulsaciones de teclado y las envía a un tercero, y otro que se disfraza de instalador legítimo comparten esa condición: fueron creados para producir un efecto nocivo no consentido por la persona propietaria del sistema.

La clasificación técnica habitual no es una lista de cajas excluyentes, sino tres preguntas que pueden hacerse sobre un mismo programa. Por el modo de propagación, un virus (virus) necesita un programa o archivo anfitrión que lo active, mientras que un gusano (worm) se propaga por la red por sí mismo; un troyano (trojan horse) se presenta como algo útil o inofensivo y solo al ejecutarse revela su función oculta. Por el modo de ocultarse y permanecer, un programa espía (spyware) se instala de forma secreta para recoger información, y un kit de raíz (rootkit) trata de esconderse de las herramientas del propio sistema. Por el objetivo, un programa de rescate (ransomware) bloquea el acceso a los datos hasta que se paga, y una red de zombis (botnet) reúne muchos equipos infectados para que sean controlados a distancia. Un mismo specimen puede ser troyano, espía y parte de una red de zombis a la vez; por eso el detalle por tipos pertenece a [[malware]].

Conviene distinguir tres conceptos que a menudo se mezclan. Una vulnerabilidad es un defecto del software —un error de programación, un permiso excesivo, una configuración insegura— que hace posible un uso no previsto. Un exploit es el programa o técnica que aprovecha en concreto esa vulnerabilidad. El software malicioso es el programa que, tras entrar, persigue su objetivo: robar, espiar, cifrar o dañar. No todo exploit instala malware, y no todo malware necesita un exploit sofisticado: a veces basta con engañar a la persona usuaria para que ejecute un troyano. El detalle de los defectos y de su aprovechamiento se trata en [[vulnerabilidades]] y [[exploits]].

Desde el punto de vista defensivo, la panorama es simétrica a la ofensiva: si el riesgo viene de ejecutar código no autorizado o de aprovechar permisos amplios y errores sin corregir, la defensa consiste en ejecutar solo código de confianza, conceder el mínimo privilegio necesario, mantener el software actualizado y disponer de copias de seguridad separadas del sistema principal. Cómo se organizan esas medidas —detección, prevención, respuesta— se trata en [[defensa-malware]].

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software]] se llega aquí por la cuarta rama de su clasificación: no todo software existe para cumplir una tarea útil del usuario. El paso siguiente es bajar un nivel y ver con detalle cómo se clasifican y comportan los programas concretos en [[malware]], para después separar las dos piezas que lo hacen posible —la [[vulnerabilidades]] y el [[exploits]] que la aprovecha— y cerrar con la [[defensa-malware]].

## Límites de esta explicación
Esta nota no describe cómo funciona por dentro cada tipo de malware, no explica vulnerabilidades concretas ni cómo se construyen exploits, y no detalla técnicas de defensa. Esas materias corresponden a [[malware]], [[vulnerabilidades]], [[exploits]] y [[defensa-malware]], respectivamente. Tampoco trata la autoría, la motivación económica o penal de quien lo crea, ni los programas no deseados que no son estrictamente dañinos.

## Referencias
Sin referencias registradas aún en `_registro/fuentes.md`. Las fuentes consultadas para redactar esta nota se proponen en la entrega para su registro con ID estable; hasta entonces, ninguna afirmación debe darse por respaldada en el registro del libro.
