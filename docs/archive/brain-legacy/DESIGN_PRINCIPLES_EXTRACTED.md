> Extracted from arushai-hq/brain/design-system/DESIGN_SYSTEM.md on 2026-03-15. These are the universally applicable design principles from the original ARUSHAI platform design system. FMI-specific and agri-business-specific patterns have been excluded. The full original design system is preserved in design-system/DESIGN_SYSTEM.md for reference.

# ARUSHAI Design Principles — Universally Applicable

## 1. Design Philosophy

**Warm, precise, confident.** ARUSHAI products are not cold enterprise software. They are trusted intelligence partners for users who may have never had access to tools like this before. Every design decision must reflect that responsibility.

**Islamic geometric principles.** Symmetry. Mathematical proportion. Pattern as meaning. Ornamentation that serves structure — never decoration for its own sake. Applied through: grid discipline, geometric icon shapes, pattern motifs in brand panels.

**Platform-first. White-label ready.** Design every screen as if ARUSHAI's name will never appear on it in production. Build for the first client today. Build so the next 100 clients need zero redesign.

**Hardest-user-first.** Design for the most constrained user first — the one with the smallest screen, worst connectivity, lowest technical literacy, most distracting environment. The comfortable user will always be able to use what the constrained user can use. The reverse is not true.

**Human errors visible, not eliminated.** The platform does not try to make humans perfect. It makes errors visible immediately at the point of entry — not discovered days later. Deviations highlighted, not hidden; confirmations required, not assumed.

## 2. Color Token System

Use CSS custom properties (design tokens) for all colors. Never hardcode hex values in component CSS.

**Semantic color pattern:**

| Purpose | Convention |
|---------|-----------|
| Success / confirmed / healthy | Green tone with light green background variant |
| Warning / watch / unverified | Amber/orange tone with light orange background variant |
| Error / critical / breakdown | Red tone with light red background variant |
| Info / system notices | Blue tone with light blue background variant |

**Three-tier alert system:** Green (safe) → Amber (watch) → Red (act now). Applied consistently across all status indicators.

**White-label injection:** Use a single CSS variable `--client-primary` as the injection point for brand color. Every CTA button, active state, and primary highlight references this variable. One-line white-labelling via configuration change.

**Color rules:**
- Never use color as the ONLY indicator of state — always pair with icon + text.
- Warm palette preferred — avoid cold blues as primary or accent colors.
- Red reserved exclusively for genuinely critical states (errors, breakdowns, P1 alerts).

## 3. Typography

**Primary font:** Inter (Google Fonts) — clean, professional, excellent readability.
**Monospace font:** Roboto Mono — for data, codes, audit logs.

**Token-based type scale:** Define each size/weight/line-height/spacing combination as a named token. Use tokens in components, never raw values.

**Number formatting:** Large numbers use locale-appropriate grouping. Currency uses correct symbol and position.

## 4. Spacing System

**8px grid.** All spacing derives from multiples of 8px: 4, 8, 12, 16, 24, 32, 48, 64.

**Token names follow a size scale:** xs (4px), sm (8px), md (16px), lg (24px), xl (32px), 2xl (48px), 3xl (64px).

**Consistency rule:** Use the same spacing token for the same purpose everywhere. Card padding, section gaps, and component margins should be predictable and uniform.

## 5. Component State Requirements

Every interactive component must define these states at minimum:
- **Default** — resting state
- **Hover** — cursor interaction (desktop)
- **Active / Pressed** — during click/touch
- **Disabled** — non-interactive
- **Loading** — awaiting response

For input components, add: **Focus**, **Error**, **Filled** states.

## 6. Mobile-First and Accessibility

- **Mobile-first design.** Always.
- **Minimum touch target:** 48x48px. No exceptions.
- **Test every layout at 320px width minimum.**
- **Offline state must be designed** — never ignored.
- **WCAG 2.1 AA minimum standard** for all interfaces.
- **Contrast ratios:** 4.5:1 minimum for normal text, 3:1 for large text, 3:1 for interactive elements.
- **Semantic HTML:** Use correct elements (`<button>`, `<nav>`, `<main>`, `<table>`) — not divs styled to look like them.
- **Focus management:** Visible focus indicators on all interactive elements. Logical tab order. Focus trapping in modals.

## 7. White-Label Architecture

**What changes per client:** Logo, company name, primary accent color (`--client-primary`), favicon.

**What NEVER changes:** Layout structure, spacing, typography scale, component behavior, animation timing, icon system, accessibility standards.

## 8. Animation Principles

- Functional animations only — never decorative.
- Duration: 150ms for micro-interactions, 300ms for transitions, 500ms for page-level changes.
- Easing: ease-out for entrances, ease-in for exits, ease-in-out for position changes.
- Respect `prefers-reduced-motion` — disable all non-essential animations.

## 9. Data Visualization

- Color-blind safe palettes (distinguishable without color alone).
- Labels on all data points — no chart should require a legend to understand basic meaning.
- Consistent number formatting with locale awareness.
- Responsive charts that work on mobile viewports.
