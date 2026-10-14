# Assets, content and copy

## Show, then tell

A wall of feature cards, each a heading and two sentences, is the default failure. Before writing a
paragraph, ask whether a visual could carry it with a caption: a real chart instead of "fast
analytics", three visual steps instead of a bulleted list, a working mini-version of the feature
instead of its description. Text earns its place where a visual cannot carry the meaning.

## The asset ladder

For every image a section needs, take the first rung available:

1. **Assets the user or brand supplied**: logo, product photos, screenshots, brand kit. Search the
   repo and the brief before anything else. An existing logo is reused byte for byte; never
   recolored, redrawn or replaced without a rebrand request.
2. **An image-generation tool**, if one is available in this session: section-specific assets at
   the right aspect ratio.
3. **Openly licensed real photography downloaded into the repo** (Openverse filtered to CC0 and
   Public Domain Mark, or Pixabay with a key), saved under `assets/`. Record credits in a source
   comment, not on the page.
4. **A labeled slot**: an element with the right aspect ratio and a comment like
   `<!-- needs: hero product photo, 1600x1200 -->`, plus a list of required assets in the hand-off.

Never hotlink placeholder services (`picsum.photos`, `placehold.co`, `pravatar`, `dicebear`,
`shadcn.png`, random Unsplash endpoints). They are the most identifiable artifacts in generated
work and break in production.

Decide photography or illustration per section: factual and physical things (product in use,
people, places) get photography; abstract ideas get illustration from a real illustration source,
or none.

## What not to draw

- **No div-built fake screenshots** (fake dashboards, task lists, terminals). Use a real screenshot,
  a generated image, or a real working component preview. A real component with sample data is a
  preview, not a fake.
- **No hand-drawn pictorial SVG** (faces, scenes, objects, sketch-style illustrations, `feTurbulence`
  grain). SVG doing geometry stays first-class: diagrams, crisp shapes, animated linework, charts.
- **No geometric masks approximating an organic edge**; derive a real alpha matte or skip the effect.
- **No CSS silhouettes standing in for real product imagery** on branded work.

## Logos

- **Brand mark**: preserve what exists. Only on a true cold start with no identity, construct a
  simple geometric mark in the palette (not a letter in a colored box) and export a favicon set.
- **Logo walls** ("works with", "trusted by"): real marks from Simple Icons or the official set,
  monochrome or multicolor, legible in every shipped theme. Logos only, no category labels under
  them. A brand with no available mark is dropped from the wall, never rendered as a text chip
  beside real logos. The wall sits below the hero, not inside it.
- A customer logo wall is a claim: use it only with supplied truth.

## Icons

- Use the project's icon set. Otherwise one library per surface (Phosphor, Tabler, Radix, Lucide,
  Heroicons, Solar and others are all acceptable; none is banned or mandated), chosen so its stroke
  matches the text beside it: about 1.5px at weight 400 rising to 2.5px at 700.
- `currentColor`, recolored per state through CSS; outline by default, fill marks the active state.
- No emoji or Unicode glyphs as icons, unless the brand itself uses emoji (some consumer and chat
  products do), then match its density.
- A missing glyph: install from a second set of matching style, or compose from primitives; do not
  draw a one-off icon path freehand.
- Mirror only direction-dependent icons in RTL.

## Data and claims

Two different things, kept apart:

- **Claims** (stats, ratings, testimonials, customer counts, uptime, awards, prices, press quotes)
  come only from supplied truth: the brief, brand guidelines, the repo, public data you verified.
  When missing, ship a clearly labeled slot ("real metric needed") and list it in the hand-off.
  "Organic-looking" invented numbers like `47.2%` are still invented; they are refused.
- **Sample data inside a product preview** (rows in a demo table, a chart in a mockup) may be
  realistic and varied, with believable, locale-appropriate names and varied dates, and must be
  recognizable as sample where it could be read as a claim.
- No Lorem Ipsum, no John Doe, no invented brands built from tech morphemes (Acme, Nexus,
  SmartFlow), no 555 phone numbers presented as real, no round-number stat bands.
- No AI-invented spec precision (`5.8 mm`, `13.4 lb`) the brand never claimed.

## Copy

- Use the product's own nouns and the subject's vocabulary; one voice and one vocabulary across the
  interface. Match the existing voice on a refinement.
- Headlines carry one specific, checkable fact. Reject anything true of any competitor with the name
  swapped ("The smart way to manage your workflow"). Write three candidates from different angles
  (mechanism, outcome, tension) and pick one.
- Buttons are verb plus object ("Start free trial", "Export report"), never "Submit", "OK" or a
  bare "Learn more". One label per intent across the whole page: nav, hero and footer all say the
  same thing for the same action.
- Links name their destination; no "click here", no two identical "Learn more" links.
- Errors name the problem and the fix, next to where it broke: "Enter a date as DD/MM/YYYY", not
  "Invalid date"; "Unable to save. Check your connection and try again", not "Oops! Something went
  wrong."
- Cut "please" in routine instructions and "successfully" in confirmations. No exclamation marks
  in success messages.
- Settings describe the ON state; never start a toggle with "Don't" or "Disable".
- Empty states point forward: what this is and the one action that fills it.
- Tone by context: warm and light in onboarding and success, neutral in routine settings, calm and
  plain in errors and destructive confirmations, serious and explicit for data loss and security.
- Sentence case for headings and buttons unless the project decided otherwise; one capitalization
  policy per element type.
- No filler verbs (elevate, seamless, unleash, empower, revolutionize, next-gen, game-changer) and
  no stock AI words (delve, tapestry, pivotal, "in today's world").
- No staging: no "not X, but Y" contrasts that only add weight, no forced triads, no one-line
  closers that repeat the point, no fake-humble or mock-poetic labels ("Field notes", "Quietly
  trusted by").
- No em dash as a rhythm device in copy you write; match the brand's rate when its copy uses them.
  En dashes in ranges stay.
- Quotes and testimonials: at most three lines, typographic quotes, attribution with name and role.
- Re-read every visible string before shipping (headlines, labels, alt text, footer, errors). Rewrite
  anything grammatically broken, with an unclear referent, or cute-but-wrong. Plain beats clever.
- For a full prose rewrite of existing text, the humanizer skill is the specialist.
