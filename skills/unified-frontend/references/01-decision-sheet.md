# The decision sheet

Fill this before writing markup. Front-loading constraints into the first generation is the only
intervention with evidence behind it: correcting afterwards underperforms starting from a stronger
instruction, and regenerating does not escape the default because the default is the mode of the
distribution.

## Before the sheet: read the brief

Collect these signals, inferring where you can instead of asking:

1. **Surface kind**: landing, pricing, portfolio, app screen, dashboard, docs page, article,
   component, deck.
2. **Audience and scene**: who, on what device, at what distance, in what light, how often.
   A procurement panel, a recruiter scanning, a nurse on night shift and a teenager on a phone get
   different answers.
3. **Vibe words and references** the user gave (named products, URLs, screenshots). A reference is
   evidence to extract from (palette, type, macrostructure, density), never pixels to copy.
4. **Existing assets**: logo, colors, type, photography, a design system. These are input, not
   optional.
5. **Quiet constraints**: accessibility-first audience, public sector, regulated industry, kids,
   trust-first commerce. These outrank aesthetic preference.

Then state one line: *"Reading this as: [surface] for [audience], in [mode] mode, leaning toward
[system or visual direction]."*

For each screen or section, also answer four positioning questions: its **narrative role** (hero,
transition, data, proof, close), **viewing distance** (phone, laptop, projector), **visual
temperature** (quiet, authoritative, warm, energized, playful, somber) and a **capacity check**
(does the real content fit this layout, or will it overflow or look sparse).

## The lines

### SUBJECT

One sentence: what this is, who it is for, its single job. "A landing page" is not a subject. "A
booking page for a two-chair barbershop in a town of 4,000, used mostly on phones by people
standing outside" is one, and it already implies large tap targets, a phone number above the fold
and no logo cloud. **Test:** could the sentence describe a competitor? Then it is not pinned.

### MODE

Persuade, Operate, Read or Experience, chosen for this surface. See SKILL.md.

### GROUND

3-6 concrete nouns from the subject's world. A seed company has germination rates, seasons, soil,
packet dimensions and Latin binomials. A mastering studio has LUFS, VU ballistics, rack units and
patch bays. This is where non-generic choices come from; a style library gives everyone the same
answers.

### PALETTE

4-6 hex values, each with a role: ground, surface, ink, ink-2, rule, accent. Name the neutral's hue
bias (warm reads organic, cool reads technical; pick on purpose). Semantic colors are separate from
the accent. Check contrast now, not in a later audit. **Test:** if the palette could be guessed from
the industry, it is the first reflex; if it could be guessed from "industry but not the obvious"
(fintech but not navy and gold, so terminal green on black), it is the second reflex. Both are
inherited.

### TYPE

Display, text and optional utility roles, named faces, one sentence of why each. "Plex because the
subject is engineering documentation and Plex is IBM's own technical type system" is a decision;
"Plex because it looks clean" is a preference, and preferences converge. **Test:** would this
pairing appear on another project of yours this month? Then it is a habit.

### SPACE

Two registers with different numbers: intra-component (label to input, icon to text, card padding)
and section rhythm. One value doing both claims that everything has equal weight.

### SHAPE

One radius system and how it nests; one elevation policy (tonal step or shadow). Published rulesets
prescribe 0, 8-12, 12-16 and 32px as "correct", so there is no canon: pick the value the subject
implies (a form is 4px, a toy might be pill-shaped) and enforce consistency against it.

### MOTION

House curve, duration band, and a count of authored moments, or `none`. `none` is legitimate and
often right for keyboard-driven tools. Interaction feedback (press, focus, hover color) is part of
the floor and does not count against the budget.

### SIGNATURE

The one element the page is remembered by, taken from GROUND. A real specimen photographed on the
subject's equipment, a live calculation the visitor can drive, a data view only this subject could
produce, a typographic treatment of the subject's real vocabulary. Not a gradient, blur, hover lift
or animated counter: those are effects, available to everyone. Spend boldness once; everything
around the signature stays quiet.

## Optional dials

Some users think in numbers. These are shorthand for lines of the sheet, never a replacement for it.

| Dial | 1-3 | 4-7 | 8-10 |
|---|---|---|---|
| VARIANCE | symmetric grid, centered, equal widths | offsets, mixed aspect ratios, left-aligned heads over centered data | asymmetric fractions, large empty zones, masonry |
| MOTION | feedback only | state transitions plus one authored entrance | choreographed scroll or gesture sequences |
| DENSITY | gallery, generous section rhythm | everyday app spacing | cockpit: tight padding, rules instead of cards, tabular numbers |

Typical starting points, always overridden by the brief:

| Surface | VARIANCE | MOTION | DENSITY |
|---|---|---|---|
| Trust-first, public sector, regulated | 3 | 2 | 5 |
| Minimal, editorial, calm | 5 | 3 | 3 |
| Mainstream product landing | 7 | 5 | 4 |
| Agency, experimental, Awwwards-leaning | 9 | 8 | 3 |
| App UI, dashboard | 3 | 2 | 6-8 |
| Docs, article | 4 | 1 | 3 |
| Redesign, preserve | match existing | +1 | match existing |
| Redesign, overhaul | +2 | +2 | match existing |

High variance always collapses to a single, explicit column below 768px.

## Worked example

**Brief:** "a landing page for our AI meeting notes tool"

**Inherited sheet**, which is what the default produces. Recognize it and discard it:

```
SUBJECT    an AI meeting notes SaaS for teams
GROUND     productivity, speed, focus
PALETTE    indigo accent on white, slate neutrals
TYPE       one geometric sans everywhere
SPACE      24px everywhere, py-24 sections
SHAPE      rounded-2xl, border + shadow
MOTION     fade-up on every section
SIGNATURE  gradient headline
```

Every line is answerable without knowing anything about the product.

**Derived sheet:**

```
SUBJECT    a notetaker for clinical research coordinators running consent visits, who cannot
           look at a screen during the visit and must produce an auditable record afterwards
MODE       Persuade
GROUND     consent forms, protocol numbers, timestamps, initials boxes, carbon copies,
           the 30-day audit window
PALETTE    ground #FCFCFA (warm-neutral, paper bias); surface #FFFFFF; ink #1A1916;
           ink-2 #57544C; rule #DEDAD0; accent #7A5C1E (archival ink brown);
           danger #8C2F1E reserved for audit-integrity failures
TYPE       display: a document serif at modest size, because the artifact replaced is a
           printed form; text: a humanist sans for screen comfort; utility: mono for protocol
           IDs and timestamps, tabular-nums always
SPACE      intra 6/10/16px; section rhythm 72px, one 120px break before the audit-trail section
SHAPE      radius 4px only, a form rather than a card UI; elevation by rule and tonal step
MOTION     house ease-out, 120-180ms; two moments: the recording indicator and row insertion
           in the transcript
SIGNATURE  a real transcript typing itself into a form's initials-and-date boxes
```

The second sheet could not be written for another product. It also lands on a warm ground and a
serif, the same surface as the cream-and-serif cliché, but it got there from the subject's
materials, with a 4px form radius the cliché would never produce. Derivation landing near a common
answer is fine. Lookup landing there is not.
