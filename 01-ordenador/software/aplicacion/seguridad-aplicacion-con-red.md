---
titulo: "Seguridad en aplicación con red"
slug: seguridad-aplicacion-con-red
rama: software
categoria: aplicacion
nivel: 4
prerequisitos: [aplicacion-con-red]
conduce_a: []
alias: ["seguridad en aplicación de red", "seguridad en red a nivel de aplicación"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Seguridad en aplicación con red

## Idea central
Una aplicación con red intercambia datos con otros ordenadores, y ese intercambio mide el riesgo: los datos viajan fuera de un solo equipo y la aplicación debe comprobar con quién habla y proteger lo que envía y lo que recibe. La seguridad en este nivel consiste en autenticar al interlocutor y proteger los datos en tránsito, no en defender el equipo frente a programas dañinos.

## Antes de empezar
- [[aplicacion-con-red]]: la relación cliente-servidor, la dirección del equipo remoto y el protocolo común que la aplicación usa para solicitar y responder.

## Explicación
En [[aplicacion-con-red]], la aplicación local pide algo a un equipo remoto y ese equipo responde. En un ordenador aislado, el riesgo principal es que otra persona local use el equipo sin permiso; por eso el sistema mantiene cuentas y permisos, como se explica en [[usuario-de-sistema]] y [[permisos-de-archivos]]. Con red aparece un segundo riesgo: la aplicación ya no sabe con certeza si el equipo que contesta es el esperado, ni si los datos que viajan han sido leídos o modificados por terceros durante el trayecto. La seguridad de la aplicación con red nace de ese cambio de situación.

El primer problema es saber con quién se habla. La autenticación es el procedimiento por el que la aplicación comprueba la identidad de la otra parte antes de entregar datos sensibles o de aceptar sus respuestas como válidas. En la práctica, el cliente presenta una credencial —por ejemplo, un nombre de usuario acompañado de una contraseña— y el servidor la contrasta con lo que tiene registrado; el servidor, a su vez, puede tener que acreditar su identidad ante el cliente, para que este no envíe sus datos a un impostor. Sin autenticación, cualquier equipo que responda en la dirección esperada podría hacerse pasar por el servidor y obtener los datos que el cliente le envía.

El segundo problema es qué ocurre con los datos mientras viajan. La confidencialidad es la propiedad de que solo el destinatario pueda leer el contenido; la integridad es la propiedad de que nadie pueda alterarlo sin que se detecte. Para lograrlas se usa el cifrado: una transformación de los datos con una clave, de modo que quien no dispone de la clave obtiene un texto ilegible y no puede modificarlo sin que el destinatario lo note. La aplicación no cifra «el ordenador» ni «la red»; cifra el mensaje concreto que envía y descifra el que recibe, con las claves acordadas con su interlocutor.

Estos dos problemas se resuelven antes de entregar el resultado a la persona. Si el interlocutor no se autentica, la aplicación no debe enviarle datos sensibles ni atender sus peticiones como si fuera el cliente legítimo; si el mensaje recibido no supera la comprobación de integridad, la aplicación debe descartarlo en lugar de mostrarlo. De este modo, la seguridad se convierte en una condición del intercambio: la tarea de [[aplicacion-con-red]] solo se considera completada cuando la respuesta procede de quien decía ser y llega tal como fue enviada.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[aplicacion-con-red]] se desciende a este peldaño porque el intercambio cliente-servidor introduce dos preguntas que no existían en una aplicación local: quién es el interlocutor remoto y qué le ocurre a los datos durante el trayecto. El contrato de esta nota no le asigna un `conduce_a` posterior; queda como rama dentro del recorrido de aplicación, junto a [[aplicacion-con-red]] y [[aplicacion-grafica]], sin salto hacia el software de sistema ni hacia el software malicioso.

## Límites de esta explicación
Esta nota no desarrolla los mecanismos criptográficos concretos, ni los protocolos de red que los aplican, ni la seguridad del sistema operativo del equipo local. Tampoco trata la defensa frente a programas dañinos ni la detección y eliminación de malware; eso corresponde a [[defensa-malware]], sin entrar aquí en su detalle. No desarrolla además qué es una vulnerabilidad de una aplicación, tema que pertenece a [[vulnerabilidades]] dentro del software malicioso.

## Referencias
- [FTE-0001] *Operating Systems: Three Easy Pieces*: respaldo de la distinción entre cuentas de usuario y permisos en el sistema local, que sirve de contraste con la autenticación remota.
- [FTE-0002] *Modern Operating Systems*: respaldo de la función del sistema operativo como intermediario entre la aplicación y los servicios del equipo, frente a la comunicación con el equipo remoto.
