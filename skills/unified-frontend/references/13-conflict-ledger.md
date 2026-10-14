# Conflict ledger

Every place the source skills contradicted each other, what each said, and the resolution this skill
uses. Load this only when a rule seems to clash with another installed skill or with a source.

Source shorthand: **AS** Anti-Slop (AJONAI) · **IM** impeccable · **TS** taste-skill
(design-taste-frontend and its variants) · **TM** tastemaker · **IF** interfaces better-* skills ·
**LP** landing-page-design · **WD** web-design-engineer · **HU** humanizer.

The deciding principle in almost every row: a rule that bans or mandates a specific value by name is
perishable and loses to a rule that derives the value from the brief, unless the rule protects users
(the floor), in which case it wins outright.

| # | Topic | What the sources said | Resolution |
|---|---|---|---|
| 1 | Em dash | TS, TM, HU, LP: total ban (LP even bans hyphens in text). IF: use real em and en dashes instead of `--` and hyphens. AS: refuses a total ban; correct punctuation is for the reader. | No em dash as a rhythm device in copy you write; match the brand's existing rate (HU). En dashes in numeric ranges stay (IF, AS); never a hyphen there. Hyphens stay in compound words (LP's hyphen ban rejected). |
| 2 | Eyebrow labels | IM: total ban. TS: max one per three sections. AS: contested (ban vs ration). | Zero decorative eyebrows. A label survives only if deleting it loses information (date, status, category). |
| 3 | Fonts by name | TS: recommends Geist, Satoshi, Cabinet Grotesk; bans Fraunces and Instrument Serif as defaults; discourages Inter and serifs. LP: only Geist, Manrope, Geist Mono, Poppins; never Inter, Roboto, Arial, Helvetica. WD: Inter, Roboto, Arial, Fraunces, system-ui as display are slop. AS: no blanket bans; Geist is itself monoculture; system stack fine for body. IF: never propose a new typeface unless asked. | No whitelist or blacklist. Faces derived from the subject with a written reason; the overused list only raises the bar for a display voice. System stacks fine for UI and body. Never change type on an existing project unless asked. |
| 4 | Serif vs sans | TS: serif very discouraged. IF: serif headline over sans body reads deliberate. AS: the decision comes from the subject. | Subject decides. Neither "creative means serif" nor "serif banned". |
| 5 | Italics and font count | LP: never italics, one typeface per site, no weight 900. TS: emphasis via italic or bold of the same family. IF: rarely more than three fonts. | Italic allowed for emphasis in the same family. Usually two families, three at most; one is often right for app UI. Weight follows the face and subject. |
| 6 | Placeholder images | TS: `picsum.photos/seed/...` as default. TM: fetch Openverse CC0 into the repo. AS: placeholder hosts are the most identifiable artifact (checker error). WD: honest labeled placeholder. | Asset ladder: supplied, then generated, then openly licensed photos saved locally, then a labeled slot. Never hotlinked placeholder services (checker extended to all of `picsum.photos`). |
| 7 | Numbers and claims | TS, LP: use "organic, messy" numbers like `47.2%` instead of round fake ones. WD, IM, AS: never fabricate data; claims from supplied truth. | Claims only from supplied truth, else a labeled slot. Realistic sample data allowed inside product previews, marked as sample where it could read as a claim. Messy-looking invented stats are still invented. |
| 8 | Motion volume | TM: GSAP on every screen; a page with zero motion is a skipped step. LP: every element fades up 800ms+. TS: "motion claimed, motion shown"; dial-driven. IM: one authored moment, no identical entrance on every section. AS: a counted budget; `none` is legitimate. IF: no animation on frequent interactions. | Budget by mode (`06-motion.md`), written in the sheet. Feedback states are always present, so no page is inert; decorative motion is optional and purposeful. Uniform section fade-ups refused. |
| 9 | Easing and duration | LP: `transition-all duration-700 cubic-bezier(0.32,0.72,0,1)`. TS: `transition: all 0.3s cubic-bezier(0.16,1,0.3,1)`. IF: `cubic-bezier(0.2,0,0,1)`, 150-300ms, never `all`. AS: three canonical curves, all conventions. | One house curve per project, default `cubic-bezier(0.2,0,0,1)`. Durations by interaction size. `transition: all` refused everywhere. |
| 10 | Press feedback | IF: scale `0.96`. AS: `0.97`. TS, LP: `scale(0.98)` or `translateY(1px)`. | `0.96` on buttons, `0.98` on large surfaces, never on disabled. |
| 11 | Hover | LP: slight scale or translate on hover. AS, IM: `hover:scale-105` and image hover transforms are tells. IF: hover only behind `(hover: hover)`. | Hover is a color or background shift behind `(hover: hover)`; no scale on cards or images. |
| 12 | Springs | TS: spring `stiffness 100, damping 20`, no linear easing. IF: `bounce: 0` always. AS: damping 1.0 default, bounce only for momentum gestures. | Critically damped (`bounce: 0`) by default; overshoot only when a gesture carried momentum. |
| 13 | Gradient text | LP: mandatory gradient on hero headings. IM, AS, TS, WD: gradient text is a tell. | Refused unless the brief asks for it. |
| 14 | Gradient backgrounds | LP: never gradients in backgrounds. TS: bento cells need a brand gradient or image. AS: gradients need a light source. | Allowed when they depict light or a material; interpolate in OKLab or OKLCH; never symmetric orbs from nowhere. |
| 15 | Pure black and white | TS: never `#000` or `#fff`. LP: dark palette includes `#000000`. AS: committed choices pass; only the timid middle fails. TS: cream grounds banned for premium briefs. | Nothing banned; the sheet commits with a reason. Pure black fine where the scene earns it; the timid near-cream by inertia is the failure. |
| 16 | Ramp hue | AS: shift hue 5-10° across lightness. IF: hold the hue constant in OKLCH. | Constant hue in OKLCH by default (OKLCH already corrects perceived drift); deliberate drift up to 10° is a sheet decision. |
| 17 | WCAG large text | TS: large text is 18px+. AS, IF: 24px or 18.67px bold. | 24px or 18.67px bold. TS's 18px would pass text that AA fails. |
| 18 | Radius | IM: cards 12-16px, pills for small controls. LP: only Tailwind values. TS: all-sharp, all-soft (12-16) or all-pill. AS: no canon; one project constant from the subject. | One radius system from the sheet; pills for small controls; concentric nesting. |
| 19 | Nested radius cutoff | IF: outer = inner + padding, separate surfaces past 24px. LP: inner = outer − gap when the gap is under 32px; square below 2px. | Same formula; separate surfaces past 24px of padding; square when the inner result is 2px or less. |
| 20 | Border plus shadow | IM, AS: one elevation policy; hairline plus wide shadow is a defect. IF: shadows for elevation, borders for structure, a transparent border under shadows for forced-colors. | One policy per surface; the invisible forced-colors border does not count. |
| 21 | Side stripe borders | IM: ban above 1px. WD: cliché. AS: contested; correct for severity in status regions. LP: never border on one side of a card. | Refused as card decoration; allowed for severity (alerts, logs, callouts) and the selected nav item. |
| 22 | Icons | TS: Phosphor, HugeIcons, Radix, Tabler; Lucide discouraged; never hand-roll SVG. LP: Phosphor, Solar, Iconamoon; never Material. TM: lucide-animated on shadcn, Iconify by mood. IM: real library or authored SVG. IF: stroke matches text weight. | The project's set, else one library per surface matched to text weight. No library banned by name. No emoji icons, no freehand pictorial SVG; simple geometric authored SVG is fine. |
| 23 | Asking the user | WD: stop and wait for confirmation of the system and a v0. TS: one question only if the read diverges, else proceed. LP: ask in one batch, never stall. TM: ask which screens are in scope. IM: init interview when no product context. | Infer, declare the sheet, proceed. One batched question only for decisive ambiguity. Stop for approval only when a plan was requested or an existing visual world would be replaced. |
| 24 | Dark mode | TS: both modes mandatory for consumer pages. IM: pick light or dark from the use scene, not the category. TS: one theme per page. | Theme from the use scene; app UI follows the system setting; a marketing page may lock one theme; never flip mid-page unless that is the signature. |
| 25 | Page structure | LP: a fixed 12-part structure with FAQ of 6-12, identical final CTA and a mandatory tagline-reveal section. AS: that template is the monoculture. TM: derive from a narrative arc and rotate named macrostructures. | Structure from the argument (hook, problem, solution, how, proof, close) and a named shape chosen for it. LP's parts become jobs, not slots; no mandatory tagline reveal. |
| 26 | Hero contents | LP: one proof signal (logo strip, stat) above the fold. TS: trust strips and taglines banned inside the hero; logo wall directly below. TM: one job, one visual. | Hero: promise, one sentence, one primary action plus one different-intent secondary, one visual. Proof sits directly below the hero. |
| 27 | Centered hero | TS: avoid centered when variance > 4. AS: the centered oversized H1 is part of the template. | Alignment follows content; centered for manifesto or announcement pages. |
| 28 | Breakpoints | TS: standardize 640/768/1024/1280/1536. IF: breakpoints come from content; container queries for components. | Named breakpoints for consistency, collapse where content breaks, container queries inside components, test between breakpoints. |
| 29 | Section spacing | TS: hero top padding max about 96px. TM: pivotal sections 128-192px. LP: fixed token list up to 96px. AS: rhythm varies by role. | Not a conflict once scoped: modest hero top padding; section rhythm 64-160px+ varied by role on landing pages. |
| 30 | Dials | TS: three dials (8/6/4 baseline). WD: five dials. TM: four. IM: none, modes instead. | Modes plus the decision sheet are primary; three optional dials as shorthand (`01-decision-sheet.md`). No default baseline: values come from the brief. |
| 31 | Component sourcing | TM: pull from registries rather than hand-roll. TS: install the official design-system package. IF: native element first, then the project's own. | Native, then project, then official system, then restyled registry, then hand-rolled. |
| 32 | Product UI motion | TM: staggered list and table entrances on data load. IM: no orchestrated page-load sequences in product. IF: never stagger routine interactions. | No staggered entrances on routine loads; animating a newly inserted row is fine. |
| 33 | Custom scrollbars | IM craft floor: theme the scrollbar. IM operate: do not reinvent scrollbars. | Tint native scrollbars (`scrollbar-color`, `scrollbar-width`); never replace scrolling behavior. |
| 34 | Verification depth | TS: 60-item pre-flight every time. TM: many scripts plus 11 critique scores. IM: one batched inspection and one confirm, then stop. WD: browser acceptance only when asked. | One batched verification round plus one confirm; the checker once; the "Before you finish" table. Full browser acceptance when the user asks for QA. |
| 35 | Review output | WD, IM: 0-10 scores per dimension. IF: severity table and Block or Approve verdict. AS: co-occurrence, "inherited" not "AI". | Severity findings table and verdict always; scores only when asked; co-occurrence framing. |
| 36 | Default stack | TS: React or Next with Tailwind v4 and Motion by default. WD: inline React plus Babel HTML artifacts. TM: detect the stack first. | Use the project's stack. With no project, choose the lightest stack that fits the deliverable and say so; check `package.json` before any import. |
| 37 | Mono numbers in dense UI | TS: `font-mono` for all numbers at density 8+. IF, AS: `tabular-nums`. IM: mono is not a costume. | `tabular-nums` on the text face; mono only for code, IDs and measurements. |
| 38 | Copy hyphens and orphans | LP: no hyphens anywhere, no orphan words. IF: `text-wrap: pretty`. | Hyphens stay in compounds; `balance` on headings and `pretty` on paragraphs prevent orphans. |

## Not conflicts, kept from each source

- AS: the decision sheet, the "tell is brief-invariant" principle, interaction states first, the
  checker, co-occurrence auditing.
- IM: modes per surface, the brief wins, refinement vs redesign semantics, the browser surfaces
  nobody themes, bounded verification.
- TS: brief inference and the design read, official design systems, redesign protocol, hero and
  section discipline, motion engineering rules (`useMotionValue`, no scroll listeners).
- TM: grounding in real references and real assets, structure from a narrative arc, rotating page
  shapes across projects, project memory, the color contract.
- IF: exact craft values, evidence-based review, escalation triggers, the cheaper-fix order.
- LP: one offer, one audience, one action; intake; conversion rules; ship requirements; SEO.
- WD: verify facts before designing, four positioning questions, placeholder honesty.
- HU: the copy tells (staging, forced triads, inflation, stock words) and matching the writer's
  own rate of a pattern instead of stripping it.
