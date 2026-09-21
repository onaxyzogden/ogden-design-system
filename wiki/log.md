# Log

## 2026-09-21 — Fieldwork redesign round; three lessons folded back
- Implemented a design-canvas redesign handoff into `onaxyzogden/fieldwork-demo`, working against this methodology rather than the prototype source (the `.dc.html` format is not portable code).
- The handoff's prototype was deliberately thinner than the shipped app — five issue categories against the repo's 81, a stub slot generator against a real scheduler, no payments. Adopted its *expression and interaction patterns* in full; declined its *reductions in data depth*, which would have been a regression. Recorded as ADRs 006-009 in the project's own `docs/design-decisions.md`, not here.
- Confirmed the mechanism/expression split this document opens with: the project took a refined amber brand of its own while inheriting Layers 1-4 unchanged.
- Three lessons fed back into `hybrid-design-system.md`:
  - **Layer 3 + Layer 4** — the no-disabled-submit-control rule was already present as half a sentence ("prefer keeping submit controls enabled"). Promoted to a full pattern: the three distinct failures (tab order, screen-reader silence, no pointer events so the explanatory tooltip never opens), the per-field replacement, and the two caveats worth knowing (focus only lands on fields rendered before the click; read-only-because-someone-else's is not a blocked action). Added to the anti-pattern list.
  - **Layer 4** — "test harness and legitimately useful chrome are not reliably distinguishable up front." Identity switchers were dropped from the redesign as scaffolding, then restored once it turned out the prototype could not be evaluated without them.
  - **Layer 0** — model identity as a real reference from the first schema, never a viewer-relative boolean. A boolean answers "is this mine?" but loses "whose is it?", leaving records that exist but cannot be reached from the side that owns them.

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
