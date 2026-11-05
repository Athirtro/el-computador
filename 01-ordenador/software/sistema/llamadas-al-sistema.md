---
titulo: "Llamadas al sistema"
slug: llamadas-al-sistema
rama: software
categoria: sistema
nivel: 6
prerequisitos: [nucleo-kernel]
conduce_a: [interrupciones]
alias: ["system calls"]
estado: borrador
fuentes: []
---

# Llamadas al sistema

## Idea central
Una llamada al sistema es la petición con la que un programa ordinario solicita al núcleo un servicio que no puede resolver por sí mismo. Es el camino ordenado por el que un programa se pone en contacto con el centro del sistema operativo en lugar de acceder directamente a los recursos.

## Antes de empezar
- [[nucleo-kernel]]: el componente del sistema operativo que permanece activo y controla directamente el hardware, coordinando el uso de los recursos por los programas.

## Explicación
El núcleo coordina los recursos, pero un programa no puede pedirle un servicio sin un mecanismo de petición definido. Ese mecanismo es la llamada al sistema (system calls): cada llamada comunica qué servicio se solicita y los datos necesarios para prestarlo, y el núcleo responde con el resultado o con la denegación de lo pedido. Ejemplos de servicios son leer o escribir un archivo, crear un proceso o solicitar memoria.

La petición tiene tres partes esenciales. Primero, un identificador del servicio solicitado, que indica al núcleo qué debe hacer. Segundo, los parámetros de la petición, es decir, los datos imprescindibles para esa tarea concreta. Tercero, el resultado que devuelve el núcleo al programa cuando termina, con el que el programa sabe si el servicio se prestó y, en su caso, qué se obtuvo. Sin esta estructura de petición y respuesta no habría intermediación: cada programa tendría que intentar acceder por su cuenta a los recursos.

La llamada marca además un cambio de responsabilidad. Hasta que se invoca, el programa actúa en su propio ámbito y no puede disponer de los recursos reservados al núcleo. Al invocarla, entrega el control al núcleo, que ejecuta el servicio con sus privilegios y, al terminar, devuelve el control al programa. Esa entrega y devolución ordenadas es lo que hace que la petición sea segura: el programa no salta por su cuenta a las zonas ni a las funciones del núcleo, sino que utiliza la única vía prevista para solicitarlas.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[nucleo-kernel]] se sabe que hay un centro siempre activo que controla los recursos y atiende las peticiones de los programas. Esta nota explica qué forma adopta una petición concreta cuando un programa necesita un servicio. El siguiente peldaño, [[interrupciones]], examina cómo se produce físicamente esa entrega del control entre el programa y el núcleo.

## Límites de esta explicación
Esta nota no explica el mecanismo hardware con el que se entrega el control al invocar una llamada, ni el detalle de las interrupciones que lo hacen posible; eso se trata en [[interrupciones]]. Tampoco enumera los servicios concretos que ofrece un sistema determinado ni las vías de programación que los exponen a los programas.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
