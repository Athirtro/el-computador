---
titulo: "Comprobación de consistencia"
slug: comprobacion-de-consistencia
rama: software
categoria: sistema
nivel: 7
prerequisitos: [journaling]
conduce_a: []
alias: ["file system check", "fsck"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Comprobación de consistencia

## Idea central
La comprobación de consistencia (file system check, fsck) es el recorrido sistemático que hace un programa de diagnóstico sobre las estructuras de un [[sistema-de-archivos]] para detectar y, cuando es posible, corregir las incoherencias que deja un corte de corriente o un fallo. Es el procedimiento que se realiza cuando el [[journaling]] no basta o no existe, y su función es dejar el conjunto de archivos y carpetas coherente antes de volver a usar el disco.

## Antes de empezar
- [[journaling]]: el diario de cambios que anota cada modificación antes de aplicarlo, y que permite rehacer o deshacer operaciones incompletas tras un corte.
- [[sistema-de-archivos]]: la parte del sistema operativo que mantiene la información persistente como archivos con nombre y ruta.
- [[tipos-de-sistema-de-archivos]]: cada tipo concreto de sistema de archivos, como ext4, NTFS o FAT32, organiza sus estructuras con reglas propias.

## Explicación
Un sistema de archivos no guarda solo los datos del usuario; guarda además los metadatos, es decir, la información del propio sistema sobre cada archivo: su tamaño, los bloques que ocupa en el disco y el directorio al que pertenece. Para cada archivo o carpeta existe una entrada que describe estos datos, y existen también tablas que registraron qué bloques están ocupados y cuáles están libres. La consistencia significa que todas estas piezas concuerdan entre sí: cada archivo apunta a bloques existentes y no compartidos, cada bloque ocupado pertenece a algún archivo, cada directorio solo enumera entradas válidas y el registro de bloques libres coincide con la realidad del disco.

Una escritura interrumpida a mitad puede romper cualquiera de esas coincidencias. Al reanudarse el sistema, las estructuras pueden describir un estado que nunca existió como conjunto completo: un directorio puede apuntar a bloques marcados como libres, un archivo puede declarar un tamaño que sus datos aún no tienen, o dos archivos pueden reclamar el mismo bloque. El disco sigue operando físicamente, pero la organización queda incoherente.

La comprobación de consistencia es el proceso que verifica esas coincidencias recorriendo las estructuras una por una. En un primer paso, lee la información general del volumen, como su tamaño y sus tablas principales, para saber qué debe esperar. En un segundo paso, recorre todas las entradas de archivos y comprueba que cada una apunta a bloques dentro del volumen, con un tamaño coherente y sin solaparse con otras entradas. En un tercer paso, recorre los directorios y verifica que cada nombre se corresponde con una entrada válida y que no hay entradas duplicadas ni huérfanas, es decir, archivos que existen pero que ningún directorio enumera. En un cuarto paso, compara el registro de bloques libres con el resultado de los pasos anteriores y lo corrige para que refleje los bloques realmente ocupados. Cuando encuentra una incoherencia menor y deducible, por ejemplo un contador desactualizado o una entrada huérfana, la repara; cuando encuentra daño en los propios datos del usuario, lo señala en lugar de inventar un contenido.

Este recorrido es un programa de [[herramientas-de-sistema|herramientas de sistema]], normalmente denominado fsck por su nombre en inglés, y se ejecuta con el volumen desmontado o en modo de solo lectura, porque reparar mientras el sistema escribe añadiría nuevas escrituras sobre estructuras ya dudosas. Puede ejecutarse de forma automática al arrancar tras un cierre anormal o manualmente por el administrador. Su coste es proporcional al tamaño del volumen: en discos grandes, recorrer todas las estructuras puede tardar mucho, y durante ese tiempo el volumen no está disponible para su uso habitual.

La relación con el diario de cambios es de complemento, no de sustitución. Cuando un tipo de sistema de archivos dispone de [[journaling]], al arrancar tras un corte el sistema primero reproduce las anotaciones del diario y solo recurre a la comprobación completa si el diario no basta, si el propio diario quedó incompleto o si se sospecha un fallo más profundo. Cuando el tipo no dispone de diario, como ocurre con FAT32 según se vio en [[tipos-de-sistema-de-archivos]], la comprobación completa es la única vía de recuperación de la organización. En ambos casos conviene recordar el límite señalado en [[journaling]]: la comprobación detecta y corrige incoherencias en los metadatos, pero no puede reconstruir datos del usuario que ya se sobrescribieron antes del corte.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[journaling]] se pasa a esta nota al preguntarse qué ocurre cuando el diario no existe o no basta. El diario protege la organización evitando escrituras incompletas; la comprobación de consistencia es el procedimiento que revisa la organización etapa por etapa y la deja coherente cuando ya no hay un registro previo del que tirar. Es una rama terminal de la cadena: explica el mecanismo de reparación que complementa al diario sin abrir un nuevo peldaño hacia el detalle interno de cada tipo de sistema de archivos ni hacia la protección de los datos del usuario.

## Límites de esta explicación
Esta nota no desarrolla el detalle interno del diario de cambios, que se trata en [[journaling]], ni cómo cada tipo concreto, como ext4, NTFS o FAT32, nombra y ordena sus estructuras internas, que se trata en [[tipos-de-sistema-de-archivos]]. Tampoco trata las copias de seguridad ni los fallos físicos del disco: la comprobación repara inconsistencias lógicas en las estructuras, no sustituye la recuperación de datos dañados ni la prevención de fallos del soporte.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): consistencia y recuperación de sistemas de archivos.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): consistencia y recuperación de sistemas de archivos.
