# Log

## 2026-10-16 — The register applied to the Fieldwork operator Walkthroughs and decision queue; two more lessons
- The eighth application of the register: the operator's Walkthroughs and decision queue in `onaxyzogden/fieldwork-demo` (PR #71, recorded as ADR 093 there). The remit was "the operator sees whose move each walkthrough waits on, and makes each decision in one press or skips it". The audit found 12 issues; all 12 are fixed, with the empty state from "Also found".
- Two lessons extended the register bullet in Layer 1:
  - **An end screen says what is still waiting.** The all-clear shows only when nothing is left.
  - **Breaking what someone else holds asks first.** Even a replacement, when it cannot be undone; one step when nothing would break.
- The page name, one state with three names, the red count, accent on every chip and the lost focus were already covered and needed no change.

## 2026-10-16 — The register applied to the Fieldwork operator Home and Today; four more lessons
- The seventh application of the register: the operator's Home and Today in `onaxyzogden/fieldwork-demo` (PR #70, recorded as ADR 092 there). The remit was "the operator sees what today holds and what needs them first, and gets to it in one step". The audit found 12 issues, and all 12 are fixed, with the eight further findings in scope.
- Four lessons extended the register bullet in Layer 1:
  - **A greeting is a slogan.** Home names itself too.
  - **A heading names the scope it shows.** "Today" only on today; otherwise the date.
  - **Totals count the same set the list shows.**
  - **An illustration says only what it knows.** One mark per real item, and no route it cannot know.
- The red count, the four controls to one page and the lost focus were already covered by the register bullet and needed no change.

## 2026-10-16 — The register applied to the Fieldwork operator request detail; four more lessons
- The sixth application of the register: the operator's request detail, its tabs and the fulfilment screen in `onaxyzogden/fieldwork-demo` (PR #69, recorded as ADR 091 there). The remit was "the operator sees what this request needs, decides in one step, and books it". The audit found 12 issues, and all 12 are fixed, with five of seven further findings.
- Four lessons extended the register bullet in Layer 1:
  - **A fact is not a state.** Facts sit on neutral surfaces in plain text.
  - **A status chip keeps one rule on every screen it appears.** The detail colours it as the list does.
  - **A fact every item shares is said once, above them.**
  - **Where the toast has no undo, a recoverable removal asks first,** as a fallback to Layer 3's undo window, not a replacement for it.
- The inline-error finding was already covered by Layer 3 and needed no change.

## 2026-10-16 — The register applied to the Fieldwork operator request list; four more lessons
- The fifth application of the register: the operator's Requests page in `onaxyzogden/fieldwork-demo` (PR #68, recorded as ADR 090 there). The remit was "the operator sees what is theirs to act on, finds any request in one step, and opens it". The audit found 10 issues, and all 10 are fixed.
- Four lessons extended the register bullet in Layer 1:
  - **In a list, status colour says whose move it is.** Accent for the rows that wait on the person, a neutral chip for the rest, red only for errors.
  - **One move, one control.** A duplicate route back is a second thing to keep in step.
  - **A filtered list that matches nothing says so and offers the way back,** and focus lands somewhere when that control goes.
  - **A label is for the person; its value is the system's.**

