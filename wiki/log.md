# Log

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
