---
titulo: "Autenticación"
slug: autenticacion
rama: software
categoria: sistema
nivel: 7
prerequisitos: [credenciales]
conduce_a: []
alias: ["autenticación de usuario", "authentication"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Autenticación

## Idea central
La autenticación es el contraste entre la identidad que una persona presenta y el registro que el [[sistema-operativo]] tiene de esa identidad. Sin ese contraste, cualquier persona ante el teclado podría actuar como cualquier [[usuario-de-sistema]] y apropiarse de sus derechos.

## Antes de empezar
- [[credenciales]]: la prueba concreta —un nombre de usuario acompañado de una contraseña, u otra prueba equivalente— que una persona presenta para demostrar que es quien dice ser, distinta de la propia identidad registrada.

## Explicación
El [[usuario-de-sistema]] define la identidad y el [[registro-de-usuarios]] la guarda de forma persistente, pero ninguna de esas dos notas dice por qué se puede confiar en quien se sienta ante el teclado para actuar en nombre de esa cuenta. Para eso existe un paso previo a cualquier acción: comprobar que quien solicita entrar en el sistema es realmente quien dice ser. Ese paso es la autenticación, y se basa en un contraste: lo que la persona presenta se compara con lo que el registro tiene guardado para esa cuenta, y solo si coincide se le atribuyen los derechos de la cuenta.

Que el contraste sea local o remoto cambia qué hay que tener en cuenta, no su fundamento. En el caso local, el ordenador en el que se trabaja es el mismo que conserva el registro, de modo que al iniciar sesión el sistema consulta su propio registro y decide sin necesidad de salir de la máquina. En el caso remoto, la cuenta está en otro ordenador. Entonces la prueba —las [[credenciales]]— viaja por la red hasta el servidor que custodia el registro, o el servidor actúa en nombre de un cliente; en ambos casos, además de contrastar la prueba, hay que cuidar el transporte, porque una prueba que viaja en claro puede ser interceptada o una cuenta remota puede ser suplantada por un impostor que se hace pasar por el servidor esperado. Por eso la autenticación remota no se reduce a comparar datos, sino que se acompaña de la protección del canal, tratada en [[seguridad-aplicacion-con-red]] y supuesta por cualquier [[aplicacion-con-red]].

La autenticación tiene un límite claro: no dice qué puede hacer la cuenta una vez que ha entrado, solo dice si la persona es quien dice ser. Una vez superada, el sistema atribuye a cada proceso lanzado los derechos de la cuenta autenticada y, a partir de ahí, son las reglas de [[permisos-de-archivos]] las que deciden qué archivos puede leer o escribir en cada caso. Confundir autenticar con autorizar rompería esa separación: autenticar responde a la pregunta por la identidad, autorizar responde a la pregunta por los derechos.

## Cómo se conecta con lo anterior y lo siguiente
Las [[credenciales]] proporcionaban la prueba; esta nota explica el contraste con el registro y por qué el resultado de ese contraste decide a qué cuenta se atribuyen los actos siguientes. No tiene un `conduce_a` previsto en el contrato: el detalle de cómo se conceden los derechos una vez autenticada la cuenta pertenece a [[permisos-de-archivos]] y a [[registro-de-usuarios]].

## Límites de esta explicación
Esta nota no entra en cómo el sistema guarda y protege las [[credenciales]] en el registro, es decir, en la custodia de la prueba, que pertenece a la nota de credenciales. Tampoco entra en cómo el sistema concede los derechos una vez autenticada la cuenta, tratado en [[permisos-de-archivos]] y [[registro-de-usuarios]], ni en la protección del canal de red, que se trata en [[seguridad-aplicacion-con-red]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): protección de un sistema operativo basada en la identidad de usuario y en la comprobación de quién actúa en nombre de cada cuenta.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): cuentas de usuario y su contrastación como base del modelo de protección en sistemas tipo Unix.
