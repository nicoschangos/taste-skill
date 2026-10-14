# Motion

## Settled rules (every source agrees)

1. Every animation names its purpose: feedback, spatial continuity, state change or directing
   attention. "It looked cool" is not a purpose; the fix is deletion.
2. Never `ease-in` on UI; start fast and settle.
3. Never animate layout properties (`width`, `height`, `top`, `left`, `margin`, `padding`). Animate
   `transform`, `opacity`, `filter`, `clip-path`, `mask`; for height use `grid-template-rows`.
4. `prefers-reduced-motion` is mandatory, and the reduced version is a gentle cross-fade, not the
   absence of feedback.
5. Never `transition: all`. Name the properties.

## Volume is a budget, set by mode

The sources disagree sharply here (one wants motion on every block, one wants one orchestrated
moment, one wants often zero). The disagreement is resolved by the surface:

| Mode | Budget |
|---|---|
| Persuade | One signature moment (a sequenced hero, one scroll-told beat where order carries the argument) plus interaction feedback. Scroll reveals only where sequence means something; never the same fade-up on every section. |
| Experience | May be cinematic and scroll-choreographed, still with a stated purpose per sequence and a reduced-motion path. |
| Operate | Feedback, panel and tab transitions, list insertion, skeleton-to-content. Frequent actions get none, or 150ms or less on color and opacity. |
| Read | Near zero beyond feedback. |

Write the count in the sheet. `none` is legitimate. Feedback (press, focus, hover color) is part of
the floor and never counts against the budget, so no page ships inert.

**Motion claimed is motion shown.** If the sheet promises a choreographed hero, ship it working.
If you cannot ship working motion in scope, lower the budget and ship a clean static page. Never
half-built motion (cut-off triggers, jumpy entrances, missing cleanups).

## Curves and durations

Three "canonical" ease-outs circulate (`cubic-bezier(0.23, 1, 0.32, 1)`,
`cubic-bezier(0.16, 1, 0.3, 1)`, `cubic-bezier(0.32, 0.72, 0, 1)`) and a 2.3x spread in default
durations. They are conventions, not physics: pick one house curve, write it in the sheet and use it
everywhere. If nothing is chosen, use `cubic-bezier(0.2, 0, 0, 1)`. Do not emit Material's
`cubic-bezier(0.4, 0, 0.2, 1)` by reflex.

| Interaction | Duration |
|---|---|
| Press, hover | 100-150ms |
| Tooltip, small popover | 125-200ms |
| Dropdown, menu | 150-250ms |
| Modal, drawer, sheet | 200-400ms |
| View or page transition | 300-500ms |
| One focal storytelling moment | up to 500-800ms, with a reason |

UI motion over 300ms needs a stated reason. Smaller distances take shorter durations.

## Exact recipes

- **Press**: scale `0.96` on buttons, `0.98` on large surfaces, ease-out, `100`-`150ms`, excluded
  on `:disabled`, with an opt-out variant where it would distract.
- **Staged entrance** (infrequent, where order shows hierarchy): split into semantic chunks (title,
  description, actions), stagger `100ms`, each `300ms` ease-out from `opacity: 0`,
  `translateY(12px)`, `filter: blur(4px)`. Never stagger routine interactions.
- **Exit**: shorter and smaller than the entrance: `150ms`, opacity, `-12px` translate, `4px` blur.
  Slide fully out only when the destination carries meaning (a drawer closing to its edge).
- **Icon swap** (copy to copied, play to pause): cross-fade scale `0.25` to `1`, opacity `0` to `1`,
  blur `4px` to `0`; spring `{ duration: 0.3, bounce: 0 }`, or `300ms` with the house curve.
- **Skip state animations on first render**: `initial={false}` on an `AnimatePresence` wrapping a
  state swap, never around an intentional entrance.
- **Theme switch**: suppress all transitions during the swap.
- **Interactive state uses transitions or springs**, which retarget when reversed mid-flight;
  keyframes are for sequences that run once.

## Springs and gestures

For anything the user drags, flicks or throws, springs beat fixed curves because they are
interruptible and velocity-aware. Think in damping ratio and response:

| Interaction | Damping | Response |
|---|---|---|
| Move or reposition | 1.0 | 0.4s |
| Rotation | 0.8 | 0.4s |
| Drawer or sheet | 0.8 | 0.3s |

Default damping `1.0` (`bounce: 0`). Overshoot only when the gesture carried momentum. Project the
release with exponential decay and hand the release velocity to the spring so dragging and
animating have no seam. Never lock input during a transition; always animate from the on-screen
value; enter and exit along the same path; set `transform-origin` to the trigger so a popover grows
from its button.

## Visible by default

Scroll reveals built as `opacity: 0` plus a script toggle hide content forever when the script
fails, a bot reads the page or the browser restores scroll past the trigger. Content is visible in
the base styles; the animation's `from` keyframe (with `animation-fill-mode: both`) or the script
enhances the entrance.

## Choosing the tool

Pick the lightest tool that does the job, and use the one the project already depends on:

1. CSS transitions for state changes; CSS `@keyframes` for one-shot sequences; CSS scroll-driven
   animations (`animation-timeline: view()`) for simple scroll-linked effects.
2. Motion (`import { motion } from "motion/react"`) in React for presence, layout (`layout`,
   `layoutId`) and gesture work. Continuous values (pointer position, scroll progress, magnetic
   effects) go through `useMotionValue`, `useTransform` and `useScroll`, never `useState`, which
   re-renders every frame. Animated components are isolated client leaves (`"use client"`).
3. GSAP with ScrollTrigger only for pinned, scrubbed or multi-step timelines. Pin at
   `start: "top top"`; a scroll length equal to the travel; clean up with `gsap.context().revert()`
   in the effect's cleanup.

Never `window.addEventListener("scroll", ...)` or `requestAnimationFrame` loops that write React
state. Use IntersectionObserver, `useScroll`, ScrollTrigger or scroll-driven CSS.

## Performance

`will-change` only after seeing first-frame stutter, naming the property (`transform`, `opacity`,
`filter`), never `all`. Lazy-load heavy libraries (Three.js, large animation runtimes) below the
fold. Watch for continuous repaints: grain or blur on scrolling containers destroys mobile frame
rates.

## Decorative motion to skip

Each of these is motion added so the page feels alive rather than because something changed:
`hover:scale-105` on cards and buttons; image scale or rotate on hover; more than one marquee per
page; pulsing dots without live data; blinking fake cursors; the same fade-up on every section;
bounce and elastic easing on non-gesture UI; custom mouse cursors; infinite loops on informational
content.
