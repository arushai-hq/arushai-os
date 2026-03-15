> Migrated from arushai-hq/brain on 2026-03-15. This content is archived — it reflects an earlier business direction. Preserved for historical reference.

---
# ARUSHAI Claude Code Instructions
# Read this before every task.

## Identity
You are building ARUSHAI's multi-tenant SaaS
platform. Every UI decision serves the platform
first, the client second.

## Before Writing Any UI Code
1. Read /design-system/DESIGN_SYSTEM.md completely
2. Check /wireframes/screens/ for existing patterns
3. Never recreate a component that already exists
4. Always use design tokens — never hardcode colours

## Colour Rules — Non-Negotiable
Primary Navy: #1A2F5E
Action Amber: #E8912A
Intelligence Teal: #0D6B6E
Background Cream: #FAF7F2
Success: #2E7D32
Warning: #F57C00
Error: #C62828

NEVER use any other colours without explicit instruction.

## Typography Rules
Import: Google Fonts — Inter (primary)
Never use system fonts for headings.
Always use the type scale from DESIGN_SYSTEM.md

## Component Rules
Build from existing components first.
If a new component is needed — add it to
/wireframes/screens/components/ after building.
Every component must have: default, hover,
active, disabled, loading states minimum.

## Platform Rules
Mobile first. Always.
Minimum touch target: 48x48px always.
Test every layout at 320px width minimum.
Offline state must be designed — never ignored.

## White-Label Rules
Client logo goes in top-left of app bar.
Client name replaces "ARUSHAI" in all
client-facing screens.
Use CSS variable --client-primary for
any colour that clients can customise.

## File Naming Convention
Wireframes: [layer]-[screen-name]-[platform].html
Example: l1-login-mobile.html
Example: l2-production-logging-mobile.html
Example: l2-inventory-dashboard-web.html

## Commit Message Convention
ui: add [screen-name] [platform] wireframe
ui: update [screen-name] — [what changed]
design: update DESIGN_SYSTEM — [what changed]
feat: add [component-name] to component library

## Prototype Requirements
Every HTML wireframe must:
- Be fully self-contained (no external dependencies
  that require internet — embed or use CDN)
- Work when opened directly in browser
- Show all states (use JavaScript to toggle states)
- Include a state switcher panel for review
  (small floating panel: buttons to switch
  between Loading / Default / Error / Offline states)
- Be responsive across all breakpoints
- Include a header comment showing:
  Screen name, platform, version, date,
  spec file reference

## Multi-Tenant Reminder
Every screen that shows company name or logo
must use placeholder variables:
{{CLIENT_NAME}} for company name
{{CLIENT_LOGO}} for logo placement
{{CLIENT_PRIMARY}} for brand colour

This makes white-labelling a configuration
change — not a redesign.
---
