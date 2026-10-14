# Operate and Read surfaces

## Operate: app UI, dashboards, settings, tools, admin

The failure here is not blandness but strangeness without purpose: decorated buttons, mismatched
controls, gratuitous motion, display faces on labels, invented affordances for standard tasks. The
test is whether a user fluent in the category trusts the interface at once. Familiarity is a
feature; the tool should disappear into the task, and brand lives in precise details.

### System first

- Use the project's component library, or the official system the product lives in (Polaris for
  Shopify admin, Atlassian for Jira-like tools, Fluent or Carbon for enterprise, Primer for
  developer tools, GOV.UK or USWDS for public services). Install the official package rather than
  recreating its CSS, and do not import its tokens only to override most of them. One system per
  project.
- Behavioral primitives (dialog, popover, menu, select, combobox, toast, command palette, drag and
  drop, virtualization) come from a maintained headless library (Radix, React Aria, Headless UI,
  the platform's `<dialog>` and popover API), restyled to the tokens. Hand-rolled versions get focus,
  dismissal and positioning wrong.
- A component pulled from a registry or library does not get a pass on the floor: restyle it and
  verify its states in the same pass. Never ship shadcn/ui or any kit in its default look.

### Type, color, layout

- One well-tuned sans is often right for the whole UI; mono for code, IDs and measurements. No
  display faces on labels, buttons or data.
- A fixed `rem` scale with a tight ratio (1.125-1.2); no fluid headings in product UI.
- Restrained color: the accent marks primary actions, current selection and state, never
  decoration. A second neutral layer separates sidebars, toolbars and panels from content. A
  standard state vocabulary (hover, focus, active, disabled, selected, loading, error, warning,
  success, info) defined once and used everywhere.
- Responsive behavior is structural: collapse the sidebar, adapt the table, change columns.
- Standard navigation patterns are virtues: top bar plus side nav, breadcrumbs, tabs, command
  palette. Consistency over surprise; the same action looks the same on every screen.
- Theme native scrollbars with `scrollbar-color` and `scrollbar-width`; do not replace scrolling
  behavior or standard controls with custom ones.
- Modals are not the first answer. Prefer inline editing, progressive disclosure or a side panel;
  use a modal when the task needs interruption or protected focus.
- Overlays escape clipping containers: `<dialog>`, the popover API, `position: fixed` or a portal.

### Density and data

- Density is allowed and often needed. High density means rules instead of cards, tight padding,
  and `tabular-nums` on every number.
- Tables: numbers right-aligned, text left-aligned; one thin rule under the header, no full grid;
  a sticky header on long tables; row hover on clickable rows; empty, loading and "no results for
  this filter" states that differ from each other. Use a real table library (TanStack Table, AG
  Grid) for sorting, virtualization and column management.
- Charts: palette-mapped series, direct labels where possible, a text alternative or data table,
  no decorative sparklines or progress rings standing in for content.
- Every component ships default, hover, focus, active, disabled, loading and error. Skeletons, not
  spinners, inside content. Empty states teach the interface.

### Motion in product UI

Feedback and state only. Frequent actions instant or 150ms or less on color and opacity; panels,
tabs and drawers 150-250ms. No orchestrated page-load sequences and no staggered entrances on
routine data loads; animating a newly inserted row is fine. Users are in flow; never make them wait
for choreography.

### Light, dark and the scene

Pick themes from the real usage scene (an operator in a dark control room, an accountant on a bright
office monitor, a nurse at 3am). An app follows the system setting and offers a toggle when either
mode loses something important.

## Read: docs, articles, guides, help, changelogs

Structure for comprehension first, then make the reading worth staying in.

- Measure 60-75 characters, body 16-18px at line-height 1.5-1.7, generous paragraph spacing.
- A clear heading hierarchy that doubles as navigation: a table of contents for long pages, anchor
  links on headings, `scroll-padding-block-start` under sticky chrome, the current section
  highlighted.
- Code blocks scroll horizontally inside their own container, use the project's mono at a size that
  matches body optically, and have a copy button with a visible confirmation.
- Callouts by meaning (note, warning, danger) with an icon and a label, not color alone. A side
  stripe is acceptable here because it carries severity.
- Dates, versions and authors where readers need them; a "last updated" date on docs.
- Search, previous and next links, and a way back to the index.
- Motion near zero: no scroll reveals on paragraphs.
- A docs index is still Read, not Persuade: no hero theatrics.
