# Decisiones de estructura y alcance

## D-001 Migración de nombres (pendiente validación)
Archivos actuales en raíz con mayúsculas, espacios y tildes no cumplen §4 (`slug` minúsculas, guiones, sin tildes). Propuesta de renombrado (no ejecutado aún por §13.4):
- `El computador.md` → `01-ordenador/ordenador.md` (slug `ordenador`)
- `Hardware.md` → `01-ordenador/hardware.md` (slug `hardware`)
- `Software.md` → `01-ordenador/software.md` (slug `software`)
- `Software de sistema.md` → `01-ordenador/software/software-de-sistema.md`
- `Software de aplicación.md` → `.../software-de-aplicacion.md`
- `Software de programación.md` → `.../software-de-programacion.md`
- `Software malicioso.md` → `.../software-malicioso.md`
- `El Kernel.md` → `01-ordenador/software/sistema/nucleo-kernel.md` (alias: kernel, núcleo)
- `El sistema operativo.md` → `.../sistema-operativo.md`
- `Gestión de recursos.md` → `.../gestion-de-recursos.md`
- `La memoria.md` → `01-ordenador/hardware/memoria-ram.md` (alias: memoria RAM)
- `Memoria virtual.md` → `.../memoria-virtual.md`
- `Espacio de usuario.md` → `.../espacio-de-usuario.md`
- `Espacio de Kernel.md` → `.../espacio-de-kernel.md`
- `Estructuras de datos.md` → `01-ordenador/software/sistema/estructuras-de-datos.md`
- `Formatos de archivos.md` → `.../formatos-de-archivos.md`
- `Lenguajes de programación.md` → `01-ordenador/software/programacion/lenguajes-de-programacion.md`
- `Lenguajes compilados.md` → `.../lenguajes-compilados.md`
- `Compilación.md` → `.../compilacion.md`
- `Lenguaje ensamblador.md` → `.../lenguaje-ensamblador.md`
- `Código máquina.md` → `.../codigo-maquina.md`

## D-002 Contenido legado no conforme a §5/§11
- `Software.md` contiene bloques Python/C, prohibidos salvo autorización explícita. Propuesta: reescribir sin código, solo prosa; conservar idea factorial como ejemplo abstracto.
- `El computador.md` contiene tabla de PC del autor con unidades (`931,51 GB`, `3200 MT/s A-DATA`) — pulir formato y unidades con coma/punto.
- Mayoría de stubs solo tienen `Referencias: [[...]]`, sin frontmatter ni secciones §5. Propuesta: considerarlos borradores a reescribir desde cero, no `redactado`.

## D-003 Alcance hardware: tu PC como caso, no como única verdad
Tu tabla (`El computador.md`) fija: CPU AMD Ryzen 7 5700G, GPU RTX 5050 8 GB, RAM 2x16 GB 3200 MT/s A-DATA, HDD 931,51 GB, SSD 953,85 GB, PRIME B350M-A. Propuesta: usarlo como ejemplo recurrente, explicando siempre el caso general x86-64 y marcando diferencias cuando aplique (ARM, etc.).

## D-004 Alcance software malicioso
§3: tratar malware desde lo técnico y defensivo, sin instrucciones ofensivas detalladas. Si se amplía a exploits explotables, requiere tu criterio explícito.

## D-005 Estructura .obsidian versionada
`.obsidian/` está commiteado. Propuesta: mantenerlo versionado por ahora; añadir `.gitignore` solo para `.obsidian/workspace.json` si querés historial limpio. Decidir antes de siguiente commit.

## D-006 Pausa desarrollo aplicación (2026-11-05)
Desarrollo en pausa al completar Lote E2. Rama aplicación: 44 notas en borrador, 0 pendientes en mapa. 22 huecos A-F quedan como lotes pendientes:

- **F1 (7):** direccion-web-detalle, codigo-de-estado, contenido-estatico-web, contenido-dinamico-web, sintaxis-javascript, componente-web-incorporado-detalle, aplicacion-nativa-pura
- **F2 (5):** serializacion-de-datos, pixel, buffer-de-imagen, rasterizacion, pantalla
- **F3 (5):** captura-vs-burbujeo, contenedor-multimedia-detalle, formato-de-intercambio, estandar-de-codec, autoridad-certificadora
- **F4 (5):** infraestructura-de-claves-publicas, clave-simetrica, clave-asimetrica, autenticacion-remota, bucle-de-eventos
- **F5 (5):** altura-de-arbol, arbol-de-busqueda-binaria, recorridos-en-arbol, direccion-ip, dns

Al reanudar: generar desde `cola-pendientes.md` (sin enlaces desde notas) y lanzar F1→F5 en orden, validando enlaces solo a `cola-listos.md` (§4.1).
