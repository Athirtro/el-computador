# El Computador

Libro técnico-divulgativo en español sobre el ordenador, escrito como vault Obsidian.

Recorre el ordenador **de lo más visible a lo más fundamental**, un peldaño a la vez, sin saltos de abstracción:
`Aplicación → … → código máquina → ISA → ALU → puertas lógicas → transistores → semiconductores → física cuántica del sólido → silicio dopado`.

Lector objetivo: ingenieros de sistemas/computación que quieren entender la máquina de arriba abajo, sin lagunas.

## Estructura

```
.
├── 00-indice.md                  # Orden de lectura lineal
├── 01-ordenador/
│   ├── hardware/                 # Procesador, memoria, buses, periféricos...
│   └── software/
│       ├── sistema/              # Firmware, kernel, procesos, memoria...
│       ├── aplicacion/
│       ├── programacion/         # Lenguajes, compilador, ensamblador...
│       └── malicioso/            # Malware, vulnerabilidades, exploits (técnico/defensivo)
├── _control/
│   ├── mapa.md                   # Cobertura y estado de cada nodo
│   ├── cola.md                   # Temas en orden de prerequisitos
│   └── decisiones.md             # Decisiones de alcance
├── _registro/
│   ├── conceptos.md              # Única fuente de verdad (sin duplicados)
│   └── fuentes.md                # Referencias primarias verificadas
└── AGENTS.md                     # Prompt maestro del orquestador
```

Cada nota usa frontmatter + secciones fijas (`Idea central`, `Explicación`, `Límites`, etc.), enlaza en `[[slug]]` y cita fuentes registradas con ID `FTE-####`.

## Reglas clave

- **Una nota, un peldaño.** Si necesita dos niveles, se divide.
- **Sin duplicados:** cada concepto tiene una única nota canónica.
- **Sin saltos:** todo término nuevo se define o enlaza.
- **Sin código/diagramas** salvo autorización explícita. Prosa en español, LaTeX para fórmulas, Mermaid si se autoriza diagrama.
- **Fuentes primarias primero** (AMD/Intel, IEEE, ISO, manuales oficiales). Nada de referencias inventadas.

Ver detalle completo en [`AGENTS.md`](AGENTS.md).

## Estado

- [x] AGENTS.md revisado, estructura creada, migración a slugs
- [x] Mapa de cobertura + índice inicial (`_control/mapa.md`, `00-indice.md`)
- [ ] Redacción de notas (tras validación del mapa)
- [ ] Cadena completa hasta física/matematica (`revisado`)

## Colaborar

1. Revisar `_control/mapa.md` y `00-indice.md`.
2. Respetar `AGENTS.md` (§5 formato, §11 checklist).
3. Registrar toda fuente nueva en `_registro/fuentes.md` antes de citarla.

## Cómo verlo en Obsidian

Clona y abre la carpeta como vault:

```bash
git clone https://github.com/Athirtro/el-computador.git
```

Empieza por `00-indice.md` y sigue los enlaces `[[...]]`.

---
Orquestación por agente con subagentes redactores. Todo cambio se versiona: commit + push a `main`.
