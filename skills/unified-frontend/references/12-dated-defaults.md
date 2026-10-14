# The current monoculture

**Snapshot: August-October 2026.** Everything here is perishable: a record of what the default
looked like at one moment, not a permanent list. Use it to ask "did I choose this or inherit it?",
never as a decision. The decision sheet is what survives this file going stale.

## Why it rotates

| Generation | The escape | What it became |
|---|---|---|
| 1 | Inter, Roboto, Montserrat, generic SaaS blue | The original monoculture |
| 2 | "Use warm off-white, an editorial serif, a tracked eyebrow" | Cream grounds, italic serif heroes and eyebrows are now top detector rules |
| 3 | "Use hairlines instead of heavy shadows" | Models did both; hairline plus wide shadow is a named defect |

When the eyebrow got flagged, models restyled it instead of deleting it; the avoidance has its own
signature. If this skill's own recommendations were followed uniformly, they would become
generation 4. Derivation from a specific brief does not converge, because briefs do not.

## Visual defaults (the mode, right now)

**Palette.** Purple and violet (HSL 260-310) and cyan (160-200); literals `#7c3aed`, `#8b5cf6`,
`#a855f7`, `#9333ea`, `#6366f1`; the `#667eea → #764ba2` gradient. Second wave: warm cream grounds
near `#F4F1EA` with brass, clay, oxblood or ochre accents and espresso text (`#1a1714`); near-black
with one acid-green or vermilion accent; broadsheet layouts with hairlines and zero radius.

**Type.** Older wave: Inter, Roboto, Open Sans, Lato, Montserrat, Arial, Helvetica. Newer wave:
Fraunces, Instrument Sans and Serif, Geist, Mona Sans, Plus Jakarta Sans, Space Grotesk, Recoleta.
Likely next: the faces anti-slop skills now prescribe as the escape (Satoshi, Cabinet Grotesk,
Manrope, Outfit); not yet in detectors, but the pattern of generation 2 says they will be. Geist
recurring is a framework fact (the Next.js and shadcn default), not taste.

**Structure.** Sticky translucent header with backdrop blur; pill badge above the H1; oversized
centered headline; solid plus outline CTAs of equal size; logo cloud; three icon-in-tinted-square
cards; round-number stat band; three-tier pricing with a scaled "Most popular" middle; FAQ
accordion; centered final CTA; four-column footer. Floating glass pill nav. A mandatory word-by-word
"tagline reveal" section.

**Surface.** `rounded-2xl` on everything regardless of size; border and shadow together; Tailwind's
default shadow scale everywhere; `py-20`/`py-24` on every section.

**Effects.** Gradient text; blurred gradient orbs behind the hero; colored glow shadows in the
accent's hue; glassmorphism cards; decorative grid backgrounds; `hover:scale-105`;
`transition-all duration-300` or `duration-700`; fade-up on every section.

**Assets.** One icon library at mixed rendered stroke widths; placeholder image hosts; `shadcn.png`
avatars; untouched chart library colors; div-built fake dashboards in the hero.

**Copy.** "Elevate", "seamless", "unleash", "next-gen"; "The smart way to X"; "Quietly trusted by";
"Field notes"; staged "not X, but Y" contrasts; dash-heavy rhythm; version stamps and locale or
weather strips as decoration.

## Detector rule IDs

Useful when reading detector output or other rulesets: `overused-font` · `ai-color-palette` ·
`cream-palette` · `gradient-text` · `dark-glow` · `radial-halo` · `icon-tile-stack` ·
`hero-eyebrow-chip` · `kicker-above-heading` · `numbered-section-labels` · `italic-serif-display` ·
`oversized-h1` · `flat-type-hierarchy` · `extreme-negative-tracking` · `monotonous-spacing` ·
`nested-cards` · `gpt-thin-border-wide-shadow` · `repeating-stripes-gradient` ·
`codex-grid-background` · `side-tab` · `border-accent-on-rounded` · `bounce-easing` ·
`pulsing-dot` · `blinking-cursor` · `marquee` · `image-hover-transform` · `broken-image`

## Contested: positions this skill took

Sources actively disagree on these. The position below is this skill's; write the project's own in
the decision sheet and stay consistent.

| Topic | Position here |
|---|---|
| Glassmorphism | Functional only (an overlay above real content), never two translucent layers stacked, solid fallback under `prefers-reduced-transparency` |
| Border plus shadow | One elevation policy per surface; an invisible forced-colors border does not count |
| Radius | A project constant chosen in the sheet, nested concentrically |
| Eyebrows | Zero decorative ones; a label survives only when it carries information |
| Easing and duration | One house curve per project; durations by interaction size |
| System fonts | Fine for UI and body text; not as an own-world display voice |
| Side stripe | Not decoration on cards; correct for severity in alerts, logs and callouts, and for the selected nav item |

## Refreshing this file

Every few months, or when output stops looking like this: generate five pages from five deliberately
unrelated briefs with no styling guidance, and diff them. Anything identical across all five is the
current mode. Rewrite the sections above and update the date. If last cycle's recommendations show
up in the diff, remove them from this skill rather than promoting them.
