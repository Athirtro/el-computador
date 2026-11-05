---
titulo: "Función de dispersión"
slug: funcion-de-dispersion
rama: software
categoria: sistema
nivel: 6
prerequisitos: [tabla-hash]
conduce_a: [colision-en-tabla-hash]
alias: ["función de dispersión", "hash function"]
estado: borrador
fuentes: [FTE-0005]
---

# Función de dispersión

## Idea central
La función de dispersión es la regla que convierte una clave en la posición de la [[tabla-hash]] donde debe guardarse o buscarse su valor asociado. Su trabajo es repartir las claves entre las posiciones disponibles de forma razonablemente uniforme, sin depender del orden en que se insertan.

## Antes de empezar
- [[tabla-hash]]: organización de pares clave-valor en memoria en la que la posición de cada elemento se calcula a partir de su clave.
- [[estructuras-de-datos]]: organización general de la información en memoria.

## Explicación
En la [[tabla-hash]] la clave y la posición no coinciden: la clave puede ser un texto, un número de cuenta o cualquier otro identificador, mientras que la posición es un índice dentro de un conjunto limitado de posiciones. La función de dispersión es el puente entre ambos dominios. Recibe una clave y devuelve un entero dentro del rango de posiciones; ese entero es la posición calculada para esa clave.

Una propiedad esencial es la determinista: la misma clave produce siempre la misma posición, en cualquier momento y sin importar qué otros elementos haya ya en la tabla. Sin esto, buscar sería imposible, porque al localizar un elemento habría que saber exactamente qué cálculo se hizo al insertarlo. La función asigna la posición; la tabla decide qué hacer con ella.

La segunda propiedad es el reparto. Si las claves se concentraran en unas pocas posiciones, gran parte de la tabla quedaría vacía y el acceso directo se perdería: muchas claves distintas terminarían disputándose los mismos lugares. Por eso se busca que claves distintas y parecidas caigan en posiciones distintas y bien distribuidas por todo el rango. Cuando el reparto es uniforme, cada posición recibe, en promedio, una parte similar del total de claves, y la búsqueda por clave mantiene su ventaja frente al recorrido secuencial.

Para lograr un rango acotado a partir de un valor sin límite previo, el cálculo habitual reduce el resultado módulo el número de posiciones, es decir, se queda con el resto de dividir por ese número. Así, cualquier valor intermedio cabe en el intervalo de índices. Esta reducción, sin embargo, puede hacer que dos claves distintas terminen en la misma posición. Esa coincidencia es la colisión, y esta nota solo la señala como consecuencia inevitable de comprimir un dominio grande en uno pequeño; su tratamiento corresponde a la nota siguiente.

El reparto no se puede entender sin su coste. La función se aplica en cada inserción y en cada búsqueda, de modo que debe ser rápida: un cálculo muy costoso anularía la ganancia de no recorrer la tabla. Al mismo tiempo, un cambio pequeño en la clave debería producir un cambio apreciable en la posición calculada; de lo contrario, claves cercanas seguirían cayendo cerca y el reparto se degradaría. La función de dispersión es, en suma, un compromiso entre rapidez, determinismo y uniformidad del reparto.

## Cómo se conecta con lo anterior y lo siguiente
La [[tabla-hash]] introdujo la idea de calcular la posición a partir de la clave, pero dejó sin explicar cómo se hace ese cálculo: esta nota ocupa ese hueco al definir la función que realiza la conversión y las propiedades que debe cumplir. El siguiente paso es [[colision-en-tabla-hash]], porque una vez que la función reparte las claves, queda por resolver qué ocurre cuando dos de ellas obtienen la misma posición.

## Límites de esta explicación
Esta nota no trata el detalle de las colisiones —cómo se guardan dos claves en una misma posición—, que corresponde a [[colision-en-tabla-hash]]. Tampoco presenta familias concretas de funciones de dispersión ni criterios para elegir el tamaño de la tabla en función de su carga, ni la representación de estos datos en disco, que corresponde a [[formatos-de-archivos]].

## Referencias
- FTE-0005 (Introduction to Algorithms, Cormen et al., 4ª ed.): función de dispersión, reparto uniforme y determinismo.
