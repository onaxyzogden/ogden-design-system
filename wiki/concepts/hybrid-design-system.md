---
title: "Hybrid Design System (House Methodology)"
type: concept
created: 2026-09-12
tags: [design-system, methodology, cross-project, olos, mios, house-style]
sources: 0
---

# Hybrid Design System — House Methodology

A shared methodology for designing and building web UI/UX across Ogden projects, synthesized from [[olos]] (OGDEN Atlas), [[milos]] (MIOS), and the principles/patterns cataloged at [DesignMotionHQ](https://designmotionhq.com).

**Core distinction this document holds onto: the *mechanism* is shared across every project; the *expression* is not.** OLOS's cool obsidian dashboard chrome and MIOS's soft-glass editorial warmth are not meant to converge into one palette — they're two skins over the same underlying methodology. A third project should start from the methodology below, then invent its own tokens, primitives, and motifs the way OLOS and MIOS each did.

---

## Layer 0 — Principles

Every project's own DESIGN.md should open with these, adapted from DesignMotionHQ's counter-thesis to schema-rendered AI UI:

1. **Intent-First Design** — before any pixel, name the actual users and their highest-stakes mistake. Don't default to generic CRUD assumptions.
2. **Hierarchy Over Defaults** — every screen gets a deliberate primary/secondary/tertiary ranking. Nothing is "equally weighted" by accident.
3. **System Consistency** — tokens live in one documented file. Off-system values are either promoted to intentional extensions or flagged as drift — never silently tolerated.
4. **State Completeness** — loading, empty, partial, error, success, and offline are designed upfront for every view that fetches or mutates data, not patched in later.

---

## Layer 1 — Tokens

**Rule:** semantic tokens over literals, always, with a documented resolution/fallback chain.

- Every color, spacing, radius, shadow, and z-index value is a named token, never a hard-coded literal in component code.
- Spacing uses a numeric base-unit scale (e.g. 4px grid: `space-1` = 4px, `space-2` = 8px …), not t-shirt sizes — numeric scales say exactly how far apart two tokens are; t-shirt sizes don't.
- Where a token needs to express different values in different scopes (a tint, an accent), define an explicit fallback chain and document it, e.g.:
  ```
  scope-local-token → component-scope-token → domain-scope-token → global-default
  ```
  (This is OLOS's OKLCH elevation ladder feeding semantic aliases, and MIOS's `--motif-tint → --level-color → --pillar-accent → --primary` chain — same mechanism, different names.)
- A perceptually-uniform color space (OKLCH or similar) is worth adopting once a project needs a real elevation ladder (3+ surface levels that must read as evenly-spaced); skip it for simpler projects rather than importing complexity that isn't earned yet.
- z-index gets its own small named scale (base/dropdown/sticky/overlay/modal/toast/tooltip/max), never raw integers in component code.

---

## Layer 2 — Motifs & Primitives

**Rule:** one canonical primitive per concern. When a second one appears, the old one becomes a deprecated forwarding wrapper — it is not deleted, and it is not left to drift independently.

- Each project names its own small vocabulary of reusable visual "moves" (3–6 motifs is plenty). OLOS's is a single surface primitive (`BentoBox`); MIOS's is five named effects (halo, ghost-text, soft-glass, shimmer-border, editorial serif). A new project should do the same exercise from scratch rather than importing either list.
- Every motif/primitive documents:
  - What problem it solves (what was being duplicated before it existed)
  - Its fallback/tint contract, if it takes a scoped color
  - When **not** to use it (one-off brand moments, throwaway prototypes, non-visual state signaling)
- Composition rules matter as much as the motif itself: don't stack two of the same animated effect on nested elements, gate every animation under `prefers-reduced-motion`, and make sure light/dark variants are both defined whenever a scope overrides a tint.

---

## Layer 2.5 — Pattern Reference

**Rule:** don't re-enumerate the tactical pattern library inside the house methodology — cite it, then document which patterns a project drew from.

[DesignMotionHQ's `/patterns` catalogue](https://designmotionhq.com/patterns) (80+ named patterns across Feedback, Forms, Interaction, Motion, Navigation, Visual, and Content) is the tactical menu that Layers 2 and 3 pull concrete choices from. This methodology is a meta-layer above that catalogue, not a competitor to it — it governs *how* a project picks and governs patterns, not *which* date-picker or modal-hierarchy to use.

- When a project needs a concrete pattern (a form field state, a data table, a command palette, an easing curve), the DesignMotionHQ catalogue is the first place to look before inventing one.
- Every pattern adopted from the catalogue gets recorded the same way a motif or primitive does (Layer 2): what it's used for, its token/tint contract if any, and when not to use it. A project's DESIGN.md should keep a short "patterns in use" list naming which catalogue entries it has adopted, so the choice is documented rather than ad hoc.
- Two catalogue categories map directly onto layers already defined here rather than needing their own list:
  - **Feedback patterns** (toast, skeleton loading, optimistic UI, undo UX, error states, Doherty threshold) *are* the frictionless-feedback half of Layer 3's ceremony/frictionless split.
  - **Visual patterns** (design tokens, shadow elevation, border radius, dark mode, depth layers) *are* Layer 1/2 mechanism, expressed as named patterns rather than raw tokens.
- Categories with no house-level equivalent yet (most of Forms, most of Interaction, Navigation specifics, Motion specifics beyond reduced-motion gating) are intentionally left to per-project judgment, sourced from the catalogue as needed — the house methodology doesn't take a position on, say, OTP input design or command-palette behavior.

---

## Layer 3 — Thresholds & Feedback

**Rule: ceremony is earned, not default.**

A boundary in the UI gets a deliberate ritual pause (a la MIOS's Ceremony Gate) only when at least one of these is true:
- The action is **irreversible** or high-stakes
- The boundary is **identity-bearing** — entering it is meant to change the user's mental state, not just their route (e.g., a covenant/intention moment), not a generic "next screen"
- The user is **returning after meaningful absence** and needs re-grounding, not just a reload

Everything else gets DesignMotionHQ-style frictionless feedback instead:
- Inline validation timed to avoid interrupting typing
- Toast notifications for non-blocking status
- Skeleton/loading states that communicate progress, not just delay
- Empty states that guide the next action, not just say "nothing here"

**Why the split matters:** ceremony that fires on every screen stops being ceremony — it becomes friction, which is precisely the "AI-generated UI wastes the user's time" failure DesignMotionHQ is naming. Scarcity is what makes a ritual moment register (the same mechanism as the Von Restorff effect: isolated things get noticed; ubiquitous things don't).

---

## Layer 4 — Governance

- **ADR trail.** Every token-level or primitive-level decision gets a dated architectural decision record — not just a comment in code. Future sessions (human or agent) should be able to answer "why is it this way" without archaeology.
- **Anti-pattern list.** Maintain an explicit "do NOT use" list alongside the positive guidance — generic/undifferentiated design, AI purple/pink gradients, emojis as icons, missing `cursor: pointer`, invisible focus states, instant (non-transitioned) state changes.
- **Pre-delivery checklist.** Before shipping any UI work, verify contrast ratios, focus visibility, reduced-motion handling, responsive breakpoints, and that new surfaces compose the canonical primitive rather than rolling a new one.
- **Drift gets flagged, not tolerated.** An off-system value is either promoted to a documented, intentional extension of the token set, or corrected — it never just sits there unaddressed.

---

## What Stays Project-Local (not house style)

Concrete example from the two source projects, to make the mechanism/expression distinction unambiguous:

**OLOS-specific (do not inherit as-is):** no blue as primary action color; no border-radius greater than 6px; the two-gold brand/active split; the "High-Tech Earth" cool-obsidian chrome palette; Fira Code + Fira Sans as the specific typefaces.

**MIOS-specific (do not inherit as-is):** the five specific motifs (halo, ghost-text, soft-glass, shimmer-border, editorial serif); ceremony gate copy and ayat content; the editorial-serif treatment itself.

A new project inherits the *practice* — pick your own constraints, name your own motifs, choose your own type pair, document all of it — not the specific values above.

---

## Provenance

- [[olos]] — `design-system/ogden-atlas/MASTER.md`, `wiki/concepts/design-system.md` (`onaxyzogden/atlas`)
- [[milos]] — `wiki/concepts/motif-tokens.md`, `wiki/concepts/ceremony-gate-pattern.md` (`onaxyzogden/Maqasid`)
- [DesignMotionHQ](https://designmotionhq.com) — home page thesis + `/patterns` catalog (80+ patterns, 10 categories)
- Synthesized in conversation, 2026-09-12.
- Compared layer-by-layer against the full `/patterns` enumeration on 2026-09-12; gap analysis led to Layer 2.5.
