---
titulo: "Journaling"
slug: journaling
rama: software
categoria: sistema
nivel: 6
prerequisitos: [tipos-de-sistema-de-archivos]
conduce_a: []
alias: ["diario de cambios", "journaling"]
estado: borrador
fuentes: []
---

# Journaling

## Idea central
El journaling, o diario de cambios (journaling), es la técnica por la que un [[tipos-de-sistema-de-archivos|tipo de sistema de archivos]] escribe primero la descripción de cada cambio en una zona reservada y solo después lo aplica a su sitio definitivo. Así, tras un corte de corriente, el sistema puede rehacer o deshacer las operaciones incompletas y recuperar una organización de archivos consistente, en lugar de tener que reconstruirla desde cero.

## Antes de empezar
- [[tipos-de-sistema-de-archivos]]: cada tipo concreto de sistema de archivos, como ext4, NTFS o FAT32, organiza archivos y carpetas con sus propias reglas.
- [[sistema-de-archivos]]: la parte del sistema operativo que mantiene la información persistente como archivos con nombre y ruta.

## Explicación
El problema que resuelve nace de que escribir en un disco no es un acto único e instantáneo. Cuando un programa crea un archivo, amplía uno existente o lo borra, el sistema de archivos debe modificar a la vez los datos del usuario y los metadatos, es decir, la información del propio sistema sobre cada archivo: su tamaño, los bloques que ocupa, el directorio al que pertenece. Si la corriente se interrumpe en mitad de una de esas escrituras, el resultado puede quedar a medias: por ejemplo, un directorio puede apuntar a bloques que la tabla de asignación todavía marca como libres, o un archivo puede figurar con un tamaño que sus datos aún no tienen. La estructura queda entonces inconsistente, aunque el disco siga funcionando físicamente.

Sin diario, la única salida ante ese estado es una comprobación completa del sistema de archivos al arrancar: recorrer todas sus estructuras, compararlas entre sí y corregir lo que se pueda deducir. Ese recorrido es lento en discos grandes y tiene un límite fundamental: si una escritura ya ha empezado a sobrescribir el sitio definitivo de un dato y se corta antes de terminar, el dato original ya no existe, y ninguna comprobación posterior puede reconstruirlo. La reparación detecta la inconsistencia, pero no siempre puede deshacer el daño.

El diario de cambios evita ese callejón sin salida alterando el orden de las escrituras. Antes de tocar el sitio definitivo de un cambio, el sistema anota en una zona reservada del disco qué se va a modificar y qué valores antiguos deben conservarse. Solo cuando esa anotación está escrita de forma duradera aplica el cambio en su sitio final y, una vez aplicado, puede liberar la entrada del diario. Si el corte ocurre antes de que la anotación se complete, el cambio simplemente no se aplica al reiniciar. Si ocurre después de anotarlo pero antes o durante su aplicación, el sistema lee el diario y termina de aplicar el cambio completo, o lo revierte con los valores antiguos guardados. En ambos casos queda una sola versión coherente de la estructura, nunca una mezcla a medias.

Conviene precisar qué garantiza y qué no. El journaling garantiza consistencia de los metadatos: al volver a arrancar, archivos, carpetas y permisos forman un conjunto coherente, aunque un archivo concreto aparezca en su versión anterior o en la nueva. No garantiza que los datos del usuario nunca se pierdan, porque su protección depende de si el propio contenido del archivo también se registra en el diario o solo sus metadatos, y de que las escrituras al disco físico se hayan hecho efectivas. Tampoco protege frente a un fallo del propio disco ni sustituye a las copias de seguridad: su ámbito es recuperar la organización tras un corte, no preservar cada byte.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[tipos-de-sistema-de-archivos]] se pasa a esta nota al bajar de los tipos concretos al mecanismo que dos de ellos, ext4 y NTFS, incorporan para proteger su organización y que FAT32 no incorpora. Ya se sabe que cada tipo decide cómo repartir archivos y carpetas; ahora se entiende el procedimiento que algunos tipos usan para no dejar ese reparto en un estado roto cuando la escritura se interrumpe. Es una rama terminal de la cadena: explica un mecanismo de robustez del sistema de archivos sin abrir un nuevo peldaño hacia el hardware ni hacia el detalle interno de cada tipo.

## Límites de esta explicación
Esta nota no desarrolla cómo ext4 ni NTFS organizan su diario por dentro, qué datos exactos anotan ni qué modos de registro ofrece cada uno; ese detalle interno queda fuera del alcance de este peldaño y solo se ha mencionado a nivel general en [[tipos-de-sistema-de-archivos]]. Tampoco trata la comprobación completa de consistencia como tema propio, las copias de seguridad ni los fallos físicos del disco.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota; las afirmaciones técnicas quedan pendientes de respaldo por el orquestador según §7.
