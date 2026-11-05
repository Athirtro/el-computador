---
titulo: "Tipos de sistema de archivos"
slug: tipos-de-sistema-de-archivos
rama: software
categoria: sistema
nivel: 5
prerequisitos: [sistema-de-archivos]
conduce_a: [journaling]
alias: ["tipos de sistema de archivos", "filesystem types"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Tipos de sistema de archivos

## Idea central
No existe un único modo de organizar archivos en un disco: hay varios tipos de sistema de archivos, cada uno con reglas propias sobre nombres, tamaños y permisos. Conocer los tres más extendidos —ext4, NTFS y FAT32— permite elegir o reconocer el formato de un almacenamiento sin confundirlo con el concepto general de [[sistema-de-archivos]].

## Antes de empezar
- [[sistema-de-archivos]]: la parte del sistema operativo que organiza la información persistente como archivos y carpetas con nombre y ruta.

## Explicación
Un tipo de sistema de archivos es un conjunto concreto de reglas que un sistema operativo usa para guardar, localizar y proteger los datos en un dispositivo. Dos ordenadores pueden presentar los mismos archivos y carpetas a sus programas y, sin embargo, repartirlos por dentro de formas distintas según el tipo elegido al preparar o formatear el almacenamiento. Por eso el tipo limita o facilita cosas visibles para el usuario, como el tamaño máximo de un archivo, la longitud de los nombres o los permisos que se pueden asignar.

FAT32 es el tipo más antiguo y compatible de los tres. Nace de la familia FAT, pensada para discos pequeños y para que cualquier sistema pueda leerla. Su virtud es la compatibilidad: una memoria USB formateada en FAT32 se reconoce prácticamente en cualquier ordenador y en muchos aparatos no informáticos. Su límite es su sencillez: no admite archivos individuales de más de unos 4 GB y ofrece pocas opciones de protección, por lo que hoy se reserva sobre todo para medios extraíbles compartidos y no para el disco principal del sistema.

NTFS es el tipo habitual de Windows. Admite discos grandes y archivos muy grandes, y guarda información adicional sobre cada archivo, como permisos, propietario y fechas, para que el sistema pueda decidir quién puede leerlo o modificarlo. Esa información de control es parte de su diseño general, no un añadido movido por cada programa. En conjunto, NTFS está pensado para un sistema de escritorio con muchos usuarios, archivos de gran tamaño y control de acceso, a costa de una mayor complejidad interna.

Ext4 es el tipo habitual de las distribuciones Linux. Hereda de la familia ext, creada para ese sistema, y comparte con NTFS la capacidad para discos y archivos grandes y para permisos por usuario. Su diferencia práctica no está en los nombres que muestra, sino en cómo organiza el espacio y cómo protege la consistencia de los datos ante un corte de corriente, aspecto que se trata en detalle en [[journaling]]. Como cada sistema operativo puede montar con facilidad sus propios tipos y con más esfuerzo los ajenos, la elección del tipo suele venir determinada por el sistema que va a usar el disco a diario.

Entre los tres, la comparación útil no es cuál es «mejor» en abstracto, sino cuál responde al uso: compatibilidad máxima con FAT32, escritorio Windows con NTFS o sistema Linux con ext4. Ninguno cambia lo explicado en [[sistema-de-archivos]] —archivos, carpetas y rutas—, solo el modo concreto de aplicar esas ideas al almacenamiento.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[sistema-de-archivos]] se pasa a esta nota al bajar del concepto general al caso concreto: ya se sabe que hay archivos y carpetas, y ahora se verá que cada tipo los implementa con límites y protecciones distintos. El paso siguiente es [[journaling]], que explica el mecanismo —presente en ext4 y NTFS, pero no en FAT32— que ayuda a recuperar la organización tras un fallo.

## Límites de esta explicación
Esta nota no desarrolla la estructura interna de ext4, NTFS ni FAT32, ni detalla el mecanismo de [[journaling]], tratado en la nota siguiente. Tampoco entra en tipos usados en medios extraíbles, en red o en dispositivos incrustados, ni en los dispositivos físicos de almacenamiento.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): tipos de sistema de archivos como reglas concretas de organización.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): tipos de sistema de archivos como reglas concretas de organización.
