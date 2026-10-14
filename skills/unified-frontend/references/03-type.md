# Typography

## Choosing faces: share and context, not names

No face is banned and none is mandated. Every published list disagrees: one ruleset bans Inter,
Arial and Helvetica, another prescribes `system-ui` (which resolves to exactly those faces on macOS
and Windows), a third bans Fraunces and Instrument Serif while recommending Geist, and Geist is
itself the shipped Next.js and shadcn default. Every face in today's "overused" list was
yesterday's recommended escape. The coherent rule:

- **The finding is a monoculture face doing the display work of a page whose brief never asked for
  it.** The same face on its own brand's site (Geist on Vercel, Mona Sans on GitHub) is identity,
  not a tell.
- A system stack for UI or body text is fine; system faces ship real optical sizing and hinting.
- Serif or sans is decided by the subject, never by "creative brief means serif" and never by
  "serif is banned". A printed-form subject earns a document serif; a sports-data subject
  probably does not.
- Write one sentence of why for each face. If the pairing would appear on another project of
  yours this month, it is a habit. Rotate deliberately across projects.
- Source and self-host the face the design needs (`next/font`, or `@font-face` with
  `font-display: swap`). The nearest installed font is not a fallback for an own-world display
  voice. Load every weight and style you use; browsers synthesize the rest badly.
- On an existing project, never change typefaces unless the task asks for it.

**Non-Latin scripts** (Japanese, Chinese, Korean, Arabic and others) use a different model: usually
one family across a weight scale, chosen for the script's coverage, not a Latin pairing.

## Fewer families, sizes and weights

Usually two families, three at most (display, text, optional utility mono for code, data and
measurement). Mono is not a costume for "technical". Pair for contrast on one axis: category
(serif with sans), weight, width or personality. Two near-identical sans faces read as a mistake.
Emphasis inside a headline uses the italic or bold of the **same** family; a stray word in another
family is not emphasis.

## Scale

- A small modular scale (1.2 for dense UI, 1.25-1.333 for marketing, larger for editorial) with
  semantic names (`text-body-sm`, `text-display`). Pair every size with its line-height and
  weight so a role is one decision.
- Span more than 2x between smallest and largest; many similar sizes read as a flat hierarchy.
- Heading levels descend; a subordinate heading never outranks its parent.
- Hierarchy also comes from weight, color, case and space, not size alone.
- Display up to about `6rem`. Plan headline size together with the hero visual: a headline over six
  words does not start at the largest step. A heading that wraps to four lines is a size error.
- Body starts at `16px` (`rem` units). UI text may go to `14px`, captions `13px`, rarely below
  `12px`. Fluid type with `clamp()` beats breakpoint jumps.

## Line-height (unitless)

| Role | Value |
|---|---|
| Display | `1.0`-`1.1`; at least `1.1` plus a little bottom padding when italic or containing descenders |
| Headings | `1.2`-`1.3` |
| Body | `1.5`-`1.6` (up to `1.7` for long reading) |
| Anything wrapping to 3+ lines, even in a tight row | at least `1.4` |

Tailwind v4 sets `text-5xl` and up to line-height `1`, while `leading-tight` is `1.25`, so
`leading-tight` on display type loosens it. Set display leading explicitly.

## Tracking (in `em`)

| Size | Tracking |
|---|---|
| Display 40px+ | `-0.02em` to `-0.03em`, floor `-0.04em` (Tailwind `tracking-tighter` is `-0.05em`, too tight) |
| Headings 24px+ | `-0.01em` to `-0.02em` |
| Body | `0` |
| Uppercase labels at 14px or less | `+0.05em` to `+0.12em` |

Kerning stays on. `font-kerning: none` is never a fix.

## Weight

Weight 400 or heavier below 18px. Weights 100-300 only at 28px and up, checked against the
background. Avoid 900 unless the face and the subject call for it. Light-on-dark blooms, so dark
themes may need one step lighter.

## Measure and wrapping

- Long-form text 60-75 characters per line, set on the text container (`max-width: 65ch`), not the
  page container.
- `text-wrap: balance` on headings and short descriptions (Chromium ignores it past six lines);
  `text-wrap: pretty` on paragraphs.
- `overflow-wrap: break-word` where long words, URLs or IDs could escape.
- `white-space: nowrap` on labels and badges where a break looks broken. A CTA label never wraps on
  desktop: shorten it or widen the button.
- `text-align: start` in interface text; `justify` only in specific editorial layouts.
- Break heading lines by hand only where the thought breaks.

## Numerals

`font-variant-numeric: tabular-nums` on timers, counters, prices, stat bands and numeric columns.
Proportional figures in prose; oldstyle figures there if the face has them. Use properties, not raw
feature tags: `font-variant-numeric`, `font-weight: 650` rather than `font-variation-settings`.
Leave `font-optical-sizing: auto`.

## Punctuation and characters

- Store text in natural case; apply case with `text-transform`.
- Curly quotes and apostrophes, the ellipsis character `…`, non-breaking spaces between a number
  and its unit (`10 MB`). Code keeps straight quotes.
- **Dashes.** En dash for numeric and date ranges (`2018–2026`, `€40–80k`); never a hyphen there.
  In copy you write, do not use the em dash as a rhythm device: rewrite with a period, comma, colon
  or parentheses, because readers now read dash-heavy prose as generated. When the brand's own
  copy uses em dashes, match its rate rather than stripping them. Hyphens stay in compound words.
- No `<br>`-split, italicized headline as a default "design move"; no vertical rotated text unless
  the composition needs it.
- All caps only for short labels, always tracked.

## Details

- `text-underline-offset` and thickness tuned or `from-font`; a dotted underline signals extra
  meaning (an abbreviation, a defined term). Don't underline for emphasis.
- `-webkit-font-smoothing: antialiased` and `-moz-osx-font-smoothing: grayscale` once on the root.
- `text-box: trim-both cap alphabetic` in buttons and badges as a progressive enhancement.
- Keep text selectable; theme `::selection` from the palette. `user-select: none` only on drag or
  gesture surfaces.
- Decorative text effects (drop caps, outlines) in CSS, so the text stays selectable.
- `lang` on the document, `dir` where direction changes, `<bdi>` around mixed-direction values.
