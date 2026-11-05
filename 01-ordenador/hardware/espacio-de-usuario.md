---
titulo: "Espacio de usuario"
slug: espacio-de-usuario
rama: software
categoria: sistema
nivel: 8
prerequisitos: [memoria-virtual]
conduce_a: []
alias: ["espacio de usuario", "user space"]
estado: borrador
fuentes: []
---

# Espacio de usuario

## Idea central
El espacio de usuario es la parte del espacio de direcciones virtuales reservada a los programas ordinarios. Es la zona en la que trabaja cualquier programa cuando se ejecuta, sin acceso directo al control del ordenador: para tocar recursos protegidos debe pedir permiso al núcleo.

## Antes de empezar
- [[memoria-virtual]]: la abstracción con la que el sistema operativo da a cada programa un espacio amplio, ordenado y privado, en lugar de porciones sueltas de memoria física.
- [[proceso]]: un programa en ejecución, con sus instrucciones y sus datos; es quien habita este espacio.
- [[nucleo-kernel]]: el centro siempre activo del sistema operativo, que trabaja en la otra zona del espacio, la privilegiada.

## Explicación
El espacio de direcciones que ve un programa no es un bloque único y homogéneo. El sistema lo divide en dos partes con distinto nivel de privilegio. Una de ellas es el espacio de usuario (user space, en inglés), la que ocupa la mayor parte de ese espacio y la única en la que un programa ordinario puede leer e instrucciones y datos propios.

Estar en el espacio de usuario significa trabajar sin privilegios especiales. El programa solo puede acceder a su propia porción de memoria, no a la de otros programas, y no puede tocar directamente las estructuras internas que el núcleo usa para gobernar el ordenador. Si intenta alcanzar una dirección fuera de su parte autorizada, el sistema lo detiene: el hardware no le entrega un acceso físico, le entrega una denegación.

Esa limitación no lo deja aislado del resto del ordenador. Cuando un programa necesita un servicio que solo el núcleo puede ofrecer, no entra por su cuenta en la zona privilegiada; se lo solicita, mediante mecanismos tratados en [[llamadas-al-sistema]]. Mientras tanto, el núcleo resuelve el pedido en su propio espacio y devuelve el resultado al programa, que nunca sale del suyo.

Cada proceso posee su propio espacio de usuario, independiente de los demás: dos programas pueden usar las mismas direcciones virtuales sin pisarse, porque cada uno vive en su espacio y el sistema dirige cada pedido a lugares distintos, como ya se vio en [[memoria-virtual]].

## Cómo se conecta con lo anterior y lo siguiente
Desde [[memoria-virtual]] se pasa de la idea de un espacio privado y amplio por programa a la división interna de ese espacio según el privilegio. El espacio de usuario es la mitad no privilegiada de esa división: la zona donde vive y trabaja todo proceso ordinario. La otra mitad, donde trabaja el núcleo con acceso completo al hardware, se trata en [[espacio-de-kernel]]; los mecanismos concretos que separan y traducen ambas zonas se estudian en [[paginacion]].

## Límites de esta explicación
Esta nota no explica la zona privilegiada ni por qué sus datos están fuera del alcance ordinario; eso se trata en [[espacio-de-kernel]]. Tampoco explica cómo se pide un servicio del núcleo desde un programa, materia de [[llamadas-al-sistema]], ni cómo se dividen y traducen las direcciones en la práctica, materia de [[paginacion]] y [[segmentacion]].

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
