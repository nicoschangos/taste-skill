# Space, surface and layout

## Uniform spacing is a semantic error

Proximity carries meaning: elements in the same spacing pattern read as related items of equal
weight. One gap value everywhere asserts a flat structure the content does not have. The generated
signature is 16-24px doing every job plus identical `py-24` on every section.

| Register | Job | Typical band |
|---|---|---|
| Intra-component | label to input, icon to text, list rows, card padding | 4-16px |
| Inter-component | between cards, heading to its group | 16-32px |
| Section rhythm | between page regions | 64-160px, varied by role |

- Use the project's scale; otherwise a 4px base that widens as it grows (2, 4, 8, 12, 16, 24, 32,
  40, 48, 64, 80, 96, 128, 160). Values off the scale need a reason.
- The gap between groups is at least 2x the gap within a group.
- A card's internal padding is less than or equal to the gap around it. Content cards (pricing,
  testimonials, features) start at 24px padding.
- Space above a heading exceeds the space below it; a heading binds to what follows.
- Section rhythm breathes unevenly: pivotal sections (hero, primary proof) get more room
  (128-192px on landing pages), connective sections less, and at least one deliberate break marks a
  change of register. The hero's own top padding stays modest (about 96px at most on desktop) so
  its content does not float halfway down the viewport; add presence with scale, not padding.
- Mobile is not desktop stacked: compress section rhythm to its own smaller numbers.
- Density is decided per region: an airy hero, a tight table, a settings page in between.

## Grouping and alignment

- Group with space first, a background shape second, a rule last.
- A small set of alignment edges; everything sits on them.
- Controls look like controls (a shape, border, underline or a toolbar zone), never like the text
  beside them.
- Order by importance: key content at the top and leading edge; identifying content leads a row,
  metadata and actions trail. Visual order matches DOM order (no `order` or `row-reverse` tricks).
- One primary action per view; more than three secondary actions go behind a menu.
- 12px between adjacent bordered or filled controls; 24px between the glyphs of borderless text or
  icon controls.
- Full-width mobile buttons sit inside the layout margins (about 16px inline).

## Radius

Published rulesets prescribe 0, 8-12, 12-16 and 32px, each without derivation, so radius is a
project constant chosen in the sheet and then enforced, not looked up.

- One system, written down: all sharp, all soft, or a documented mix (for example pill buttons,
  12px cards, 8px inputs). Round buttons in a square layout, or the reverse, is broken.
- Radius relates to element size; small controls take proportionally less. Pills are for small
  controls, not cards.
- Nested and concentric: outer radius equals inner radius plus the padding between them (plus any
  border). Past 24px of padding, or with deliberately asymmetric padding, treat the layers as
  separate surfaces with their own radius tokens. If the computed inner radius is 2px or less, make
  it square.

## Elevation: one policy per surface

A hairline plus a wide soft shadow on one element is physically contradictory (flat and floating at
once). Pick one in the sheet:

- **Tonal separation**: surfaces differ by lightness step. The better default for dense UI and the
  only one that works well in dark mode.
- **Shadow**: a designed stack, a tight darker ambient layer plus a wider softer diffuse layer,
  with a real offset, tinted toward the ground hue. Fewer elevation levels give each more power.
  Tailwind's default shadow scale on everything is the tell, not shadow itself.

Borders are for structure: dividers, table cells, selected states and form inputs (whose boundary
needs 3:1). Where a border exists only to fake depth, use the shadow instead. Keep
`border: 1px solid transparent` under a shadow ring so forced-colors mode still draws an edge;
that invisible border is not a second elevation policy.

Hard offset block shadows (`4px 4px 0`) belong only to a world that is genuinely neobrutalist.

## Separators

Space first, tonal step second, one thin low-contrast rule third. Never `border-t` and `border-b`
on every row of a list (doubled lines). A long spec list gets grouped into a few clusters, or
featured items plus a disclosure, not ten ruled rows.

## Cards

Cards only when elevation communicates real hierarchy or the item is a distinct, actionable object.
Otherwise group with space or rules. Never nest cards. In high-density views, metrics breathe in
plain layout rather than boxes.

## Grids and structure

- Grid with `gap` for 2D layout, not flex percentage math (`w-[calc(33%-1rem)]`) or per-element
  margins.
- `minmax(0, 1fr)` on tracks and `min-width: 0` on flex children that hold long text or tables.
- Wide content (tables, code, diagrams) scrolls inside its own `overflow-x: auto` container; the
  page body never scrolls sideways. `width: 100%`, not `100vw`.
- A bento grid has exactly as many cells as content items, with varied sizes and at least some
  cells carrying real imagery or a tinted surface, not six identical text boxes.
- Each layout family (three-up cards, split text-image, full-width quote) appears once per page in
  Persuade mode; no more than two image-text zigzag sections in a row.
- Page container around `max-width: 1280px`-`1400px`, centered, with 16px minimum inline padding on
  mobile (24-32px is better for body text).

## Responsive

- Use the project's named breakpoints for consistency, but collapse a layout where its content
  stops fitting, not where a device preset says. Component-level adaptation uses container queries
  (`@container`), not viewport media queries inside reusable components. A container needs a
  definite width or `container-type` collapses it.
- Declare the small-screen fallback of every multi-column layout in the same component; never
  assume it will work.
- Check the widths between breakpoints (320px, 900px, the gap between 640 and 768). The signature
  failure is correct at the named widths and broken between them.
- Full-height panes use `min-height: 100dvh`, never `h-screen`/`100vh`.
- Text boxes use `min-height`/`max-width`, never fixed height or width: translations grow, and short
  labels grow the most. Test with one long-string locale.
- Critical actions stay in flow or in stable chrome where zoom and scroll cannot clip them.
- Off-screen or collapsed content always has a visible cue: the next item peeking 16-32px past the
  edge, or a disclosure control.

## Chrome

- Navigation renders on one line on desktop and stays at or below about 80px tall; condense labels
  or move to a menu rather than wrapping.
- Sticky header: `scroll-padding-block-start` equal to its height on the scroller.
- Media and backgrounds bleed to the viewport edge; text and controls stay inside margins and safe
  areas (`env(safe-area-inset-*)` needs `viewport-fit=cover`).
- Scrollable dialogs, drawers and menus get `overscroll-behavior: contain`.
- A documented z-index scale for systemic layers (sticky nav, overlay, modal, toast), never
  arbitrary `z-50` sprinkled around.
- Logical properties (`margin-inline-start`, `inset-inline-end`, `text-align: start`) for anything
  that mirrors in RTL; physical left and right only for physical geometry.

## Backgrounds and texture

Backgrounds are surfaces, textured only from the subject's world: a grid needs a real canvas,
blueprint or measuring tool under it; grain is fine on a fixed, `pointer-events: none` layer, never
on a scrolling container (constant repaints). Grain, stripes and dot grids added "to feel designed"
are decoration.
