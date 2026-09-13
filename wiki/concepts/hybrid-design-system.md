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
- z-index gets its own small named scale (base/dropdown/sticky/overlay/modal/toast/tooltip/max), never raw integers in component code — and z-index only ranks siblings within the same stacking context, so isolate nested contexts deliberately rather than escalating numbers to compete across one.
- Type sizes come from a modular scale (a fixed ratio between steps), not arbitrary pixel values picked per-screen — the failure mode is a heading and a body size landing a few px apart and reading as a mistake rather than a choice.
- Layout rests on a disciplined column grid; departures from it are reserved for deliberate emphasis, not habit.
- Visual grouping comes from a shared property — proximity via deliberately uneven whitespace, or shared alignment/color/enclosure — never from borders/dividers or uniform spacing everywhere.
- Gradient tokens keep hue rotation narrow (roughly within 60° of the wheel) and hold lightness direction consistent end-to-end; wide hue jumps or reversed lightness read as low-quality regardless of color space.
- Border-radius values form one proportional scale; a nested element's inner radius is derived from the outer radius minus the gap between them, never picked independently.
- A dark theme is not an inverted light theme: build it from a near-black (never pure-black) base with desaturated hues and an opacity-stepped text hierarchy, not remapped light-mode values.

---

## Layer 2 — Motifs & Primitives

**Rule:** one canonical primitive per concern. When a second one appears, the old one becomes a deprecated forwarding wrapper — it is not deleted, and it is not left to drift independently.

- Each project names its own small vocabulary of reusable visual "moves" (3–6 motifs is plenty). OLOS's is a single surface primitive (`BentoBox`); MIOS's is five named effects (halo, ghost-text, soft-glass, shimmer-border, editorial serif). A new project should do the same exercise from scratch rather than importing either list.
- Every motif/primitive documents:
  - What problem it solves (what was being duplicated before it existed)
  - Its fallback/tint contract, if it takes a scoped color
  - When **not** to use it (one-off brand moments, throwaway prototypes, non-visual state signaling)
- Composition rules matter as much as the motif itself: don't stack two of the same animated effect on nested elements, gate every animation under `prefers-reduced-motion`, and make sure light/dark variants are both defined whenever a scope overrides a tint.
- Icons are a primitive too: pick one icon set and one sizing scale (e.g. 16/20/24/32/48px for inline/default/nav/feature/hero contexts) and stop there — mixed icon styles or ad hoc sizes read the same way mismatched primitives do. Regardless of the icon's visual size, its tappable/clickable area should never drop below ~44×44px. Icons in the set additionally share stroke weight and one fill-or-outline choice, with rounded glyphs given slight optical upsizing to read as the same size as square ones.
- Motion timing is part of the primitive's contract, not an afterthought: pair easing to direction (ease-out entering, ease-in leaving, ease-in-out for moves/resizes) and scale duration to the weight of what's moving (roughly 100-200ms for hover/toggle-scale feedback up to 400-500ms for page-level transitions) — document both alongside the motif the same way its tint/fallback chain is documented. When two signals represent one state change (an icon rotation and a panel expansion), they run on the identical timing curve — desync between them reads as broken, not as two effects.
- Overlays (menus, dropdowns, popovers, tooltips) detect available viewport space and reposition or flip themselves so they never render clipped off-screen.
- No interaction that matters may depend on hover or gesture alone: every hover-revealed action and every swipe/drag gesture needs a discoverable, tap/keyboard-reachable equivalent, detected via capability query rather than inferred from device type.
- Interactive-state cues (an inline-edit affordance, a hover effect) reveal themselves through tint, icon, or shadow — never by resizing or shifting the element's layout footprint, which would displace neighboring content.
- A pattern is substituted for a different one when the breakpoint changes the interaction model (e.g. tabs → bottom sheet on mobile), not just visually shrunk.
- A tooltip holds one short phrase; once an explanation needs more than that, it's replaced by a popover or inline-help pattern instead.
- An interactive preview state (hover, drag-to-rate) renders visibly distinct from the committed state and reverts cleanly if the interaction is abandoned before commit.

---

## Layer 2.5 — Pattern Reference

**Rule:** don't re-enumerate the tactical pattern library inside the house methodology — cite it, then document which patterns a project drew from.

