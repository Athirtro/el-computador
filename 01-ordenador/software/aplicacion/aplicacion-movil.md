---
titulo: "Aplicación móvil"
slug: aplicacion-movil
rama: software
categoria: aplicacion
nivel: 4
prerequisitos: [software-de-aplicacion]
conduce_a: []
alias: ["aplicación móvil", "mobile application", "app móvil"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Aplicación móvil

## Idea central
Una aplicación móvil (mobile application) es una [[software-de-aplicacion|aplicación]] diseñada para ejecutarse en un dispositivo móvil, es decir, un ordenador portátil de uso con una mano, con pantalla táctil y sensores integrados. Su rasgo distintivo no es la tarea que resuelve, sino el entorno físico y de interacción en el que la resuelve.

## Antes de empezar
- [[software-de-aplicacion]]: qué es una aplicación y en qué se distingue del software de sistema y del de programación.

## Explicación
Desde [[software-de-aplicacion]] se sabe que una aplicación traduce una intención del usuario en operaciones ejecutadas por el [[sistema-operativo]], sin gestionar directamente el hardware. Una aplicación móvil mantiene esa posición, pero el dispositivo al que se dirige condiciona su interfaz y su uso.

Un dispositivo móvil es un ordenador compacto y alimentado por batería que se sostiene y se maneja con una o dos manos. Se define en una línea por tres rasgos: pantalla táctil, sensores integrados y conectividad permanente. La pantalla táctil es la superficie que detecta el contacto del dedo y convierte su posición y sus movimientos en órdenes. El sensor es el componente que capta una magnitud física —posición, orientación, luz, proximidad o aceleración— y la convierte en un dato digital utilizable por el programa.

La entrada táctil cambia la relación entre persona y programa respecto a una aplicación de escritorio. En [[aplicacion-grafica]] la entrada se intermedia con un puntero movido por un ratón o un teclado; en la aplicación móvil el dedo actúa directamente sobre los elementos visibles. Eso hace centrales los gestos —tocar, desplazar, ampliar con dos dedos— y obliga a una interfaz pensada para dedos y para pantallas de menor tamaño, con controles grandes y pocas elementos a la vez. No es un detalle estético: es otro modo de entrada, con otra precisión y otros límites.

Los sensores y el hardware integrado amplían lo que la aplicación puede percibir sin que el usuario lo escriba. Una aplicación móvil puede reaccionar a que el dispositivo se mueve, cambia de orientación o se encuentra en un lugar determinado, porque recibe esos datos del sistema operativo. Como en el resto de aplicaciones, ella no accede directamente a esos componentes: los solicita al sistema, que los arbitra a través del [[nucleo-kernel]]. Además, al tratarse de un equipo alimentado por batería y de tamaño reducido, la aplicación móvil debe trabajar con recursos limitados y con consumo de energía acotado, lo que condiciona cuánto puede hacer en segundo plano y cuánto debe mostrar en pantalla.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-aplicacion]], que presenta la aplicación en general, se desciende aquí a una variante concreta: la que se ejecuta en un dispositivo móvil. El propósito sigue siendo el de cualquier aplicación —resolver una tarea del usuario apoyándose en el sistema—, pero la entrada táctil, los sensores y las restricciones del equipo portátil definen su forma. La nota es terminal: no conduce a un siguiente peldaño, porque el detalle de pantallas, sensores y sistemas operativos móviles pertenece a notas de hardware y de sistema aún no registradas.

## Límites de esta explicación
Esta nota no trata las aplicaciones de escritorio, cuya interfaz y forma de entrada se desarrollan en [[aplicacion-grafica]], ni las aplicaciones que acceden a la web, tratadas en [[aplicacion-con-red]] como vínculo. Tampoco explica cómo funcionan físicamente la pantalla táctil o los sensores, ni cómo es un sistema operativo móvil en detalle: son conceptos nuevos que el orquestador deberá registrar antes de enlazarlos. Por eso aquí se definen en una línea, sin desarrollarlos.

## Referencias
- FTE-0001: respalda la idea general de que la aplicación se apoya en los servicios del sistema operativo y del núcleo para acceder al hardware. No es una fuente específica de plataformas móviles.
- FTE-0002: respalda la misma separación entre programa de usuario y gestión del hardware por el sistema. Tampoco es específica de dispositivos móviles.
