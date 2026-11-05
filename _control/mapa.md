# Mapa de cobertura - El Computador

> Orquestador. Estados: `pendiente | asignado | borrador | redactado | revisado`. `[[slug]]` = nota canónica. Ninguna nota hoja está redactada aún (§13.4: validación previa).

## 0. Raíz
- [[ordenador]] — pendiente
- [[hardware]] — pendiente (legado: `Hardware.md` vacío en raíz)
- [[software]] — borrador (reescrito según §5/§11, pendiente fuentes)

## 1. Hardware (visible → físico)
- Procesador
  - [[procesador]] — pendiente → [[cpu-amd-ryzen-7-5700g]] (caso del autor, ver decisiones D-003) — pendiente
  - [[arquitectura-x86-64]] — pendiente
  - [[ciclo-de-ejecucion]] — pendiente
  - [[registros-y-unidad-de-control]] — pendiente
  - [[unidad-aritmetico-logica-alu]] — pendiente
- Memoria
  - [[memoria-ram]] — pendiente (legado: `La memoria.md`)
  - [[memoria-cache]] — pendiente
  - [[memoria-virtual]] — pendiente (legado: `Memoria virtual.md`)
  - [[espacio-de-usuario]] — pendiente (legado: `Espacio de usuario.md`)
  - [[espacio-de-kernel]] — pendiente (legado: `Espacio de Kernel.md`)
  - [[bus-de-memoria]] — pendiente
- Almacenamiento
  - [[almacenamiento]] — pendiente
  - [[hdd]] — pendiente (caso: disco 931,51 GB)
  - [[ssd]] — pendiente (caso: disco 953,85 GB)
  - [[gpu]] — pendiente (caso: RTX 5050 8 GB)
- Placa base
  - [[placa-base]] — pendiente (caso: PRIME B350M-A)
  - [[buses]] — pendiente
  - [[chipset]] — pendiente
- Periféricos
  - [[perifericos-de-entrada]] — pendiente
  - [[perifericos-de-salida]] — pendiente
  - [[fuente-de-alimentacion]] — pendiente
  - [[refrigeracion]] — pendiente
- Fundamento eléctrico / físico (común a todo hardware)
  - [[circuitos-combinacionales]] — pendiente
  - [[circuitos-secuenciales]] — pendiente
  - [[puertas-logicas]] — pendiente
  - [[algebra-de-boole]] — pendiente
  - [[transistor-mosfet]] — pendiente
  - [[transistor-como-interruptor]] — pendiente
  - [[semiconductores]] — pendiente
  - [[bandas-de-energia]] — pendiente
  - [[fisica-del-solido]] / [[fisica-cuantica-del-solido]] — pendiente
  - [[silicio-dopado]] — pendiente
- Comunicaciones
  - [[red-buses-internos]] — pendiente (comparar con red)

## 2. Software (visible → físico)
- Sistema
  - [[software-de-sistema]] — borrador (reescrito panorama 4 subgrupos)
  - [[firmware]] — pendiente
  - [[bios-uefi]] — pendiente
  - [[sistema-operativo]] — pendiente (legado: `El sistema operativo.md`)
  - [[nucleo-kernel]] — pendiente (legado: `El Kernel.md`)
  - [[gestion-de-recursos]] — pendiente (legado: `Gestión de recursos.md`)
  - [[gestor-de-procesos]] — pendiente
  - [[gestor-de-memoria]] — pendiente
  - [[sistema-de-archivos]] — pendiente
  - [[controladores-drivers]] — pendiente
  - [[estructuras-de-datos]] — pendiente (legado: `Estructuras de datos.md`)
  - [[formatos-de-archivos]] — pendiente (legado: `Formatos de archivos.md`)
- Aplicación
  - [[software-de-aplicacion]] — borrador (panorama por finalidad)
  - [[aplicacion-grafica]] — pendiente
  - [[aplicacion-con-red]] — pendiente
- Programación
  - [[software-de-programacion]] — borrador (panorama lenguajes/traductores/IDE)
  - [[lenguajes-de-programacion]] — pendiente (legado: `Lenguajes de programación.md`)
  - [[lenguajes-compilados]] — pendiente (legado: `Lenguajes compilados.md`)
  - [[lenguajes-interpretados]] — pendiente
  - [[compilacion]] — pendiente (legado: `Compilación.md`)
  - [[compilador]] — pendiente
  - [[interprete]] — pendiente
  - [[ensamblador]] — pendiente
  - [[lenguaje-ensamblador]] — pendiente (legado: `Lenguaje ensamblador.md`)
  - [[codigo-maquina]] — pendiente (legado: `Código máquina.md` vacío)
  - [[conjunto-de-instrucciones-isa]] — pendiente → enlaza a [[arquitectura-x86-64]]
  - [[enlazadores]] — pendiente
  - [[cargadores]] — pendiente
- Malicioso
  - [[software-malicioso]] — borrador (panorama técnico/defensivo sin exploits detallados)
  - [[malware]] — pendiente
  - [[vulnerabilidades]] — pendiente
  - [[exploits]] — pendiente
  - [[defensa-malware]] — pendiente

## 3. Cadena troncal de lectura (sin saltos)
[[ordenador]] → [[hardware]] → [[procesador]] → [[arquitectura-x86-64]] → [[ciclo-de-ejecucion]] → [[registros-y-unidad-de-control]] → [[unidad-aritmetico-logica-alu]] → [[circuitos-combinacionales]] → [[circuitos-secuenciales]] → [[puertas-logicas]] → [[algebra-de-boole]] → [[transistor-mosfet]] → [[transistor-como-interruptor]] → [[semiconductores]] → [[bandas-de-energia]] → [[fisica-cuantica-del-solido]] → [[silicio-dopado]]

Cadena software: [[software]] → [[sistema-operativo]] → [[nucleo-kernel]] → [[gestion-de-recursos]] → [[memoria-virtual]] → [[espacio-de-usuario]] / [[espacio-de-kernel]] → [[lenguajes-de-programacion]] → [[compilacion]] → [[lenguaje-ensamblador]] → [[codigo-maquina]] → [[conjunto-de-instrucciones-isa]] → ... (física)
