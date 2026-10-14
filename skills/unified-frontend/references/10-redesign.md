# Redesign and refinement

Misclassifying the mode is the biggest source of bad redesign output. Decide which of these the
request is, and ask once if it is genuinely ambiguous ("Keep the current brand, or start the look
from scratch?").

| Mode | Keeps | Changes |
|---|---|---|
| Refinement | identity, tokens, behavior, copy, everything outside scope | only what was asked |
| Redesign, preserve | brand tokens, logo, voice, IA, URLs | evolves type, spacing, color calibration and motion within the brand |
| Redesign, overhaul | product truth, content, IA, function, URLs, accessibility wins | the visual world, replaced and documented |
| New brand | content and function | everything visual, treated as a new surface |

Never split the difference: polishing a look you were asked to replace produces neither.

## Audit before touching

Document the current state first:

- Brand tokens (colors, type stack, logo treatment, radii) and the dial reading of the existing
  site (variance, motion, density). That reading, not a baseline, is the starting point.
- Information architecture: page tree, primary nav, key conversion paths.
- Content: what is doing work, what is filler.
- Patterns to preserve: signature interactions, a recognizable hero, the copy voice, existing
  accessibility wins (focus states, alt text, keyboard support, contrast).
- Patterns to retire: inherited defaults from `12-dated-defaults.md`, broken layouts, dead links,
  generic stock imagery, performance traps.
- SEO baseline: ranking pages, titles, meta, structured data, Open Graph cards. SEO migration is
  the top redesign risk.

Run `node scripts/check.mjs` on the existing code for a quick inventory of inherited defaults.

## Never change silently

Without explicit approval, do not modify URL structure and slugs, primary nav labels, form field
names and order (analytics and autofill depend on them), section IDs and analytics events, the logo
or wordmark, or legal, consent and cookie copy. A brand that is already purple stays purple.

## Levers, in order

Stop when the brief is satisfied:

1. Typography: the largest visual lift for the least risk.
2. Spacing and rhythm: two registers, section rhythm by role.
3. Color recalibration: unify neutrals, build ramps, keep the brand accent, fix contrast.
4. States and motion: add the missing states first, then the motion the budget allows.
5. Hero and key-section recomposition, using the argument in `08-persuade.md`.
6. Full block replacement, only when a block cannot be saved.

If IA, content and SEO are sound, levers 1-4 deliver most of the value at a fraction of the risk.
If the debt is structural (broken IA, no system, broken mobile), do a full redesign with strict
content preservation. If the brand itself changes, treat it as a new surface.

## Records

Write the new decision sheet where the project keeps design memory (`DESIGN.md` or a style lock),
replacing the old one on an overhaul. On a preserve, update only the lines that changed.
