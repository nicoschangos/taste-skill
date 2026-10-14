# unified-frontend

Un solo skill de diseño frontend que reemplaza a ocho que se contradecían entre sí:
Anti-Slop (AJONAI), impeccable, taste-skill, tastemaker, los `better-*` de interfaces,
landing-page-design, web-design-engineer y humanizer (en la parte de copy).

Este README es para ti. Claude no lo carga: lee solo `SKILL.md` y, cuando hace falta, el archivo de
`references/` que corresponda.

## Por qué existe

Con todos esos skills activos a la vez pasan dos cosas:

1. **Gastas más tokens.** Al inicio de cada sesión solo se carga el nombre y la descripción de cada
   skill (unos 50-200 tokens cada uno), así que tenerlos instalados cuesta poco. El problema es que
   casi todos dicen "úsame para cualquier UI", y cuando pides algo de frontend se activan varios a
   la vez y cada uno carga su cuerpo completo. Aproximadamente: taste-skill ~17k tokens, impeccable
   (SKILL + new-work + craft-floor) ~16k, tastemaker ~12k más sus referencias, web-design-engineer
   ~7k, landing-page-design ~3.5k. Son unos 50-60k tokens de instrucciones antes de escribir una
   línea.
2. **El resultado empeora, no solo cuesta más.** Se contradicen en al menos 38 puntos. Unos
   ejemplos: landing-page-design exige texto con degradado en el hero y los otros lo prohíben;
   taste-skill recomienda Geist y Anti-Slop lo señala como fuente sobreusada; taste-skill dice que
   el texto grande empieza en 18px y WCAG dice 24px; tastemaker exige animación en todas las
   pantallas e impeccable pide un solo momento animado. Con órdenes opuestas, el modelo
   promedia y vuelve justo al resultado genérico que intentabas evitar.

Este skill carga unos 3.7k tokens (`SKILL.md`) y en una tarea típica suma 2 o 3 referencias, unos
8-10k en total. Todas las contradicciones están resueltas con una escalera de precedencia, y cada
una está documentada en `references/13-conflict-ledger.md` (qué decía cada skill y quién ganó).

## Instalación

```bash
npx skills add nicoschangos/taste-skill --skill unified-frontend
```

O copia la carpeta `skills/unified-frontend` a `~/.claude/skills/` (personal) o a
`.claude/skills/` dentro de tu proyecto.

El checker estático no tiene dependencias y necesita Node:

```bash
node ~/.claude/skills/unified-frontend/scripts/check.mjs src/
```

## Qué desactivar para que no compitan

Desinstala o desactiva los que se solapan, porque si no se siguen activando junto a este:

- `taste-skill` / `design-taste-frontend`, `taste-skill-v1`, `gpt-tasteskill`, `soft-skill`,
  `minimalist-skill`, `brutalist-skill`, `redesign-skill`, `stitch-skill`
- `tastemaker`
- `landing-page-design`
- `web-design-engineer`
- `anti-slop-ajonai`
- `impeccable`, salvo que uses su modo `live` o su CLI; en ese caso invócalo a mano

Para conservar uno sin que se dispare solo, añade esto a su frontmatter:

```yaml
disable-model-invocation: true
```

Así deja de cargarse automáticamente y solo se ejecuta cuando lo llamas con `/nombre`.

Lo que **sí puedes dejar** sin conflicto:

- `humanizer`: es especialista en reescribir prosa y no compite en diseño.
- `output-skill` (full-output-enforcement): es compatible.
- `variant`, `break`, `state-machine`, `interface-review`, `explain-interface` (de interfaces):
  ya se invocan solo a mano, así que no cuestan nada hasta que los llamas.
- Los `better-*`, si prefieres sus revisiones por dominio; este skill ya incluye sus valores.
- Los skills de generación de imágenes (`imagegen-*`, `brandkit`, `image-to-code-skill`):
  no hacen el mismo trabajo.

## Cómo se usa

No necesitas comandos. Pide el trabajo con normalidad:

- "Hazme una landing para una app de turnos de una barbería"
- "Rediseña esta página pero mantén la marca"
- "Esto se ve hecho por IA, revísalo" (hace una revisión sin editar, con una tabla de hallazgos y
  un veredicto)
- "Constrúyelo en estilo brutalista" (lo que pides siempre manda sobre las reglas del skill)

Antes del código vas a ver una **hoja de decisiones** (SUBJECT, MODE, PALETTE, TYPE, SPACE, SHAPE,
MOTION, SIGNATURE). Es la pieza más importante: obliga a que cada color, fuente y espaciado salga de
tu producto concreto y no del promedio de todas las webs. Si una línea te parece genérica, corrígela
ahí; es mucho más barato que corregir el código después.

## Cómo resuelve los conflictos

De mayor a menor prioridad:

1. Lo que tú pides explícitamente.
2. Lo que ya existe en el proyecto: marca, tokens, sistema de diseño, copy, URLs.
3. El piso de accesibilidad y corrección (contraste, teclado, foco, estados, movimiento reducido).
   Si 1 o 2 chocan con esto, te lo dice y propone la versión más cercana que cumple.
4. La hoja de decisiones del brief.
5. Lo que corresponde al tipo de superficie (Persuade, Operate, Read, Experience).
6. Valores de oficio exactos, solo donde nada de lo anterior decidió.
7. La lista de "lo que hoy se ve generado", que solo pide justificar, nunca decide.

## Estructura

```
unified-frontend/
├── SKILL.md                  núcleo: precedencia, flujo, hoja de decisiones, piso, defaults
├── references/               se cargan bajo demanda
│   ├── 01-decision-sheet.md  cómo llenar la hoja, ejemplo trabajado, diales opcionales
│   ├── 02-color.md · 03-type.md · 04-space-surface.md
│   ├── 05-states-a11y.md     estados, accesibilidad, triggers de severidad
│   ├── 06-motion.md          presupuesto de animación, curvas, recetas exactas
│   ├── 07-assets-content.md  imágenes, iconos, datos, copy
│   ├── 08-persuade.md        landings, marketing, portfolios
│   ├── 09-operate-read.md    apps, dashboards, docs
│   ├── 10-redesign.md · 11-review.md
│   ├── 12-dated-defaults.md  la monocultura actual (perecedera, con fecha)
│   └── 13-conflict-ledger.md las 38 contradicciones y cómo se resolvieron
├── scripts/check.mjs         checker estático (de Anti-Slop, MIT)
└── NOTICE.md                 créditos y licencias
```

El skill está escrito en inglés a propósito: el inglés usa menos tokens que el español para el
mismo contenido y es el idioma de las fuentes. Claude te responde en el idioma en que le escribas.

## Mantenimiento

`references/12-dated-defaults.md` tiene fecha porque lo que hoy delata a una web generada cambia
cada pocos meses (y suele cambiar justo porque todos siguieron el último consejo). Ese archivo
explica cómo actualizarlo.
