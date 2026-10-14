# States and accessibility

Read this by default when building UI. A screenshot of generated UI usually looks fine; it falls
apart the moment someone interacts with it, because it is inert. When candidate tells were
adversarially audited, missing interaction states survived more often than any visual tell. Ship
the absent states before restyling the present ones.

## Criteria, not conventions

These are requirements whatever the style guide says. A density or voice you dislike is not a
finding; a control with no accessible name is.

## Native elements first

`<button>` for actions, `<a href>` for navigation (so cmd-click and middle-click work), real
`<input>`, `<select>`, `<dialog>`, `<details>`. A `<div onClick>` has no keyboard access and no
role. ARIA that duplicates a native role (`role="button"` on a button, an `aria-label` repeating the
visible text) is a no-op; an `aria-label` must start with the visible label.

## The states

| State | Requirement |
|---|---|
| Hover | Color or background shift behind `@media (hover: hover)` (Tailwind 4's `hover:` already is; Tailwind 3's is not). No scale on cards or images. |
| Active | Feedback on pointer-down: scale `0.96` on buttons, `0.98` on large surfaces, `100`-`150ms` ease-out, never on `:disabled`. Set `-webkit-tap-highlight-color: transparent` where the control draws its own press. |
| Focus | `:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }` or the browser ring, at 3:1 against adjacent colors. `:focus-within` for compound controls. Never `outline: none` without a replacement. |
| Disabled | Still readable (non-text contrast where it carries information), `cursor: not-allowed`, no hover response, and an explanation of why somewhere. Prefer keeping a submit button enabled and validating on submit. A tooltip on a natively disabled control is unreachable: put text beside it or use `aria-disabled`. |
| Loading | Anything over about 300ms shows pending state in place. Skeletons shaped like the real layout when the shape is known; a submit button stays enabled until the request starts, then shows progress. |
| Empty | Every list, table, search and dashboard has a zero state with a reason and a next step. "No results for this filter" differs from "nothing here yet". |
| Error | What failed, how to fix it, next to the field, in the interface's voice; focus moves to the first error on submit; announced via a polite live region. Never `window.alert()`. |
| Success | Confirmed plainly, without exclamation marks. |

Destructive actions are never immediate: an undo window is better than a confirmation, and a
confirmation names the action and object ("Delete project"), never "Are you sure?". Confirmations
on non-destructive actions train people to click through the real ones.

## The surfaces nobody themes

The cheapest signal that a page was built rather than assembled:

```css
:root            { color-scheme: light dark; caret-color: var(--accent); }
::selection      { background: var(--accent-soft); color: var(--ink); }
:focus-visible   { outline: 2px solid var(--accent); outline-offset: 2px; }
a                { text-underline-offset: 3px; text-decoration-thickness: 1px; }
.tabular         { font-variant-numeric: tabular-nums; }
::-webkit-scrollbar-thumb { background: var(--rule-2); }
```

Adapt `color-scheme` to the themes you actually ship.

## Keyboard

- Every pointer path has a keyboard path, including drag (add a single-pointer or button
  alternative).
- No positive `tabindex`; fix DOM order instead.
- Custom widgets (tabs, menus, comboboxes) implement the WAI-ARIA APG key map, or use the native
  element.
- Dialogs and drawers trap focus and restore it to the trigger on close.
- A skip link to `<main>`.
- `aria-hidden` never sits on an ancestor of a focusable control; use `inert`.

## Forms

- A visible label above every input, wired with `for`/`htmlFor`; placeholders show an example,
  never replace the label. Helper text below the label, error text below the input.
- Correct `type`, `inputmode`, `autocomplete` and a meaningful `name`, so mobile keyboards and
  autofill work. `spellcheck={false}` on emails, usernames and codes.
- Inputs at `16px` on mobile, or iOS zooms the page.
- Never block paste. Size inputs to their expected content.
- Checkbox and radio labels share one hit target with the control.
- Warn before navigating away from unsaved changes.
- Placeholder, helper, error text and focus rings all pass contrast against the section ground.

## Hit areas and targets

At least 24 by 24px (WCAG 2.2 AA), 44px for primary touch targets, with spacing between adjacent
targets. Enlarge the hit area with padding or a pseudo-element, not the visual.

## Motion and time

- Movement, scale, blur and parallax run only under `prefers-reduced-motion: no-preference`. Under
  `reduce`, replace them with short opacity cross-fades so the state change stays legible. A global
  kill switch that removes all feedback is itself a defect.
- Infinite loops, marquees and auto-advancing carousels pause on hover and focus and have a visible
  pause control when they run longer than five seconds.
- Nothing the user needs runs on a timer they cannot extend.
- Every animated state change leaves a static cue (color, icon or label) when the animation does
  not run.

## Announcements

Live regions exist before their content: render the empty `role="status"` region first, then
update its text. Success toasts use `role="status"`, not `aria-live="assertive"`.

## Images and media

`alt` by purpose: `alt=""` for decorative images, a functional label otherwise. The tell is not
missing alt but alt in the wrong register (a 15-word description on a decorative blob). Explicit
`width` and `height` on images so layout does not shift. Content images get a 1px inset outline in
pure black or white at 10% opacity (`oklch(0 0 0 / 0.1)` light, `oklch(1 0 0 / 0.1)` dark), never
a tinted color; skip transparent artwork.

## Structure

Heading levels never skip; landmarks (`<header>`, `<nav>`, `<main>`, `<footer>`); `lang` on
`<html>`; `dir` and `<bdi>` where direction changes. The current page is marked in navigation.
Every screen answers: where am I, where can I go, what is here, how do I get out.

## Zoom and resize

Nothing clips, overlaps or becomes unreachable at 320px width or 200% zoom. Never
`maximum-scale=1` or `user-scalable=no`. Sizes in `rem` so the reader's font size applies.

## URL state

Filters, tabs, pagination and expanded panels that someone might share or return to live in the
URL.

## Dates, numbers, text assembly

`Intl.DateTimeFormat` and `Intl.NumberFormat` with the user's locale; never a date built from
`getMonth()`. Build whole strings with ICU plural arguments, never `" + n + " item" + (n === 1 ? ""
: "s")`.

## Escalation triggers

In any review these are high severity on sight, never averaged down because the surface is minor:
an interactive control with no accessible name; a keyboard-reachable control with no visible focus;
a pointer-only path; motion ignoring reduced motion; content clipped at 320px or 200% zoom; a
failing contrast pair on text or controls; meaning by color alone; a destructive action with no
confirmation or undo; truncated content with no way back; content hidden past a scroll edge with no
cue; an error with no recovery; the danger hue on a non-destructive action; a state change carried
only by motion.
