---
titulo: "Pantalla táctil"
slug: pantalla-tactil
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [dispositivo-movil]
conduce_a: []
alias: ["pantalla táctil", "touchscreen"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Pantalla táctil

## Idea central
La pantalla táctil (touchscreen) es la superficie que a la vez muestra la imagen de una [[aplicacion-movil]] y detecta el contacto del dedo sobre ella. Lo que esta nota explica no es el componente físico que genera esa detección, sino su consecuencia en la interacción: la entrada deja de ser un puntero movido por otro dispositivo y pasa a producirse directamente sobre los elementos visibles.

## Antes de empezar
- [[dispositivo-movil]]: equipo portátil de uso con una o dos manos, dedicado a la aplicación y a la entrada táctil.

## Explicación
En una interfaz gráfica de escritorio, tal como se describe en [[aplicacion-grafica]], la persona actúa sobre [[widget|widgets]] mediante un puntero desplazado con ratón o teclado: primero se mueve el puntero hasta el elemento y después se confirma la acción. En la pantalla táctil el dedo sustituye esa mediación. La posición del contacto sobre la pantalla es a la vez la posición del puntero, de modo que lo visible y lo accionable coinciden: pulsar el botón equivale a tocar el sitio donde el botón se ve.

Eso convierte el contacto en la unidad básica de entrada. Un toque breve y puntual funciona como clic o confirmación. Un contacto mantenida y desplazada funciona como arrastre: desplaza un contenido, mueve un objeto o revela elementos fuera de la vista. La pantalla móvil entrega posiciones y desplazamientos con una precisión gruesa — el dedo cubre una zona mayor que un puntero —, por lo que los elementos deben ser amplios y las acciones deben tolerar esa imprecisión. En [[aplicacion-movil]] ya se anticipaba este cambio: no es un detalle estético, sino otro modo de entrada, con otra precisión y otros límites.

Los gestos son secuencias de contactos que la aplicación interpreta como una sola orden. El gesto de ampliar o reducir con dos dedos a la vez, por ejemplo, se lee como una intención de cambiar la escala de lo mostrado, aunque físicamente sean dos contactos que se acercan o se alejan. La aplicación no recibe «dos dedos» como tales, sino una serie de [[eventos-de-interfaz|eventos]] con posición y tiempo; su [[manejador-de-eventos|manejador]] combina esos eventos para reconocer el gesto y traducirlo en la acción correspondiente, del mismo modo que un clic se reconoce como clic y no como «un evento de ratón».

La pantalla táctil también fusiona salida e entrada en un mismo sitio. A diferencia de un teclado, que ocupa un dispositivo separado del monitor, aquí la imagen mostrada es el propio control: editar, avanzar, retroceder o seleccionar se hace sobre lo que se está viendo. Esa fusión es lo que hace natural la interacción directa, pero también elimina la confirmación visual del polo del puntero y obliga a diseñar la [[interfaz-grafica-de-usuario|interfaz]] para dedos y no para puntero.

Todo ello llega a la aplicación ya interpretado por el [[sistema-operativo]], que recibe la información del componente a través de sus [[controladores-drivers|controladores]] y la pone a disposición de la aplicación como eventos. La aplicación no consulta directamente el hardware: recibe el resultado de contactos y posiciones y los asocia a los elementos que él mismo ha dibujado. El detalle de cómo se produce ese resultado — qué magnitud física se mide y cómo se convierte en posición — queda fuera de esta nota.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[dispositivo-movil]] se desciende aquí al rasgo que lo distingue de un ordenador de escritorio: la entrada directa sobre la pantalla. Lo anterior —la aplicación que se apoya en el sistema sin acceder al hardware— se mantiene: la aplicación móvil sigue sin gestionar directamente la pantalla, solo recibe sus contactos a través del sistema operativo. La nota es terminal: no conduce a un siguiente peldaño, porque el principio físico de la detección, que sería el paso siguiente hacia el hardware, pertenece a una nota aún no registrada.

## Límites de esta explicación
Esta nota no explica cómo funciona físicamente la detección del contacto ni el sensor que la produce, que son conceptos nuevos aún no registrados y deberán tratarse en notas de hardware posteriores. Tampoco trata la entrada con puntero de escritorio, que corresponde a [[aplicacion-grafica]]. Aquí «sensor» se entiende solo en una línea: componente que capta una magnitud física y la convierte en dato digital utilizable por el programa.

## Referencias
- FTE-0001: respalda que la aplicación accede al hardware a través del sistema y su núcleo. No cubre específicamente la entrada táctil ni los gestos.
- FTE-0002: respalda la misma separación entre programa de usuario y gestión del hardware por el sistema. Tampoco es específica de pantallas táctiles.
