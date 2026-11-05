# Plan - Nivel 3 (Software)

> Orquestador. Nivel 3 = primer desglose de los 4 grupos de nivel 2. No se redacta hasta validar esta planificación.

## 1. Alcance por rama

### A. Sistema (7 notas)
| Nota | Prerrequisito | Cubre | No cubre |
|---|---|---|---|
| [[sistema-operativo]] | [[software-de-sistema]] | Entorno integral, funciones SO, ejemplo kernel | [[nucleo-kernel]], [[gestion-de-recursos]] |
| [[firmware]] | [[software-de-sistema]] | Software en dispositivo, arranque previo | [[bios-uefi]], [[controladores-drivers]] |
| [[bios-uefi]] | [[firmware]] | BIOS/UEFI, reconoce HW y carga SO | Detalle UEFI avanzado |
| [[sistema-de-archivos]] | [[sistema-operativo]] | Aparición de archivos y carpetas | [[formatos-de-archivos]] |
| [[estructuras-de-datos]] | [[sistema-operativo]] | Organización en memoria | [[formatos-de-archivos]] |
| [[formatos-de-archivos]] | [[estructuras-de-datos]] | Representación en disco | Detalle cada formato |
| [[controladores-drivers]] | [[sistema-operativo]] | Enseña SO a manejar dispositivos | Firmware de cada dispositivo |

### B. Aplicación (2 notas)
| Nota | Prerrequisito | Cubre | No cubre |
|---|---|---|---|
| [[aplicacion-grafica]] | [[software-de-aplicacion]] | Ventanas, GUI, ejemplo editor | [[aplicacion-con-red]] |
| [[aplicacion-con-red]] | [[software-de-aplicacion]] | Comunicación con otros equipos | Seguridad web detallada |

### C. Programación (3 notas nivel 3)
| Nota | Prerrequisito | Cubre | No cubre |
|---|---|---|---|
| [[lenguajes-de-programacion]] | [[software-de-programacion]] | Lenguajes de alto nivel, Python/C como ejemplos | [[lenguajes-compilados]], [[lenguajes-interpretados]] |
| [[compilador]] | [[lenguajes-de-programacion]] | Traduce completo antes de ejecutar | [[compilacion]] paso a paso |
| [[interprete]] | [[lenguajes-de-programacion]] | Ejecuta instrucción a instrucción | Productos compilados |

### D. Malicioso (3 notas)
| Nota | Prerrequisito | Cubre | No cubre |
|---|---|---|---|
| [[malware]] | [[software-malicioso]] | Clasificación por propagación/ocultamiento/objetivo | [[vulnerabilidades]], [[exploits]] |
| [[vulnerabilidades]] | [[software-malicioso]] | Defectos que permiten uso no previsto | Explotación detallada |
| [[exploits]] | [[vulnerabilidades]] | Aprovechamiento concreto | [[defensa-malware]] |
| [[defensa-malware]] | [[malware]], [[exploits]] | Prevención/detección/respuesta | Detalle operativo |

## 2. Orden de lectura propuesto (coherente con escalera sin saltos)
1. [[sistema-operativo]] → 2. [[nucleo-kernel]] → 3. [[gestion-de-recursos]] → 4. [[sistema-de-archivos]] / [[estructuras-de-datos]] / [[formatos-de-archivos]] (en paralelo tras SO) → 5. [[firmware]] → [[bios-uefi]] → [[controladores-drivers]]
2. [[lenguajes-de-programacion]] → [[compilador]] / [[interprete]] (paralelo) → [[compilacion]] → [[lenguaje-ensamblador]] → [[codigo-maquina]]
3. [[aplicacion-grafica]] / [[aplicacion-con-red]] (paralelo)
4. [[malware]] // [[vulnerabilidades]] (paralelo) → [[exploits]] → [[defensa-malware]]

## 3. Paralelización (mismo nivel, sin prerequisito pendiente común)
- **Lote 1 paralelo (6 subagentes):** `sistema-operativo`, `firmware`, `lenguajes-de-programacion`, `aplicacion-grafica`, `aplicacion-con-red`, `malware`, `vulnerabilidades`
- **Lote 2 secuencial:** `sistema-de-archivos`, `estructuras-de-datos`, `controladores-drivers` (tras SO), `bios-uefi` (tras firmware), `compilador`, `interprete` (tras lenguajes), `exploits` (tras vulnerabilidades)
- **Lote 3:** `formatos-de-archivos` (tras estructuras), `compilacion` (tras compilador), `defensa-malware` (tras malware+exploits)

## 4. Fuentes a registrar antes de redactar
- Sistemas operativos: Tanenbaum u OSTEP + documentación oficial kernel Linux
- UEFI: especificación oficial UEFI
- Lenguajes/compiladores: documentación GCC/Clang, CPython
- Malware: NIST glosario + CISA (propuestas P-1–P-3 ya consultadas, pendientes de ID)

## 5. Riesgos y decisiones pendientes
- Alias `malware` duplicado con futura nota `[[malware]]` → reasignar al crearla
- Fuentes en `[[software]]`, `[[software-de-sistema]]`, etc.: aún `fuentes: []`, deben registrarse antes de pasar a `redactado`
- `lenguajes-de-programacion` como prereq y conduce (circularidad) ya corregida en `software-de-programacion.md`

> **Validación pendiente:** confirmar Lote 1 y orden lineal antes de asignar subagentes.
