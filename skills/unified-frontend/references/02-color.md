# Color

## Start from what exists

Reuse the project's tokens and notation. A consistent hex system beats hex with `oklch()` scattered
through it. For a new system, OKLCH is the default because its lightness is perceptually uniform.

## Purple is not the problem

Detectors flag purple/violet (HSL 260-310) and cyan (160-200) above a saturation gate on display
text, plus literals like `#7c3aed`, `#8b5cf6`, `#6366f1` and the `#667eea → #764ba2` gradient. The
problem is purple arriving on a page whose brief never mentioned it. A grape cooperative gets
purple, used well: its own ramp, harmonised neutrals, restrained gradients.

The same logic covers grounds. The cream detector fires only on a timid warm tint (warmth between 6
and 48 on a light ground). Pure white passes, a committed warm ground passes, any cool grey passes.
**Commitment in either direction passes; the timid middle is the failure.** So neither pure white,
pure black nor cream is banned here. The sheet decides, with a reason.

## A system is ramps, not colors

- One neutral ramp, one accent ramp, and only the status ramps the product renders. A second
  accent earns its place only when two things must be told apart at a glance.
- Every step has a job (page background, hover, border, solid fill, body text). Do not generate
  steps nothing consumes.
- **Hold the hue constant in OKLCH** across the ramp; peak chroma mid-ramp and reduce it at both
  extremes; step more finely at the light end (about `0.04`-`0.05` L per step from 50 to 200).
  A deliberate hue drift of up to 10° (warm ramps leaning yellow as they lighten) is a sheet
  decision, not a default. In HSL, ramps that only change lightness are wrong; rebuild in OKLCH.
- Tint neutrals toward the accent with 2-4% of its chroma. A pure `#808080` reads as unconsidered.
  Do not mix warm and cool greys in one project.
- Use the same proportion of each hue's own maximum chroma, not one chroma number for every hue.

## Tokens

Primitives name a value (`--blue-600`) and are never used in components. Semantic tokens name a role
(`--color-text-secondary`, `--color-accent-solid`, `--color-bg-surface`) and are the only tier
components reference. Never borrow a token because its value is right today. If a role has no
token, add one. Call the brand token `accent`, not `primary`, when `--color-text-primary` exists.

## One color, one meaning

- One accent per page, used identically in every section. A rose page does not get a teal badge in
  the footer.
- Anything within 15° of OKLCH hue counts as the same color. Keep status hues at least 15° from the
  accent, and never use the danger hue on a non-destructive action.
- Fill exactly one primary action per view; peers stay neutral. Color goes on the background, not
  the label.
- Never carry meaning by color alone: pair with an icon or a label.

## Contrast is a palette decision

Check it while writing the sheet, then measure the rendered pair (foreground against the surface it
actually sits on, not the page background).

| Pair | Minimum |
|---|---|
| Text | 4.5:1 |
| Large text, at least `24px` or `18.67px` bold | 3:1 |
| UI boundaries, input borders, focus rings, meaningful graphics | 3:1 |

White text on Tailwind `-500` fills fails for indigo (4.47), violet (4.23), red (3.76), blue (3.68)
and green (2.28). Use `-600`/`-700` or darken your own accent. Text on an alpha color (`/50`,
`rgba`, `color-mix` with transparent) must be measured as rendered. Fix contrast by moving
lightness, the channel contrast responds to, not hue. When a fixed brand color cannot pass for its
role, use a known-safe neutral for that pairing and tell the user; do not ship the failing pair.

On colored surfaces, tint secondary text from the surface hue or the foreground, never a flat grey.

## Gradients and light

- No gradient text by default; emphasis comes from weight or size.
- A gradient needs a light source or a material. A symmetric blurred blob behind a hero implies
  light from nowhere, and `overflow: hidden` then slices its soft edge flat. Let atmosphere emanate
  from a real element, bleed past the container, or be one continuous surface.
- Interpolate `in oklab` by default; use `in oklch` when a two-hue gradient goes grey in the middle.
- **Shadows are occlusion, not emission.** A colored, zero-offset halo reads as the object emitting
  light. Keep glow only for things that actually emit (a screen, a sign, a flame), and make it
  emphatic there. Tint ordinary shadows toward the ground hue; never pure black on light grounds.

## Dark mode

- Choose light, dark or both from the use scene, not the category. App UI respects
  `prefers-color-scheme`; a marketing page may lock one theme. Test every shipped theme.
- A page has one theme. Sections do not flip to the inverse mid-scroll unless that flip is the
  signature, done once with a deliberate transition.
- Dark is not inversion. Build elevated surfaces by lightness steps (shadows barely read on dark
  grounds). Lower the accent's chroma and raise its lightness; slightly reduce text weight; widen
  the dark end and remeasure every pair.
- Set `color-scheme` on the root so native controls, scrollbars and the caret follow.
- Token structure that never leaves a theme half-applied: bare `:root` defines the complete
  palette; `@media (prefers-color-scheme: dark)` redefines only tokens (guarded so an explicit light
  choice wins); `[data-theme="dark"]` redefines the same tokens; components use tokens only; `body`
  gets an explicit background token. Pick one switching mechanism and use it throughout.
- Suppress all transitions during the theme swap, or every color transition fires at once.
- `prefers-contrast: more` gets its own value per appearance.

## Wide gamut

`oklch()` chroma beyond sRGB needs an sRGB value declared first, with the vivid one inside
`@media (color-gamut: p3)`.

## Charts

Never ship a chart library's default series colors (Recharts `#8884d8`, matplotlib `#1f77b4`, Plotly
`#636efa`). Map series to the palette, keep one meaning per hue, and label directly where possible.
