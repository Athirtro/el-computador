---
titulo: "TLB"
slug: tlb
rama: software
categoria: sistema
nivel: 10
prerequisitos: [paginacion]
conduce_a: []
alias: ["TLB", "translation lookaside buffer"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# TLB

## Idea central
La TLB (*translation lookaside buffer*) es una caché pequeña y rápida, dentro del procesador, que guarda las traducciones de página más usadas recientemente. Evita consultar la [[tabla-de-paginas]] en cada acceso a memoria, que es justo el camino lento que la [[paginacion]] introdujo.

## Antes de empezar
- [[paginacion]]: divide el espacio virtual en páginas de tamaño fijo y traduce cada dirección virtual a un marco físico cambiando solo el número de página por el número de marco.

## Explicación
Cada acceso a memoria realizado por un programa pasa por la traducción de la [[paginacion]]. El procesador entrega el número de página virtual y el desplazamiento, y debe averiguar en qué marco físico reside esa página. Esa averiguación se busca en la [[tabla-de-paginas]], un registro en memoria que indica, por programa, la correspondencia página virtual → marco físico.

El problema es de velocidad: si cada acceso tuviera que ir a buscar su correspondencia en esa tabla, la traducción añadiría un acceso extra a memoria en cada lectura o escritura. Aunque la traducción sea correcta, el procesador pasaría gran parte del tiempo esperando a la propia tabla. Cuanto más grande sea el espacio virtual, más costosa es esa búsqueda.

Una caché es, en una línea, un almacenamiento pequeño y muy rápido que guarda copias de los datos más usados para no tener que ir a buscarlos al almacenamiento principal y lento cada vez. La TLB aplica esa idea a las traducciones: guarda en el procesador las últimas correspondencias consultadas, junto con el programa al que pertenecen y sus permisos. Cuando el procesador necesita traducir una dirección, mira primero en la TLB. Si encuentra allí la traducción, la usa directamente y no toca la tabla de páginas. Si no la encuentra, consulta la tabla, obtiene la correspondencia y la copia en la TLB, sustituyendo otra entrada si ya no caben más.

Que la TLB guarde el programa al que pertenece cada traducción importa porque la misma página virtual puede apuntar a marcos distintos según el programa, como ya se vio en la [[paginacion]]. Sin ese dato, dos programas podrían recibir por error la traducción del otro. Por eso las entradas se invalidan o se separan al pasar de un programa a otro, en especial durante un [[cambio-de-contexto]].

La TLB no cambia qué traducciones existen: sigue siendo la [[tabla-de-paginas]] quien las define. Solo acelera el camino habitual, que es consultar las traducciones recientes. Cuando la traducción buscada no está en la TLB, el sistema sigue funcionando, pero recorre el camino completo a través de la tabla.

## Cómo se conecta con lo anterior y lo siguiente
Desde la [[paginacion]] se avanza de la traducción correcta a la traducción rápida: el problema ya no es cómo traducir, sino cómo no pagar el coste de la tabla en cada acceso. La TLB es el peldaño que resuelve ese coste guardando las traducciones recientes en el procesador. No sustituye a la tabla, que sigue siendo la fuente de la correspondencia.

## Límites de esta explicación
Esta nota no explica cómo se organiza internamente la [[tabla-de-paginas]]; eso se trata en [[tabla-de-paginas]]. Tampoco explica qué ocurre cuando la página pedida no está cargada en ningún marco físico; eso se trata en [[fallo-de-pagina]]. El diseño en circuitos de la TLB y sus políticas de sustitución de entradas quedan fuera de este peldaño.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): traducción de páginas y su aceleración con una caché de traducciones.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): paginación y caché de traducciones de páginas.