## 2026-10-16 — The register applied to the Fieldwork contractor workspace; five more lessons
- The fourth application of the register, and the first on the contractor: the contractor workspace in `onaxyzogden/fieldwork-demo` (PR #67, recorded as ADR 089 there). The remit was "the contractor sees the next job and what it pays, and answers each offer in one step". The audit found 11 issues, and all 11 are fixed.
- Five lessons extended the register bullet in Layer 1:
  - **One action, one colour, everywhere it appears.** The colour belongs to the action's role, not the screen.
  - **One primary per screen.** A shortcut to the item already open steps aside, and each list item's own button is secondary.
  - **Headings inside a page sit below its h1.**
  - **Say the title once.** Hide a disclosure with nothing in it.
  - **An empty state says what is true.** "You're done" needs something that was done.

## 2026-10-16 — The register applied to the Fieldwork customer home; four more lessons
- The third application of the register: the customer workspace home in `onaxyzogden/fieldwork-demo` (PR #66, recorded as ADR 088 there). The remit was "the customer sees what needs them, what's coming, and how each request stands". The audit found 9 issues, and all 9 are fixed.
- Four lessons extended the register bullet in Layer 1:
  - **A workspace lists the person's items in the order they act on them**, not creation order.
  - **One state, one word**, across the badge, the tracker and the notifications.
  - **Danger colour is for errors.** A count that names something to do opens it.
  - **Accent repeated on every item is decoration.** Routine content sits on a neutral surface. Labels are sentence case, not tracked capitals.

## 2026-10-16 — The register applied to the Fieldwork customer intake; three more lessons
- The second application of the register, and the first on a customer surface: the intake in `onaxyzogden/fieldwork-demo` (PR #65, recorded as ADR 087 there). The remit was "the customer says where, what and when, and leaves knowing what happens next". The audit found 11 issues, and all 11 are fixed.
- Three lessons extended the register bullet in Layer 1:
  - **Warm is not persuasive.** A customer flow may speak warmly but does not sell, and it never shows the operator's working state (review, booking mode, scores).
  - **Order is part of a comparison.** The best pick may lead, marked once. The rest follow an order the person can read, such as time, never an internal score.
  - **What the person can act on comes first.** On a phone, real options sit above the preferences that qualify them.

## 2026-10-16 — The register applied to a Fieldwork screen; three lessons folded back
- The first application of the persuasive/operational **register**, on the operator's Contractors page in `onaxyzogden/fieldwork-demo` (PR #62, recorded as ADR 085 in that project's own `docs/design-decisions.md`, not here).
- Audited dial by dial against a written remit: "compare the people you can send". Copy voice, type scale, density/grid and accent were all persuasive. The page had no motion. It is now an h1, one factual line and one roster table, which stacks into labelled lines when the container is narrow.
- Three lessons extended the register bullet in Layer 1:
  - **Copy voice is a dial.** An eyebrow, a slogan for a heading, or a badge on every item leaks the persuasive register even when type and spacing are compact.
  - **Comparison needs aligned rows.** Cards make the eye read each one in turn. A caveat that applies to every row is said once.
  - **Density is held by width-aware tiers.** One line per value, then wrapped at word boundaries, then stacked. The tiers are measured against the container, not the window. A single breakpoint either overflows or gives up density too early.

## 2026-10-16 — "Modern UI/UX Design Scholar" NotebookLM review
- Queried the NotebookLM notebook (25 practitioner YouTube sources) across 8 themes — color, typography, layout, motion, components/platforms, gestures/gamification, mistakes, process — with source citations required; raw answers kept in the session scratchpad, every adopted principle restated in original wording.
- Folded ~30 gaps into `hybrid-design-system.md`: role-based color and the persuasive/operational **register** concept (Layer 1); progressive disclosure, behavioral consistency, motion purpose test, continuous-motion pause control and related primitives (Layer 2); async press acknowledgement, next-step chaining, gesture-form ceremony, generative-output obligations (Layer 3); new anti-patterns plus flows-before-fidelity, repair order, and prototype-based review (Layer 4); an explicit list of taste calls left project-local.
- Rejected: gamification currencies/streaks/leaderboards (Zeigarnik caveat), arrow removal on swipe lists (gesture parity), single-typeface mandate (conflicts with MIOS editorial serif), implementation constants, personal craft advice.
- Frontmatter `sources` corrected from 0 to 5 (OLOS, MIOS, DesignMotionHQ, Blueprint PDF, this notebook).

## 2026-09-21 — Fieldwork operator audit round; two lessons folded back
- Audited the operator's request-detail screen in `onaxyzogden/fieldwork-demo` after the redesign round below: functionally richer than the design reference, but denser without the density buying anything — a declined job offered the same "who does this job now?" decision through five separate control clusters, announced by six different badges, all funnelling into one modal that asked it a sixth time.
- Wrote the operator's remit first, before touching any control: triage (is the scope clear enough to act on?), scope authoring (correct classification/duration/split-merge), decide who (a contractor, or self), decide the price (send a quote), unblock (handle declines/expiries, ask the customer when ambiguous). Every control on the screen was then mapped against that list with an explicit verdict — keep, fix, merge, defer behind a disclosure, or cut — rather than judged on sight.
- Result: the request detail now renders exactly one dispatch-decision card, derived from state, in place of the five duplicate clusters; two real behavior bugs (divergent guards giving different refusal messages for the same block; dispatch buttons silently branching on invisible checkbox state) were fixed as a consequence of collapsing to one path rather than patched independently. Scope-authoring controls stayed reachable but moved behind disclosures so they stop competing with the triage decision. Implemented and merged as `onaxyzogden/fieldwork-demo` PR #3; recorded as ADR 010–011 in the project's own `docs/design-decisions.md`, not here.
- Two lessons fed back into `hybrid-design-system.md`:
  - **Layer 0** — new principle 5, "Audit Against a Written Remit, Not Vibes": write the role's responsibilities down before auditing an existing screen, then map every control against them with an explicit verdict. Without that discipline, decluttering degenerates into taste.
  - **Layer 4** — new governance bullet, "A derived value must have a writer": a routing/bucketing function (here, `bucket()` routing `"Information requested"` to Waiting) must be checked against the write side, not just its own branches — a branch nothing ever writes reads as coverage while hiding that the write side was never built.

## 2026-09-21 — Fieldwork redesign round; three lessons folded back
- Implemented a design-canvas redesign handoff into `onaxyzogden/fieldwork-demo`, working against this methodology rather than the prototype source (the `.dc.html` format is not portable code).
- The handoff's prototype was deliberately thinner than the shipped app — five issue categories against the repo's 81, a stub slot generator against a real scheduler, no payments. Adopted its *expression and interaction patterns* in full; declined its *reductions in data depth*, which would have been a regression. Recorded as ADRs 006-009 in the project's own `docs/design-decisions.md`, not here.
- Confirmed the mechanism/expression split this document opens with: the project took a refined amber brand of its own while inheriting Layers 1-4 unchanged.
- Three lessons fed back into `hybrid-design-system.md`:
  - **Layer 3 + Layer 4** — the no-disabled-submit-control rule was already present as half a sentence ("prefer keeping submit controls enabled"). Promoted to a full pattern: the three distinct failures (tab order, screen-reader silence, no pointer events so the explanatory tooltip never opens), the per-field replacement, and the two caveats worth knowing (focus only lands on fields rendered before the click; read-only-because-someone-else's is not a blocked action). Added to the anti-pattern list.
  - **Layer 4** — "test harness and legitimately useful chrome are not reliably distinguishable up front." Identity switchers were dropped from the redesign as scaffolding, then restored once it turned out the prototype could not be evaluated without them.
  - **Layer 0** — model identity as a real reference from the first schema, never a viewer-relative boolean. A boolean answers "is this mine?" but loses "whose is it?", leaving records that exist but cannot be reached from the side that owns them.

## 2026-09-13 — Undo UX + Golden Ratio follow-up
- Folded in the two patterns reconsidered from the "not folded in" set: undo-window-over-confirmation (Layer 3) and golden ratio as a valid type-scale ratio (Layer 1). Commit: `d27c4f3`.

## 2026-09-13 — Full DesignMotionHQ pattern catalogue review
- Reviewed all 76 individual pattern detail pages in DesignMotionHQ's `/patterns` catalogue (dispatched as 7 parallel background research passes, ~11 pages each), each principle restated in original wording and checked against `hybrid-design-system.md` for genuine gaps vs. existing coverage.
- Folded ~28 genuine gaps into the document across Layer 1 (grid discipline, Gestalt grouping, gradient/border-radius token rules, dark-mode-is-not-inversion), Layer 2 (overlay viewport-awareness, hover/gesture parity, layout-footprint preservation, tooltip content ceiling, preview-vs-committed state, responsive pattern substitution), Layer 3 (validation-without-disabling, optimistic-UI risk tiering, autosave visibility, severity-scaled feedback surfaces, flow psychology (peak-end/serial-position/Zeigarnik), microcopy as feedback, persisted navigable state), and Layer 4 (two new anti-patterns: color-alone signaling, chart-axis distortion).
- Corrected a standing data error: the catalogue has 76 patterns (not 75) across 7 categories (not the site's claimed "10"), and the Visual category has 20 items (not 19) — both now reflected in the Layer 2.5 intro, Appendix header, and Provenance section.
- ~46 patterns were judged already covered by existing layers, deferred to per-project judgment (per Layer 2.5's existing stance), or too implementation-specific for a house methodology (e.g. CSS `:has()` specifics, input-masking chunking, range-slider/color-picker widget details).
- Commit: `d0b6f74`.

## 2026-09-12/13 — Repo scaffold + Blueprint PDF review
- Created public repo `onaxyzogden/ogden-design-system` holding the house methodology synthesized from OLOS, MIOS/MILOS, and DesignMotionHQ (`6bbe515`).
- Added the DesignMotionHQ pattern-name index (Layer 2.5 appendix) with an initial (later corrected) count of 75 patterns / 7 categories (`dbd59ae`).
- Reviewed DesignMotionHQ's "Design System Blueprint" PDF (their gated free lead-magnet) and folded in 3 additions (`4f63b93`).