[DesignMotionHQ's `/patterns` catalogue](https://designmotionhq.com/patterns) (76 named patterns across Content, Feedback, Forms, Interaction, Motion, Navigation, and Visual — see the index below) is the tactical menu that Layers 2 and 3 pull concrete choices from. This methodology is a meta-layer above that catalogue, not a competitor to it — it governs *how* a project picks and governs patterns, not *which* date-picker or modal-hierarchy to use.

- When a project needs a concrete pattern (a form field state, a data table, a command palette, an easing curve), the DesignMotionHQ catalogue is the first place to look before inventing one.
- Every pattern adopted from the catalogue gets recorded the same way a motif or primitive does (Layer 2): what it's used for, its token/tint contract if any, and when not to use it. A project's DESIGN.md should keep a short "patterns in use" list naming which catalogue entries it has adopted, so the choice is documented rather than ad hoc.
- Two catalogue categories map directly onto layers already defined here rather than needing their own list:
  - **Feedback patterns** (toast, skeleton loading, optimistic UI, undo UX, error states, Doherty threshold) *are* the frictionless-feedback half of Layer 3's ceremony/frictionless split.
  - **Visual patterns** (design tokens, shadow elevation, border radius, dark mode, depth layers) *are* Layer 1/2 mechanism, expressed as named patterns rather than raw tokens.
- Categories with no house-level equivalent yet (most of Forms, most of Interaction, Navigation specifics, Motion specifics beyond reduced-motion gating) are intentionally left to per-project judgment, sourced from the catalogue as needed — the house methodology doesn't take a position on, say, OTP input design or command-palette behavior.

### Appendix — Pattern Index (names only, verified 2026-09-13)

76 patterns across 7 categories, per the live `/patterns` page's own link enumeration (their site copy claims both "10 categories" and a "75 patterns" summary stat — neither matches the actual filter tabs or the full href list; treat 7 categories / 76 patterns as ground truth). Names and categories only, for lookup — descriptions live at the source, not reproduced here.

- **Content (4):** Empty States, Serial Position, Microcopy, Landing Page Skeleton
- **Feedback (9):** Doherty Threshold, Error States, Loading States System, Notification System, Toast Notifications, Zeigarnik Effect, Undo UX, Optimistic UI, Skeleton Loading
- **Forms (12):** Settings System, Autosave, Date Pickers, Form Field States, Input Masking, Range Sliders, Stepper Wizard, Toggle Anatomy, File Upload UX, Password Field UX, OTP Input, Form Validation Timing
- **Interaction (23):** CSS Has Selector, Bulk Actions, Disabled Buttons, Hover Trap, Behind the Button, Inline Editing, Live Cursors, Destructive Actions, Context Menu, Drag and Drop, Dropdown Design, Peak-End Rule, Search Experience System, Star Rating, Tooltip Design, Swipe Actions, Bottom Sheets, Color Picker UX, Command Palette, Filter Chips, Accordion Disclosure, Data Table, Modal Hierarchy
- **Motion (4):** Animation Timing, Easing Curves, Card Hover Anatomy, Scroll-Driven Animations
- **Navigation (4):** Navigation Patterns, Tabs System, Focus States, Pagination
- **Visual (20):** De-AI Landing Hero, Reverse-Engineered Linear, Charts That Lie, Design System Kit, Golden Ratio, Grid System, Proximity Rule, Shadow Elevation, Visual Hierarchy, Z-Index Mastery, Gradient Design, Design Tokens, Color Accessibility, Gestalt Laws, Border Radius, Dark Mode, Von Restorff Effect, Perfect Card, Depth Layers, Icon Design Rules

---

## Layer 3 — Thresholds & Feedback

**Rule: ceremony is earned, not default.**

A boundary in the UI gets a deliberate ritual pause (a la MIOS's Ceremony Gate) only when at least one of these is true:
- The action is **irreversible** or high-stakes
- The boundary is **identity-bearing** — entering it is meant to change the user's mental state, not just their route (e.g., a covenant/intention moment), not a generic "next screen"
- The user is **returning after meaningful absence** and needs re-grounding, not just a reload

Everything else gets DesignMotionHQ-style frictionless feedback instead:
- Inline validation timed to avoid interrupting typing — prefer keeping submit controls enabled and validating on interaction, highlighting the blocking field and moving focus there, over disabling a control outright; disabling silently breaks keyboard, screen-reader, and tooltip access.
- Toast notifications for non-blocking status
- Skeleton/loading states that communicate progress, not just delay
- Empty states that guide the next action, not just say "nothing here"
- Optimistic UI is reserved for low-stakes, reversible actions; irreversible or financial actions always wait for authoritative server confirmation before declaring success, regardless of client-side pre-validation.
- Autosave commits on a debounce tied to natural pauses in input, never on every keystroke, and the interface always makes visible whether current content is local-only, pending, or confirmed-saved.
- Feedback surface and prominence scale with severity and how much progress it blocks: badges or inline text for passive information, toasts for non-blocking status, banners for warnings, and modals reserved for responses that are genuinely required. The same discipline picks a loading indicator — skeleton when the layout is known, spinner for brief unknown delays, progress bar only when real percentage data exists.
- Flow-level UX answers to psychology, not just per-screen state: concentrate design effort on a flow's peak moment and its ending, since they're remembered disproportionately (peak-end effect); place a sequence's most critical content or call-to-action at its start or end rather than the middle (serial-position effect); use partial-completion cues to motivate return-and-finish only when the underlying goal is genuinely the user's, never manufactured to inflate engagement (Zeigarnik effect).
- Interface copy — labels, errors, empty states — is a feedback surface in its own right: write it in plain, benefit-oriented language, not system-centric jargon.
- In-progress and navigable state (multi-step form input, pagination/filter/sort state) survives reload, the back button, and sharing a link — persist it rather than letting navigation silently discard it.

**Why the split matters:** ceremony that fires on every screen stops being ceremony — it becomes friction, which is precisely the "AI-generated UI wastes the user's time" failure DesignMotionHQ is naming. Scarcity is what makes a ritual moment register (the same mechanism as the Von Restorff effect: isolated things get noticed; ubiquitous things don't).

---

## Layer 4 — Governance

- **ADR trail.** Every token-level or primitive-level decision gets a dated architectural decision record — not just a comment in code. Future sessions (human or agent) should be able to answer "why is it this way" without archaeology.
- **Anti-pattern list.** Maintain an explicit "do NOT use" list alongside the positive guidance — generic/undifferentiated design, AI purple/pink gradients, emojis as icons, missing `cursor: pointer`, invisible focus states, instant (non-transitioned) state changes, encoding status/severity/destructive intent through color alone (pair it with an icon, label, or shape, and reserve the danger/red channel exclusively for destructive or irreversible actions so it stays trustworthy), distorting a chart's axis scale in a way that overstates the magnitude of a change.
- **Pre-delivery checklist.** Before shipping any UI work, verify contrast ratios, focus visibility, reduced-motion handling, responsive breakpoints, and that new surfaces compose the canonical primitive rather than rolling a new one.
- **Drift gets flagged, not tolerated.** An off-system value is either promoted to a documented, intentional extension of the token set, or corrected — it never just sits there unaddressed.
- **Naming conventions are written down, not inferred.** Token names, CSS class conventions (BEM or otherwise), and component prop naming should be documented once per project rather than reverse-engineered by whoever joins next — this is what makes the anti-pattern list and pre-delivery checklist actually checkable by someone new.

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
- [DesignMotionHQ](https://designmotionhq.com) — home page thesis + `/patterns` catalog (76 patterns, 7 categories, count corrected 2026-09-13 from an initial 75 after enumerating every pattern link directly; the site's own "10 categories" and "75 patterns" summary-stat claims do not match the live page)
- Synthesized in conversation, 2026-09-12.
- Compared layer-by-layer against the full `/patterns` enumeration on 2026-09-12; gap analysis led to Layer 2.5 and its pattern-name index.
- Reviewed the "UX Engine" paid product ($79, Claude Code plugin) on 2026-09-12: not copied in — it's an enforcement tool (out of scope for a spec document), noted only as a candidate complementary tool.
- Reviewed the "Design System Blueprint" (free PDF, user-supplied) on 2026-09-12: contributed the icon-sizing/touch-target note (Layer 2), the easing/duration pairing note (Layer 2), and the naming-convention note (Layer 4) — restated in our own words as standard industry practice (Material Design / Apple HIG carry the same guidance), not copied from the PDF's text or layout.
- Reviewed all 76 individual pattern detail pages in the `/patterns` catalogue on 2026-09-13 (dispatched as 7 parallel research passes, ~11 pages each), each principle extracted and restated in original wording rather than copied from source text. ~30 patterns were judged genuine gaps and folded in across Layers 1, 2, 3, and 4 (grid discipline, proximity/Gestalt grouping, gradient and border-radius token rules, dark-mode-is-not-inversion, overlay viewport-awareness, hover/gesture interaction parity, layout-footprint preservation on interactive states, tooltip content ceiling, preview-vs-committed state, validation-without-disabling, optimistic-UI risk tiering, autosave state visibility, severity-scaled feedback surfaces, flow psychology (peak-end/serial-position/Zeigarnik), microcopy as feedback, persisted navigable state, and two new anti-patterns on color-alone signaling and chart-axis distortion); the remaining ~46 were judged already covered by existing layers, explicitly deferred per-project judgment (Layer 2.5), or too implementation-specific for a house methodology.
