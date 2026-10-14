# Reviewing an interface

A review is read-only unless the user also asks for the fixes. When they do, the report becomes the
change scope, and verification runs again afterwards.

## Evidence, not taste

Press hard on the floor and the escalation triggers; leave deliberate project choices alone. A
density, radius or voice you merely disagree with is not a finding. A documented project convention
settles taste but never excuses a floor violation; when a shared token or guideline causes a
problem, report it once against that source.

Calibrate before flagging. When 326 candidate tells were rated by three independent judges, fewer
than 10% were unanimously high-signal; most individual properties do not convict on their own.
**Report co-occurrence, not items**: "fourteen properties on this page are framework defaults" is a
finding, "this uses Inter" is not. Say a value reads as **inherited**, never that the page "is AI".
Off-scale magic numbers, a double space, sub-pixel misalignment, a novelty display face or an
inconsistent margin someone lived with are evidence of a human, not a machine.

## Procedure

1. **Resolve the scope** (screen, flow, feature, branch or diff) and state it. Cover empty,
   loading, error and narrow-width states where they exist. If the scope is too large to inspect
   credibly, narrow to one complete flow and say what was excluded.
2. **Recon**: stack, styling system, component library, tokens, viewports, and the project's own
   interface documents. Write every fix in the project's idiom.
3. **Interact with it** before reading it: tab through, press and hold, submit an empty form, load
   on a slow connection, resize to 320px, zoom to 200%. Most findings live here.
4. **Check the free axes**: palette, type pairing, radius, elevation, motion budget. Decided or
   defaulted? Run `node scripts/check.mjs <paths>`.
5. **Check spacing registers, states and assets.**
6. **Composition last** (hero, grid, icons). It has the lowest survival rate under audit; hold those
   findings loosely.

## Countable assertions

Turn adjectives into counts: distinct gap values and how many are section-level; distinct font
sizes and the largest-to-smallest ratio (under 2 is flat); elements with a border plus a wide
shadow; color literals not traceable to a token; interactive elements lacking `:active` or
`:focus-visible`; distinct rendered icon stroke widths; uppercase micro-labels directly above
headings; images on placeholder hosts; invented company names.

## Severity

- **HIGH**: blocks a task, misleads, hides content or controls, risks data loss, or is a repeated
  systemic failure. Every escalation trigger in `05-states-a11y.md` is HIGH on sight, regardless of
  how minor the surface is.
- **MEDIUM**: meaningfully harms comprehension, efficiency, adaptability or consistency, including
  a cluster of inherited defaults that makes the product read as templated.
- **LOW**: isolated polish with limited task impact.

Within a severity, rank by reach: a token or shared-component fix outranks the same symptom in one
leaf. One root cause is one finding, with every location in the same row.

## The cheaper fix

Propose the earliest fix that works:

1. **Delete** (a separator space could carry, animation on a frequent interaction, redundant ARIA,
   an unused ramp).
2. **Use the platform** (the native element, control or focus ring).
3. **Reuse the project** (an existing token, spacing step or curve).
4. **Correct the value** (the exact value this skill gives).
5. **Add** (a new token, wrapper, media query or ARIA attribute).

When the code under review adds what a deletion would fix, that is itself a finding.

## Output

**Scope and coverage**: the scope, stack, convention documents found, and a coverage table.

| Area | Evidence inspected | Result |
|---|---|---|
| Accessibility and states | files, components, interactions | findings count, `Clear`, or `Not reviewed` with the reason |
| Layout and space | | |
| Type | | |
| Color | | |
| Motion | | |
| Assets and copy | | |
| Inherited defaults (checker and co-occurrence) | | |

**Findings**, one table ordered by severity then reach, at most 15 rows (triggers first; if the cap
cut any, say how many). A short review, or none, is a valid result.

| Severity | Area | Location | Before | After | Why |
|---|---|---|---|---|---|

Location is `path/to/file:line` (or the exact screen and component). Before and After show real
code. Why names the violated rule and the user impact. A finding without a concrete replacement is a
complaint; cut it. Flag your own uncertainty where good human work would plausibly do the same.

**Verification**: each check or interaction, how it was run and what happened. A check you could
not run is **Not verified**, never a finding and never a pass.

**Verdict**: `Block` while any HIGH finding remains; otherwise `Approve`, with MEDIUM and LOW left
as work. Name every `Not reviewed` area in the verdict.

## Scores, only when asked

If the user asks for a score ("rate this", "how good is it"), add 0-10 per dimension after the
findings: direction (does every detail trace to one intent), hierarchy (squint test), craft
(alignment, spacing system, color and type count), function (does each element earn its place) and
originality (any unexpected but right decision). Scores never replace the findings table.

## Change-scoped reviews

For a branch, pull request or uncommitted diff, scope the review to what changed and what it
affects, and mark each finding `Introduced`, `Regression` or `Pre-existing`. The verdict and the cap
cover `Introduced` and `Regression` only; pre-existing issues go in a separate section.
