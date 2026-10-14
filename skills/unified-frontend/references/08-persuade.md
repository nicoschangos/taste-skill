# Persuade and Experience surfaces

Landing pages, marketing sites, pricing, campaigns (Persuade); portfolios, galleries, showcases
(Experience).

## Intake

Infer what you can from the brief and repo; ask one batch only for what is missing and decisive.
If something cannot be answered, assume, state the assumption in one line and keep building.

- **Purpose**: the one primary action (trial, demo, buy, waitlist, download), the exact offer, what
  counts as a conversion.
- **Audience**: who, the problem they bring, their top objections, the traffic source (ads, search,
  social, email) and what they already know when they land.
- **Proof**: which logos, testimonials, numbers, case studies, screenshots and guarantees actually
  exist. Only these may appear as claims.
- **Constraints**: brand voice, assets, mobile priority, regulated wording.

## The page's job

One offer, one audience, one primary action. Rules that hold everywhere:

- Match the message to the source: a page fed by an ad mirrors that ad's promise and tone.
- One primary CTA. Never competing CTAs above the fold. A secondary CTA must have a different
  intent; two labels for the same intent ("Get started" and "Sign up free") are a failure.
- Benefits before features, and specific: "Cut weekly reporting from 4 hours to 15 minutes", not
  "Save time and streamline".
- Put proof directly beside the claim it supports, not buried at the bottom.
- Reduce risk with at least one real reversal (free plan, no card, cancel anytime, refund terms)
  when the offer has one.
- Objections are content: answer them where they arise, or in a dedicated section placed earlier
  for high-friction offers.

## Structure comes from the argument

The template (pill badge, centered H1, two CTAs, logo cloud, three icon cards, stat band, three-tier
pricing with a scaled middle, FAQ, centered final CTA, four-column footer) is the monoculture. Do
not start from a section list. Start from the argument:

1. **Hook**: the promise, for whom.
2. **Problem or stakes**: what is broken, specific to this product.
3. **Solution or mechanism**: how it fixes it, shown rather than asserted.
4. **How it works**: a handful of concrete steps, or folded into the solution for simple products.
5. **Proof**: real evidence only.
6. **Close**: the ask, echoing the hook's promise.

At least four distinct beats; if you merge or skip one, say so. Read top to bottom, the page answers
in order: who is this for and what is promised, what is wrong, how this fixes it, why believe it,
what to do now. FAQ, pricing, risk reversal and a final CTA appear when the offer needs them, as
jobs inside this arc, not as mandatory slots.

Then pick a whole-page shape that carries this argument, by name, and say why. Rotate shapes across
projects instead of defaulting to one:

| Shape | When |
|---|---|
| Feature bands | Hero, then one full-width band per capability, each led by a real visual (not a card grid) |
| Bento showcase | Many small capabilities; mixed tile spans carry the rhythm; exact cell count |
| Editorial index | Portfolios, studios, publications; content-led with generous type and rules |
| Long-scroll narrative | The arc told beat by beat when the product must educate or overcome skepticism |
| Stat-led | The story is genuinely quantitative and the numbers are real |
| Gallery grid | The imagery sells: commerce, food, travel, physical product, photography |
| Product workbench | Seeing it work is the pitch: the hero is the product in use |
| Split diptych | A persistent statement column beside scrolling content |
| Conversational FAQ | A trust gap or one dominant objection; answers carry proof and CTA |
| Manifesto | Type-forward, one point of view, few images |
| Catalogue | Many SKUs, plans, specs or releases set with editorial care |
| Poster fold | One full-bleed art-directed first screen, quieter below |
| Minimal conversion page | High-intent traffic and a short offer (download, waitlist) |
| Comparison page | Search intent like "X vs Y" or "alternatives to X" |

On a vague brief with no signal, offer three shapes from different families (grid-led, document-led,
poster-led) instead of defaulting.

## The hero

One job, one visual focus.

- One sharp promise (headline, at most two lines on desktop), one short supporting sentence (about
  20 words, at most four lines), one primary action plus at most one secondary of a different
  intent, and one product-relevant visual.
- The hero fits the first viewport with the CTA visible. If it does not, reduce the type scale or
  cut copy. Plan the headline size together with the visual.
- No mini-dashboard of the whole site: no workflow rails, metric sidebars, floating badges, trust
  micro-strips, pricing teasers, version labels, taglines under the CTAs or decoration text strips.
  Move them to the sections below.
- A real visual, not text on a gradient blob. Alignment follows the content: left text with a right
  visual, a split, an asymmetric composition, or centered when the message itself is the design
  (manifesto, launch announcement).
- A label above the headline only if it carries real information (a launch date, a status).

## Section craft

- Each section: a short headline, a short supporting line, and one visual or one action. Anything
  more is justified by the section's job.
- No data dumps on a marketing page: top three to five highlights and a link to the full list.
  More than five items move to a better component (grouped columns, cards with images, tabs,
  scroll-snap rows, a single marquee).
- One layout family once per page; no more than two image-text zigzags in a row; no section
  header split into a big left headline and a small floating right paragraph unless the right
  column carries a real visual or control.
- Quotes at most three lines with full attribution. One marquee per page at most.
- One theme for the whole page.

## Experience mode

The artifact leads from the first viewport; the interface recedes. Navigation is minimal and
reachable. Motion may be choreographed, still with a stated purpose per sequence and a
reduced-motion path. Real work, real images; captions are functional, not poetic.

## Ship requirements

Things that make a page feel unfinished when missing: privacy and terms links that resolve, a
branded 404, client-side validation for required fields and email format, a skip link, cookie
consent where the jurisdiction requires it, a favicon set, `<title>`, meta description,
`og:image` and social tags, alt text, semantic landmarks, the current page marked in navigation, a
way back from every page, a copyright year that is current, no `#` links.

## SEO and answer engines

- `noindex` ad-only campaign pages and time-bound offers.
- Index evergreen pages whose promise matches search intent: a clear title and meta description,
  internal links from the home and feature pages, and real questions answered in plain
  question-and-answer form (with FAQ structured data when appropriate).
- On a redesign, preserve slugs, titles and structured data unless the change is requested.

## Build order

Hero, then the solution and proof beats, then the rest, section by section with reviewable diffs.
Do not regenerate the whole page on each iteration.
