Desde mi perspectiva, el software es el componente intangible del ordenador. Es el dispositivo abstracto encargado de controlar el hardware a fin de manipular los electrones en el sistema para realizar cálculos y ajustar su representación a estándares comprensibles por otros sistemas mecánicos o biológicos.

Un ejemplo inmediato de software es el sistema operativo, el cual actúa como el entorno integral que nos permite interactuar con la computadora. En su centro se encuentra el _kernel_ o núcleo, la pieza clave de software de más bajo nivel que tiene control directo sobre los componentes físicos del dispositivo y coordina todos sus recursos.

Un ejemplo de software un poco menos directo puede ser un programa escrito por un ser humano. Dicen que la programación es la brujería del siglo XXI, lo cual para mí tiene mucho sentido, porque una persona escribe códigos extraños que muy poca gente es capaz de interpretar correctamente y hace que un montón de piedras con formas extrañas realicen tareas por él. Por ejemplo:

```Python
def factorial(n):
    return n * factorial(n - 1) if n > 0 else 1
```

`factorial` es una función escrita en un lenguaje de programación llamado Python, uno de altísimo nivel, cuyo propósito es calcular de manera recursiva el valor de aplicar el operador matemático factorial a un número _n_ cualquiera. O casi cualquiera. Pero, si nos paramos a pensar un momento en las implicaciones que esto tiene, resulta enigmático: ¿cómo es que un montón de chatarra conectada a la corriente es capaz de calcular algo tan complejo como un factorial? ¿Qué clase de brujería le permite a una máquina pensar?

Incluso, si cambiamos por un lenguaje de aún menor nivel, podemos ver lo siguiente:

```C
#include <stdio.h>

// Versión recursiva (equivalente directa)
unsigned long long factorial_recursivo(int n) {
    return (n > 0) ? (n * factorial_recursivo(n - 1)) : 1;
}

// Versión iterativa (de menor nivel a nivel de ejecución de CPU, sin overhead de pila)
unsigned long long factorial_iterativo(int n) {
    unsigned long long resultado = 1;
    for (int i = 2; i <= n; i++) {
        resultado *= i;
    }
    return resultado;
}

int main(void) {
    int n = 5;
    printf("Factorial de %d: %llu\n", n, factorial_recursivo(n));
    return 0;
}
```

Aquí vemos de una forma mucho más explícita cómo hacemos que un ordenador piense. Primero, analicemos la versión recursiva, que es la equivalencia directa del código escrito en Python. En esta versión vemos que lo primero que hace el programador es indicar al sistema que la función va a devolver un número muy, muy grande y además positivo. Luego, le indica que el parámetro _n_ debe ser tratado como un valor entero. Por último, tenemos una transliteración del mismo operador condicional utilizado en Python, donde inicialmente observamos una condición y, en caso de que se compruebe positiva, devolvemos el producto de _n_ por el factorial de _n - 1_; si no, devolvemos 1.

Luego, tenemos la versión iterativa, que nos permite dimensionar la complejidad latente de la operación que estábamos llevando a cabo en una única línea en el caso anterior, pues esta es una de las principales características del software moderno: no existe una única manera de llevar a cabo una tarea. Sin embargo, aunque C está más cerca del hardware que Python, la CPU tampoco lo entiende directamente: este código debe traducirse primero a lenguaje ensamblador y luego a código máquina (ceros y unos), las únicas instrucciones que los circuitos son capaces de interpretar.

En fin, no todo el universo del software es código ejecutable. A menudo interactuamos con objetos virtuales que damos por sentado, como los archivos PDF, las páginas web, las imágenes, los videos o la música. Aunque solemos pensar en ellos simplemente como elementos del sistema, en realidad son estructuras de datos y formatos que requieren de un software específico (un visor, un navegador o un reproductor) para ser interpretados y cobrar vida.

Sin embargo, el consenso actual es clasificar el software en cuatro grandes grupos según su función y el objetivo para el que se desarrolla:

- [[Software de sistema]]
- [[Software de aplicación]]
- [[Software de programación]]
- [[Software malicioso]]