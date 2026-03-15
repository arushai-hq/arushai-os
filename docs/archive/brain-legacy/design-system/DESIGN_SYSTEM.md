> Migrated from arushai-hq/brain on 2026-03-15. This content is archived — it reflects an earlier business direction. Preserved for historical reference.

# ARUSHAI Design System
**Version 1.0 | February 2026**
**Classification: Single Source of Truth — All UI Generation**

> This document is the law that governs every screen, every component, every prototype
> generated for ARUSHAI's SaaS platform. Claude Code must read this file in full before
> writing a single line of HTML or CSS. No deviations without explicit instruction.

---

## 1. Brand Foundation

**Company:** ARUSHAI Enterprise Solutions  
**Platform:** Multi-tenant SaaS — AgriIntel (M1 Feed Mill Intelligence → M4) + OpsCore  
**Tagline:** The Guided Dawn  
**First Client:** TI Industries (Karnataka, India) — Feed Mill operations  

### Design Philosophy

**Warm, precise, confident.**  
ARUSHAI is not cold enterprise software. It is not a startup trying to look clever.
It is the trusted intelligence partner for Indian agri-businesses that have never had
access to tools like this before. Every design decision must reflect that responsibility.

**Islamic geometric principles.**  
Symmetry. Mathematical proportion. Pattern as meaning.
Ornamentation that serves structure — never decoration for its own sake.
Applied through: grid discipline, geometric icon shapes, pattern motifs in brand panels.

**Platform-first. White-label ready.**  
The platform is ARUSHAI. The client sees their own brand.
Design every screen as if ARUSHAI's name will never appear on it in production.
Build it for TI Industries today. Build it so the next 100 clients need zero redesign.

**Floor-first. Then office.**  
The hardest user is a low-literacy mill worker in a noisy Karnataka factory
wearing gloves, working under bright industrial lights, on an Android device
with intermittent connectivity. Design for them first. The office user will
always be able to use what a floor worker can use. The reverse is not true.

**Human errors visible, not eliminated.**  
The platform does not try to make humans perfect. It makes errors visible immediately
at the point of entry — not discovered days later. This philosophy must show in UI:
deviations highlighted, not hidden; confirmations required, not assumed.

---

## 2. Colour Tokens

### Core Palette

| Token Name | Hex | RGB | Usage |
|---|---|---|---|
| `--color-navy` | `#1A2F5E` | 26, 47, 94 | Primary backgrounds, headers, left panels, navigation |
| `--color-amber` | `#E8912A` | 232, 145, 42 | Primary actions, CTA buttons, critical alerts, highlights |
| `--color-teal` | `#0D6B6E` | 13, 107, 110 | Secondary actions, AI/intelligence indicators, links |
| `--color-cream` | `#FAF7F2` | 250, 247, 242 | Page backgrounds, light surfaces, app shell |

### Semantic Colours

| Token Name | Hex | Usage |
|---|---|---|
| `--color-success` | `#2E7D32` | Confirmed entries, completed actions, stock healthy |
| `--color-success-bg` | `#E8F5E9` | Success state backgrounds, toast backgrounds |
| `--color-warning` | `#F57C00` | Amber alerts, 3-day stock warnings, unverified entries |
| `--color-warning-bg` | `#FFF3E0` | Warning state backgrounds |
| `--color-error` | `#C62828` | Errors, 1-day stock critical, machine breakdown P1, locked accounts |
| `--color-error-bg` | `#FFEBEE` | Error state backgrounds, destructive action zones |
| `--color-info` | `#1565C0` | Informational messages, system notices |
| `--color-info-bg` | `#E3F2FD` | Info state backgrounds |

### Neutral Palette

| Token Name | Hex | Usage |
|---|---|---|
| `--color-white` | `#FFFFFF` | Card surfaces, input backgrounds, modal backgrounds |
| `--color-neutral-50` | `#FAFAFA` | Alternate row backgrounds, hover states |
| `--color-neutral-100` | `#F5F5F5` | Disabled backgrounds, skeleton loaders |
| `--color-neutral-200` | `#EEEEEE` | Dividers, borders, separators |
| `--color-neutral-300` | `#DDDDDD` | Input borders default, checkbox borders |
| `--color-neutral-400` | `#BBBBBB` | Placeholder icons, empty state illustrations |
| `--color-neutral-500` | `#999999` | Placeholder text, hint text |
| `--color-neutral-600` | `#666666` | Secondary text, captions, metadata |
| `--color-neutral-800` | `#333333` | Primary text on light backgrounds |
| `--color-text-primary` | `#1A1A1A` | Primary body text, headings on light backgrounds |
| `--color-text-secondary` | `#666666` | Supporting text, labels, captions |
| `--color-text-disabled` | `#AAAAAA` | Disabled state text |

### White-Label Override Token

```css
--client-primary: #E8912A;  /* Default: ARUSHAI Amber */
```

This single token is the white-label injection point for button colours and accent elements.
Every CTA button, active state, and primary highlight uses `--client-primary`.
When a client's brand colour is configured, only this token changes.
All other tokens remain ARUSHAI's system — spacing, type, structure never change.

**Implementation rule:** Never hardcode `#E8912A` directly in component CSS.
Always reference `var(--client-primary)`. This enables one-line white-labelling.

### Colour Usage Rules

**NEVER:**
- Use Navy as a text colour on dark backgrounds (insufficient contrast)
- Use Amber as a background for large text areas (eye fatigue)
- Use colour as the ONLY indicator of state — always pair with icon + text
- Use pure cold blue (`#0000FF`, `#2196F3`) anywhere — this is a warm platform
- Use red for anything that is not genuinely critical (error, breakdown, P1 alert)

**ALWAYS:**
- Amber `--client-primary` for primary action buttons
- Teal for secondary actions, links, AI indicators
- Navy for structural elements (headers, navigation, left panels)
- Cream for page backgrounds — never pure white as the page background
- Green `--color-success` only for completed/confirmed states
- Three-tier alert system: Green (safe) → Amber (watch) → Red (act now)

### Stock Alert Colour System (FMI-specific)

| Days Remaining | Colour Token | Hex | Label |
|---|---|---|---|
| 5+ days | `--color-success` | `#2E7D32` | Safe |
| 3–4 days | `--color-warning` | `#F57C00` | Low |
| 0–2 days | `--color-error` | `#C62828` | Critical |

---

## 3. Typography Scale

### Font Family

**Primary:** Inter (Google Fonts)  
Load URL: `https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap`

**Fallback stack:** `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`

**Monospace (for data, codes, audit logs):** `'Roboto Mono', 'Courier New', monospace`  
Load URL: `https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;500&display=swap`

### Web / Desktop Type Scale

| Token | Size | Weight | Line Height | Letter Spacing | Usage |
|---|---|---|---|---|---|
| `--text-display` | 32px | 700 | 1.2 | -0.5px | Dashboard headers, hero numbers |
| `--text-h1` | 24px | 700 | 1.3 | -0.3px | Page titles |
| `--text-h2` | 20px | 600 | 1.3 | -0.2px | Section headers, card titles |
| `--text-h3` | 16px | 600 | 1.4 | 0 | Subsection headers, list headers |
| `--text-body-lg` | 16px | 400 | 1.6 | 0 | Intro paragraphs, important body |
| `--text-body` | 14px | 400 | 1.6 | 0 | Standard body text, form content |
| `--text-body-medium` | 14px | 500 | 1.6 | 0 | Emphasised body text |
| `--text-caption` | 12px | 400 | 1.5 | 0.1px | Labels, metadata, timestamps |
| `--text-caption-medium` | 12px | 600 | 1.5 | 0.1px | Status badges, tags |
| `--text-micro` | 10px | 400 | 1.4 | 0.2px | Version numbers, fine print |
| `--text-button` | 15px | 600 | 1 | 0.1px | Button labels |
| `--text-button-sm` | 13px | 600 | 1 | 0.1px | Small button labels |
| `--text-data` | 14px | 400 | 1.4 | 0 | Table cells, data values (monospace) |
| `--text-data-lg` | 24px | 700 | 1 | -0.5px | KPI numbers, large metrics |

### Mobile / Floor App Type Scale

**Rule:** All sizes are +2px minimum above web equivalents. Touch interfaces require larger text.
Low-literacy users require maximum readability. No exceptions.

| Token | Mobile Size | Web Equivalent | Usage |
|---|---|---|---|
| `--m-text-h1` | 26px / 700 | 24px | Screen titles on mobile |
| `--m-text-h2` | 22px / 600 | 20px | Card titles, section headers |
| `--m-text-h3` | 18px / 600 | 16px | List item titles |
| `--m-text-body` | 16px / 400 | 14px | All body text on mobile |
| `--m-text-caption` | 14px / 400 | 12px | Supporting text, labels |
| `--m-text-input` | 16px / 400 | 14px | Input fields (prevents iOS auto-zoom) |
| `--m-text-button` | 17px / 600 | 15px | Button labels on mobile |
| `--m-text-numeric` | 28px / 700 | — | Quantity entry fields (glove-friendly) |
| `--m-text-badge` | 13px / 600 | 12px | Status badges on mobile |

### Number Formatting Rule

Indian number system always. No exceptions.

```
CORRECT:   1,00,000    (one lakh)
INCORRECT: 100,000     (western)

CORRECT:   ₹75,000/month
INCORRECT: ₹75000/month

CORRECT:   1,23,45,678  (one crore twenty-three lakhs...)
INCORRECT: 12,345,678
```

Apply `Intl.NumberFormat('en-IN')` in JavaScript for all numeric display.

### Language Support

Platform supports four languages minimum. All UI label strings must be externalised —
never hardcoded in components.

| Language | Code | Script | Notes |
|---|---|---|---|
| English | `en` | Latin | Default, fallback |
| Kannada | `kn` | Kannada script ಕನ್ನಡ | Primary for Karnataka floor workers |
| Hindi | `hi` | Devanagari हिन्दी | Secondary Indian language |
| Marathi | `mr` | Devanagari मराठी | Maharashtra operations |

**RTL note:** Architecture must support RTL for future Arabic expansion (Middle East market).
Use logical CSS properties (`margin-inline-start` not `margin-left`) wherever possible.

---

## 4. Spacing System

**Base unit: 8px**  
All spacing values are multiples of 8px. The 4px half-unit is permitted for micro-spacing only.

| Token | Value | Usage |
|---|---|---|
| `--space-1` | 4px | Icon-to-text gap, micro-spacing, badge padding |
| `--space-2` | 8px | Tight component internal spacing, small gaps |
| `--space-3` | 12px | Form element internal padding, compact lists |
| `--space-4` | 16px | Standard component padding, card content spacing |
| `--space-5` | 20px | Medium gaps between related elements |
| `--space-6` | 24px | Section internal spacing, generous card padding |
| `--space-8` | 32px | Between sections, major component separation |
| `--space-10` | 40px | Large section spacing, hero areas |
| `--space-12` | 48px | Page-level major sections |
| `--space-16` | 64px | Between major page blocks |
| `--space-20` | 80px | Large layout gaps |

### Page Margins

| Platform | Horizontal Margin | Max Content Width |
|---|---|---|
| Mobile (320–480px) | 16px each side | 100% |
| Large Mobile (480–600px) | 20px each side | 100% |
| Tablet Portrait (600–840px) | 24px each side | 100% |
| Tablet Landscape (840–1200px) | 32px each side | 960px |
| Web Desktop (1200px+) | 32px each side | 1200px |
| Large Desktop (1440px+) | Auto centred | 1360px |

### Component Internal Padding Standards

| Component | Padding |
|---|---|
| Card (mobile) | 16px all sides |
| Card (web) | 24px all sides |
| Button (primary, full-width) | 16px vertical, 24px horizontal |
| Button (inline) | 12px vertical, 20px horizontal |
| Input field | 0 vertical, 16px horizontal |
| List item (mobile) | 16px horizontal, 14px vertical |
| List item (web) | 16px horizontal, 12px vertical |
| Modal / Bottom Sheet | 24px horizontal, 24px top, 32px bottom |
| Table cell | 12px vertical, 16px horizontal |
| Alert banner | 12px vertical, 16px horizontal |
| Badge / tag | 4px vertical, 8px horizontal |

### Grid System

**Mobile:** Single column, 16px margins, no gutter  
**Tablet:** 8-column grid, 24px margins, 16px gutters  
**Web:** 12-column grid, 32px margins, 24px gutters  

---

## 5. Component Specifications

### 5.1 Buttons

#### Primary Button

```
Purpose:     One primary action per screen. The most important thing the user can do.
Background:  var(--client-primary) → default #E8912A
Text:        #FFFFFF, var(--text-button), centred
Border:      none
Border-radius: 12px
Height:      Mobile: 56dp | Web: 48px | Compact: 40px
Width:       Mobile: 100% (full-width) | Web: auto (min 140px) or full-width in forms
Shadow:      none default, 0 2px 8px rgba(232,145,42,0.3) on hover

States:
  Default:   as above
  Hover:     background darken 10% → #D4841F
  Active:    background darken 15% → scale(0.98)
  Focus:     outline 3px solid rgba(232,145,42,0.4), outline-offset 2px
  Loading:   background at 80% opacity, spinner (24px white) replaces label,
             pointer-events: none, cursor: not-allowed
             Spinner: CSS border animation, 0.8s linear infinite
             Screen reader: aria-label="Loading, please wait"
  Disabled:  background #DDDDDD, text #AAAAAA, cursor: not-allowed
             Condition: required fields empty OR form invalid
  Success:   brief flash (400ms) background #2E7D32, checkmark icon replaces text,
             then routes to next screen

Usage rules:
  — Maximum ONE primary button per screen on mobile
  — Never stack two primary buttons
  — Always full-width on mobile floor app
  — Loading state mandatory for any action with network call
  — Label must be a verb: "Log In" not "Login", "Save Formula" not "Formula"
```

#### Secondary Button

```
Purpose:     Supporting action — cancel, back, alternative choice
Background:  transparent
Border:      1.5px solid var(--color-neutral-300)
Text:        var(--color-text-primary), var(--text-button)
Border-radius: 12px (matches primary)
Height:      Same as primary for same context

States:
  Hover:     background var(--color-neutral-50), border-color var(--color-neutral-400)
  Active:    background var(--color-neutral-100)
  Focus:     outline 3px solid rgba(0,0,0,0.15), outline-offset 2px
  Disabled:  opacity 0.4, cursor: not-allowed
```

#### Destructive Button

```
Purpose:     Permanent or dangerous actions — delete, archive, override
Background:  transparent (outlined variant) OR #C62828 (filled, for final confirm only)
Border:      1.5px solid var(--color-error)
Text:        var(--color-error), var(--text-button)
Border-radius: 12px

Usage rules:
  — NEVER as the first option shown — always require one additional step
  — Always paired with a confirmation dialog before execution
  — Label must be explicit: "Delete Formula" not just "Delete"
  — Filled red variant only inside confirmation modals as final step
```

#### Text / Link Button

```
Purpose:     Low-emphasis actions — "Forgot password?", "View all", "Cancel"
Background:  none
Border:      none
Text:        var(--color-teal), var(--text-body)
Underline:   none default, underline on hover
Padding:     Vertical padding only — minimum 44dp tap target on mobile

Usage rules:
  — For tertiary actions that don't need visual weight
  — "Cancel" in modals/sheets is always a text button, never outlined
```

#### Icon Button

```
Purpose:     Single icon action — edit, delete, expand, close
Size:        Mobile: 44x44dp minimum tap target, 24dp icon centred inside
             Web: 36x36px tap area, 20px icon
Background:  transparent
Border:      none
Border-radius: 8px
Hover:       background var(--color-neutral-100)
Active:      background var(--color-neutral-200) scale(0.95)
```

---

### 5.2 Input Fields

#### Text Input

```
Purpose:     Text, email, phone, search entry
Height:      Mobile: 56dp | Web: 48px
Width:       Full-width of container (minus page margins)
Background:  #FFFFFF
Border:      1.5px solid var(--color-neutral-300)
Border-radius: 12px
Padding:     0 16px (text vertically centred by height)
Font:        var(--m-text-input) mobile / var(--text-body) web — 16px minimum on mobile
Label:       Above input, 12px, 600 weight, #1A1A1A, margin-bottom 6px
             Labels are ALWAYS visible — never placeholder-only
Placeholder: var(--color-neutral-500) — supplementary hint only

States:
  Default:   Border #DDDDDD
  Focus:     Border var(--client-primary), box-shadow 0 0 0 3px rgba(232,145,42,0.15)
  Filled:    Border #BBBBBB
  Error:     Border var(--color-error), box-shadow 0 0 0 3px rgba(198,40,40,0.12)
             Error message below: 12px, var(--color-error), margin-top 4px
             Error icon inside field right side: 20px red warning icon
  Disabled:  Background var(--color-neutral-100), border #EEEEEE, text #AAAAAA
  Read-only: Background var(--color-neutral-50), border #EEEEEE

Accessibility:
  — <label for="fieldId"> always present, never aria-label replacement
  — aria-describedby links to error message element
  — aria-invalid="true" on error state
  — autocomplete attributes always set correctly
```

#### Numeric Input (Floor App — Glove-Friendly)

```
Purpose:     Quantity entry, weight logging, batch numbers on factory floor
Height:      72dp (larger than standard — glove-tolerant)
Font:        var(--m-text-numeric) — 28px bold
Text-align:  right (numbers align right naturally)
Keyboard:    inputmode="decimal" for numeric pad activation
Border-radius: 16px
Border:      2px solid var(--color-neutral-300) (thicker — more visible on floor)

Additional elements:
  Stepper buttons (optional): minus [-] and plus [+] on either side
    Button size: 56x72dp each
    Background: var(--color-neutral-100)
    Icon: 28px, var(--color-text-primary)
    Long-press behaviour: rapid increment after 500ms hold
  Unit label: right-aligned below field, 12px, var(--color-text-secondary)
    e.g. "kg", "bags", "litres"
  Pre-filled value: shown in Teal #0D6B6E (system-calculated expectation)
  User-edited value: shown in #1A1A1A (confirmed entry)
  Deviation highlight: if edited value differs >3% from pre-fill,
    border turns Amber, inline message: "Deviation detected — add reason"

Confirmation requirement:
  All numeric inputs on floor app require tap of "Confirm" or "Save" — never auto-save
  Confirmation button full-width, 56dp, Amber, below field
```

#### Dropdown / Select

```
Purpose:     Single selection from a list — formula name, machine, shift, reason code
Height:      Mobile: 56dp | Web: 48px
Appearance:  Same styling as text input with chevron-down icon right side (20px)
Tap/Click:   Opens bottom sheet (mobile) or dropdown overlay (web)

Bottom Sheet (Mobile):
  Slides from bottom, 300ms ease-out animation
  Max height: 70vh, scrollable
  Item height: 56dp each
  Selected item: var(--client-primary) background tint, checkmark right
  Search input at top if list > 8 items
  Drag handle at top, tap outside dismisses

Dropdown Overlay (Web):
  Position: absolute below trigger, full trigger width minimum
  Max height: 300px, scrollable
  Item height: 44px, hover background var(--color-neutral-50)
  Border-radius: 12px
  Box-shadow: 0 8px 32px rgba(0,0,0,0.12)
  Keyboard: Arrow keys navigate, Enter selects, Escape closes
```

#### Search Input

```
Purpose:     Filter lists, find ingredients, find formulas
Height:      Mobile: 48dp | Web: 40px
Left icon:   Search icon 20px, var(--color-neutral-500)
Clear button: X icon appears when text entered, right side, 44dp tap target
Border-radius: 24px (pill shape — visually distinct from form inputs)
Background:  var(--color-neutral-100) default, #FFFFFF on focus
Border:      none default, 1.5px solid var(--client-primary) on focus
```

---

### 5.3 Cards

#### Default Card

```
Background:  #FFFFFF
Border-radius: 16px
Shadow:      0 2px 8px rgba(0,0,0,0.06)
Padding:     16px (mobile), 24px (web)
Border:      none

Usage: Standard content container — inventory items, formula list, reports
```

#### Elevated Card

```
Identical to default with:
Shadow:      0 4px 20px rgba(0,0,0,0.10)
Usage:       Modal-like content, featured items, MD dashboard KPI cards
```

#### Bordered Card

```
Background:  #FFFFFF (or state-specific tint)
Border-radius: 12px
Shadow:      none
Border:      1.5px solid var(--color-neutral-200)
Usage:       List items, table row alternatives, settings items
```

#### Status Card (FMI-specific)

```
Left accent bar: 4px wide, full height, colour matches status
  Safe: var(--color-success)
  Warning: var(--color-warning)
  Critical: var(--color-error)
Background:  Status colour at 5% opacity as card tint
Usage:       Stock alerts, machine status, deviation alerts
```

---

### 5.4 Alert Banners

```
Purpose:     System-level messages — offline state, sync warnings, critical alerts
Height:      Auto (min 44px), centred content
Width:       Full-width of screen
Position:    Top of content area (below navigation bar, above page content)

Variants:
  Info:      Background var(--color-info-bg), left border 4px var(--color-info)
             Icon: info circle, var(--color-info)
  Success:   Background var(--color-success-bg), left border 4px var(--color-success)
             Icon: check circle, var(--color-success)
  Warning:   Background var(--color-warning-bg), left border 4px var(--color-warning)
             Icon: warning triangle, var(--color-warning)
  Error:     Background var(--color-error-bg), left border 4px var(--color-error)
             Icon: error circle, var(--color-error)
  Offline:   Background var(--color-amber) SOLID, NO left border
             Text: #FFFFFF, Icon: wifi-off white, 13px
             Full-bleed amber — this is the most critical banner
             role="alert" aria-live="assertive"

Offline Banner Rule:
  Present on EVERY mobile screen when connectivity is lost
  Cannot be dismissed by user — disappears only when connectivity restored
  Content: "● Offline — Limited access"
  This banner is GLOBAL — implement as app-level component, not per-screen
```

### 5.5 Toast Notifications

```
Purpose:     Temporary feedback — action confirmed, error, sync complete
Position:    Mobile: bottom of screen, 16px from bottom, centred
             Web: top-right, 24px from top, 24px from right
Width:       Mobile: calc(100% - 32px) | Web: max 380px, min 280px
Padding:     14px 16px
Border-radius: 12px
Shadow:      0 4px 16px rgba(0,0,0,0.15)
Duration:    Success/Info: auto-dismiss 3s | Error: auto-dismiss 6s | No dismiss on critical

Variants:
  Success:   Background #2E7D32, text #FFFFFF, check icon
  Error:     Background #C62828, text #FFFFFF, error icon
  Info:      Background #1A2F5E (Navy), text #FFFFFF, info icon
  Warning:   Background #F57C00, text #FFFFFF, warning icon

Layout: flex row, icon left (20px) + message text (var(--text-body)) + optional action link right

Accessibility: role="status" for success/info, role="alert" for error/warning
```

### 5.6 Badges and Tags

```
Purpose:     Status indicators, role labels, category tags
Padding:     4px 8px
Border-radius: 6px (slightly rounded rectangle — not pill)
Font:        var(--text-caption-medium) — 12px, 600 weight
Max width:   120px, text truncates with ellipsis

Status badge variants:
  Active:    Background #E8F5E9, text #2E7D32
  Pending:   Background #FFF3E0, text #F57C00
  Critical:  Background #FFEBEE, text #C62828
  Offline:   Background #F5F5F5, text #666666
  AI:        Background rgba(13,107,110,0.1), text #0D6B6E (Teal — AI-generated indicator)
  New:       Background rgba(232,145,42,0.15), text #E8912A

Role indicator badge (RBAC):
  Used next to user names in logs and reports
  Navy background #1A2F5E, white text, smaller padding (3px 6px)
  Examples: "Supervisor" "Worker" "MD" "Nutritionist"
```

### 5.7 Navigation Components

#### Bottom Navigation Bar (Mobile — 4 or 5 items)

```
Position:    Fixed, bottom: 0, full width
Height:      64dp (accounts for home indicator on modern Android)
Background:  #FFFFFF
Border-top:  1px solid var(--color-neutral-200)
Shadow:      0 -2px 8px rgba(0,0,0,0.06)

Tab item:
  Width:     Equal division of full width
  Icon:      24dp, centred
  Label:     10px, below icon, 4dp gap
  Active:    Icon var(--client-primary), label var(--client-primary), 600 weight
             Active indicator: 3px pill above icon, var(--client-primary), width 24px
  Inactive:  Icon var(--color-neutral-400), label var(--color-neutral-500)
  Tap area:  Full height x full item width (64x full width ÷ num tabs)

Tab count per role:
  Floor Worker (Meena): 4 tabs — Home | Log | Alerts | Profile
  Supervisor (Raju): 5 tabs — Home | Log | Machines | Reports | Profile
  Technician (Krishna): 4 tabs — Home | Tickets | Machines | Profile
  MD: 4 tabs — Dashboard | Alerts | Reports | Profile
  (Other roles access via web — no bottom nav)
```

#### Top App Bar (Mobile)

```
Height:      56dp
Background:  #FFFFFF (default) OR var(--color-navy) (contextual — breakdown, critical)
Padding:     0 4dp 0 4dp
Shadow:      0 1px 4px rgba(0,0,0,0.08) — subtle separation only

Left zone:   Back arrow (←) OR hamburger menu — 44dp tap target
Centre:      Screen title — var(--m-text-h2), var(--color-text-primary), centred OR left-aligned
Right zone:  Action icon(s) — max 2 icons, 44dp tap target each, 8dp gap

Note: Screen title should always be the current module/task context, never the app name.
"Production Log" not "Feed Mill Intelligence" — workers need context, not branding.
```

#### Side Navigation (Web / Tablet)

```
Width:       Expanded: 240px | Collapsed: 64px
Position:    Fixed left, full height
Background:  var(--color-navy)
Transition:  width 200ms ease

Header section (top):
  Client logo: 40x40px, 20px from top, 12px from left (expanded)
               16x16px icon version (collapsed)
  Client name: 14px, 500, #FFFFFF, margin-left 12px (hidden when collapsed)

Navigation items:
  Height:    52px each
  Padding:   0 16px (expanded) | 0 (centred, collapsed)
  Icon:      20px, left-aligned (expanded) or centred (collapsed)
  Label:     14px, 500, rgba(255,255,255,0.85) (hidden when collapsed)
  Active:    Left border 3px var(--client-primary), background rgba(232,145,42,0.12)
             Icon and text var(--client-primary)
  Hover:     Background rgba(255,255,255,0.06)
  Separator: 1px rgba(255,255,255,0.10) between groups

Toggle button:
  Bottom of nav, full width
  Icon: chevron-left (expanded) / chevron-right (collapsed)
  Colour: rgba(255,255,255,0.5)

Module section headers (expanded only):
  Text: 10px, 700, rgba(255,255,255,0.4), letter-spacing 0.12em, uppercase
  Padding: 20px 16px 8px
```

### 5.8 Data Table (Web)

```
Purpose:    Inventory lists, audit logs, formula ingredient lists, production history

Table wrapper:
  Border-radius: 12px
  Border: 1px solid var(--color-neutral-200)
  Overflow: hidden (respects border-radius)
  Shadow: 0 1px 4px rgba(0,0,0,0.04)

Header row:
  Background: var(--color-neutral-50)
  Height: 44px
  Border-bottom: 1.5px solid var(--color-neutral-200)
  Cell padding: 12px 16px
  Font: 12px, 600, var(--color-text-secondary), uppercase, letter-spacing 0.08em
  Sortable column: cursor pointer, sort icon right, hover text var(--color-text-primary)

Data row:
  Height: 52px (min — auto for multi-line)
  Border-bottom: 1px solid var(--color-neutral-100)
  Cell padding: 12px 16px
  Font: var(--text-data) 14px, var(--color-text-primary)
  Hover: Background var(--color-neutral-50)
  Last row: no border-bottom

Numeric columns:
  Text-align: right
  Font: Roboto Mono, 14px
  Indian number formatting always

Status column:
  Contains badge component
  Centred horizontally

Action column (rightmost):
  Icon buttons only (edit, view, delete)
  Right-aligned
  Visible on row hover only (web) / always visible (tablet)

Pagination:
  Below table, right-aligned
  Previous / Next buttons + page indicator
  "Showing 1–20 of 145 results" text left-aligned
```

### 5.9 List Item (Mobile)

```
Height:       Minimum 64dp (auto for longer content)
Padding:      16px horizontal, 14px vertical
Border-bottom: 1px solid var(--color-neutral-100)
Background:   #FFFFFF
Active/Press: Background var(--color-neutral-50)

Layout (flex row):
  Left icon or avatar: 40x40dp, margin-right 12dp
  Content block (flex 1):
    Primary text:   var(--m-text-h3) 18px, 600, var(--color-text-primary)
    Secondary text: var(--m-text-caption) 14px, 400, var(--color-text-secondary)
    Margin-top between lines: 2dp
  Right zone:
    Status badge OR chevron OR value
    Aligned to vertical centre

Swipe actions (optional, where applicable):
  Right swipe:  Green zone — confirm / approve
  Left swipe:   Red zone — flag / escalate
  Action reveals after 60px swipe, triggers after 120px
```

### 5.10 Avatar / Role Indicator

```
Size:         Mobile: 40x40dp | Web: 36x36px | Large: 48x48dp
Shape:        Circle
Background:   Role-colour mapping:
  Worker:       Navy #1A2F5E
  Supervisor:   Teal #0D6B6E
  Nutritionist: #7B1FA2 (purple — distinct, food/science association)
  Technician:   #1565C0 (blue — technical/engineering)
  Store Mgr:    #2E7D32 (green — inventory/stock)
  Purchase Mgr: #F57C00 (orange — procurement)
  Finance:      #37474F (dark grey — accounts)
  MD:           Amber #E8912A (gold — executive)
  Admin:        Navy #1A2F5E + crown icon
Text:         2-letter initials, #FFFFFF, bold
              e.g. "RA" for RAJU, "ME" for MEENA

Usage:        All avatars follow this system — never profile photos in v1
```

### 5.11 Loading States

#### Skeleton Loader

```
Purpose:     Placeholder while data loads — prevents layout shift
Appearance:  Rounded rectangles matching content shape
Background:  Linear gradient animation:
             var(--color-neutral-100) → var(--color-neutral-200) → var(--color-neutral-100)
             1.5s ease-in-out infinite (shimmer effect)
Border-radius: Match the component being loaded (12px for cards, 4px for text lines)

Apply to:
  Text lines: height 14px, width varies (60%, 80%, 45% for natural variation)
  Cards:      Full card dimensions
  Table rows: Full row height, columns as blocks

Never show: Empty white space. Always skeleton or spinner — never blank.
```

#### Spinner

```
Usage:       Button loading states, small inline loading
Size:        24px (button) | 32px (inline) | 48px (full-screen overlay)
Colour:      #FFFFFF (on coloured buttons) | var(--client-primary) (on white)
Animation:   CSS border animation, 0.8s linear infinite
```

#### Full-Screen Loading Overlay

```
Usage:       Initial app load, critical data fetch before screen renders
Background:  #FFFFFF, opacity 0.95
Content:     ARUSHAI / client logo (60px) + spinner below (48px) + "Loading..." caption
Position:    Fixed, covers full viewport
z-index:     9999
Fade out:    opacity 0 over 300ms, then remove from DOM
```

### 5.12 Empty States

```
Purpose:     When a list or section has no data — first use, filters return nothing
Position:    Centred in the container (vertical + horizontal)
Padding:     48px top and bottom

Layout (flex column, centred):
  Illustration: Simple geometric icon or abstract shape — 80x80dp
                Colour: var(--color-neutral-300)
                Never use sad/broken imagery — keep warm and instructive
  Title:        20px, 600, var(--color-text-primary), margin-top 16px
  Message:      14px, var(--color-text-secondary), centred, max-width 260px
                Explain what goes here AND how to add first item
  Action btn:   Primary button if there's an action — "Add first formula" etc.
                Margin-top 24px

First-use empty states:
  Different from "no results" empty states
  First-use: warm, welcoming, explains value ("Your formulas will appear here")
  No results: neutral, suggests action ("No results for 'Maize'. Try different search")
```

### 5.13 Modal / Bottom Sheet

#### Bottom Sheet (Mobile — Primary Modal Pattern)

```
Trigger:     Any secondary action requiring choice or confirmation
Overlay:     rgba(0,0,0,0.5), full screen, tap-to-dismiss
Panel:
  Background:   #FFFFFF
  Border-radius: 16px 16px 0 0
  Padding:       24px 16px 32px (+ safe area for home indicator)
  Max-height:    85vh
  Overflow:      scroll if content exceeds
Drag handle:   40x4dp, background var(--color-neutral-300), centred, margin-bottom 20px
Animation:     Slide up 300ms cubic-bezier(0.34, 1.56, 0.64, 1)
Dismiss:       Drag down OR tap overlay OR cancel button
Focus:         Trapped inside sheet while open (accessibility)
```

#### Modal Dialog (Web)

```
Overlay:     rgba(0,0,0,0.4)
Panel:
  Background:   #FFFFFF
  Border-radius: 16px
  Padding:       32px
  Width:         min(90vw, 480px)
  Max-height:    85vh, scrollable
  Shadow:        0 20px 60px rgba(0,0,0,0.2)
Position:      Fixed, centred (left 50%, top 50%, transform -50%)
Animation:     Scale 0.95 → 1.0, opacity 0 → 1, 200ms ease-out
Header:        Title left, close X button right (icon button)
Footer:        Right-aligned buttons, gap 12px: Secondary then Primary (left to right)
```

### 5.14 Progress Indicators

```
Linear progress (forms, uploads):
  Height: 4px
  Background: var(--color-neutral-200)
  Fill: var(--client-primary)
  Border-radius: 2px
  Animated fill

Step indicator (multi-step flows):
  Circles connected by lines
  Active: var(--client-primary) fill, white number
  Completed: var(--color-success) fill, check icon
  Upcoming: var(--color-neutral-200) fill, grey number
  Labels below each step (web) / icon only (mobile)
```

---

## 6. Platform Breakpoints

| Name | Range | Layout | Nav Pattern |
|---|---|---|---|
| Mobile S | 320px – 375px | Single column, 16px margins | Bottom nav |
| Mobile M | 376px – 480px | Single column, 16px margins | Bottom nav |
| Mobile L | 481px – 600px | Single column, 20px margins | Bottom nav |
| Tablet Portrait | 601px – 840px | 2-column possible, 24px margins | Bottom nav OR side nav collapsed |
| Tablet Landscape | 841px – 1200px | 2–3 columns, 32px margins | Side nav collapsed default |
| Desktop | 1201px – 1440px | Full 12-col grid, 32px margins | Side nav expanded |
| Desktop L | 1441px+ | Capped at 1360px content, centred | Side nav expanded |

### Responsive Rules

```css
/* Mobile first. Always. */
/* Base styles = mobile. Add complexity upward. */

@media (min-width: 601px)  { /* Tablet portrait */ }
@media (min-width: 841px)  { /* Tablet landscape */ }
@media (min-width: 1201px) { /* Desktop */ }
@media (min-width: 1441px) { /* Large desktop */ }

/* High contrast media query for floor app sunlight mode */
@media (prefers-contrast: high) {
  /* Increase border widths to 2px, increase font weights */
}
```

---

## 7. Platform-Specific Rules

### 7.1 Floor App (Mobile — Worker, Supervisor, Technician)

These rules are NON-NEGOTIABLE. The floor app is the hardest environment in the system.

**Touch Targets**
- Minimum: 48x48dp (Material Design baseline)
- Preferred: 56dp height for all interactive elements
- Numeric inputs: 72dp height minimum
- Separation between adjacent targets: 8dp minimum
- Never place two tappable elements closer than 8dp apart

**Taps to Complete Primary Task**
- 3 taps maximum from home screen to primary action complete
- Example: Home → Production Log → Save = 3 taps
- Never bury critical actions in menus or submenus

**Offline State**
- Offline banner always visible when connectivity lost — no exceptions
- App must function for core logging tasks while offline
- Sync indicator: persistent icon in top bar showing last sync time
- Unsynced entries visually distinct (amber dot indicator on list items)
- Never lose user data because of connectivity loss — local storage first, sync second

**Visibility / Contrast**
- All text minimum 4.5:1 contrast ratio
- Critical alerts (breakdown, stock out) minimum 7:1
- Interactive elements: border visible even in bright light (2px minimum)
- High-contrast mode available in app settings

**One-Handed Operation**
- Primary actions in bottom 60% of screen (thumb reach zone)
- Navigation in bottom nav bar — always thumb-accessible
- No critical actions in top-right corner (hardest to reach one-handed)
- Floating action button (FAB) allowed for primary create action: bottom-right, 56dp

**Confirmation Requirements**
- All production log saves: confirmation bottom sheet (not just button)
- All deviation acknowledgements: reason required before save
- All breakdown reports: photo/note confirmation screen
- Destructive or high-stakes actions: 2-step confirmation always

**Cognitive Load**
- Maximum 5 data points visible without scrolling on any screen
- Use iconography as primary navigation aid — text is secondary
- Colour-code categories consistently: same colour means same thing everywhere
- Avoid jargon — use operational language workers already know

### 7.2 Office / Web (Nutritionist, Store Manager, Purchase Manager, Finance)

**Data Density**
- Office users want information — don't over-simplify
- Tables preferred over cards for list data (more items visible per screen)
- Side-by-side comparison permitted (formulas, stock periods, reports)
- Charts and graphs for trend data — not just numbers

**Keyboard Power Users**
- Tab order follows logical reading order
- Keyboard shortcuts for frequent actions (document in tooltip on hover)
- "/" opens search globally (follows common SaaS convention)
- Enter submits forms, Escape closes modals/sheets

**Export**
- Every data table has an Export button (PDF and Excel/CSV options)
- Every report has a Print-friendly view
- Export button: secondary outlined, always top-right of data section

### 7.3 MD Dashboard (Executive Mobile View)

**5-Metric Rule**
- Maximum 5 key metrics visible without ANY scrolling
- These 5 metrics are: Production (bags today), Stock Status (worst ingredient), 
  Active Breakdowns count, Deviations flagged, Daily cost variance (₹)
- Everything else is available via drill-down — not pushed to surface

**Instant Comprehension**
- Each metric: large number (display scale, bold) + status colour + trend arrow
- Red/Amber/Green status visible within 2 seconds of opening screen
- Zero learning curve — MD should understand the screen at 6am before coffee

**Drill-Down Pattern**
- Tap any metric → expanded view with last 7-day trend + detail
- Drill-down is optional — MD should never NEED to drill down for daily status
- "All clear" state is as important as "problem" state — green means relax

**Mobile Optimisation**
- Works perfectly at 390px viewport (iPhone 14 Pro) — this is the MD test device
- No horizontal scrolling ever
- Charts: horizontal bar charts preferred over pie charts (mobile readability)
- Numbers: large, bold, Indian format

### 7.4 Multilingual / Low-Literacy Rules

**Language as First-Class Feature**
- Language selector visible before login — not buried in settings
- Language stored per user profile, applied immediately on every session
- All UI labels in translation strings — zero hardcoded English in components
- Numbers, dates, currency: locale-aware formatting

**Icon-First Navigation**
- Every navigation item has an icon — text is secondary, not primary
- Icons must be universally recognisable — no abstract or clever icons
- Icon size on floor app: 28dp minimum in navigation, 24dp inline
- Icon + colour + text for all critical states (never rely on any single channel)

**Low-Literacy Accommodations**
- Short labels — maximum 2 words per navigation item
- Action buttons use simple imperative verbs ("Save", "Send", "Done")
- Avoid abbreviations — spell words out in full
- Error messages: simple language, actionable ("Stock low — order now" not "Inventory threshold breached")

**Numeric Readability**
- Large touch targets on numeric inputs (72dp height)
- One number per row — never pack two numeric fields side by side on mobile
- Pre-filled expected values in Teal — reduces data entry burden
- Confirmation of correct value: tap to accept pre-fill (one tap) vs type override (active correction)

---

## 8. White-Label Rules

### What Changes Per Client

| Element | Changeable | How |
|---|---|---|
| Logo | ✅ Yes | `--client-logo: url(...)` replaces ARUSHAI mark in client screens |
| Company name | ✅ Yes | `--client-name` string, shown in welcome text and browser tab |
| Primary colour | ✅ Yes | `--client-primary` overrides Amber for buttons and accents |
| Subdomain | ✅ Yes | `ti.arushai.com` or custom CNAME |
| Module configuration | ✅ Yes | Which modules are active per tenant (admin setting, not design) |

### What NEVER Changes Regardless of Client

| Element | Reason |
|---|---|
| Layout and grid system | Consistency = quality. Clients cannot break the UX. |
| Typography system | Inter font, size scale, weight hierarchy |
| Spacing system | 8px grid, component padding, touch targets |
| Semantic colour meanings | Red = critical everywhere. Green = safe. Non-negotiable safety signal. |
| Accessibility standards | WCAG AA is the floor, not optional |
| "Powered by ARUSHAI" attribution | Always in footer, Caption size — attribution for platform |
| Navy as structural colour | Headers, nav — part of brand identity visible in shell |
| Offline banner behaviour | Safety-critical feature, cannot be themed away |
| Confirmation patterns | Protecting data integrity — not negotiable per client preference |

### ARUSHAI vs Client Brand Zones

```
ARUSHAI brand visible:           Super Admin portal
                                 Login screen before client logo loads
                                 "Powered by ARUSHAI" footer attribution
                                 Error/maintenance pages

Client brand visible:            All operational screens once logged in
                                 App icon (can be white-labelled)
                                 Browser tab title
                                 Email notifications from platform

Neither brand dominant:          Data tables, charts, forms
                                 These are neutral — data speaks, brand steps back
```

### White-Label Implementation

```css
/* Root variables — set per tenant via JS on app load */
:root {
  --client-primary:     #E8912A;   /* ARUSHAI default */
  --client-name:        "ARUSHAI Platform";
  --client-logo:        url('/assets/arushai-wordmark.svg');
  --client-logo-icon:   url('/assets/arushai-icon.svg');
}

/* Tenant override (loaded from tenant config API) */
[data-tenant="ti-industries"] {
  --client-primary:     #E8912A;   /* TI uses ARUSHAI Amber — no override needed */
  --client-name:        "TI Industries Feed Mill";
  --client-logo:        url('/tenants/ti/logo.svg');
}
```

---

## 9. Accessibility Standards

### Minimum Standard

**WCAG 2.1 Level AA** — mandatory for all screens, all components, all platforms.

### Contrast Ratios

| Context | Minimum Ratio | Target |
|---|---|---|
| Normal text (< 18px) | 4.5 : 1 | 7 : 1 |
| Large text (≥ 18px bold, ≥ 24px normal) | 3 : 1 | 4.5 : 1 |
| UI components (borders, icons) | 3 : 1 | 4.5 : 1 |
| Critical alerts (breakdown, stock critical) | 7 : 1 | 7 : 1 |
| Cream background #FAF7F2 with Navy text #1A2F5E | 12.6 : 1 ✅ | — |
| Cream background with Teal #0D6B6E | 5.2 : 1 ✅ | — |
| Navy background with White text | 13.1 : 1 ✅ | — |
| Amber button with White text | 2.8 : 1 ⚠️ | Must use dark text OR increase amber saturation |

**Amber Button Rule:** White text on Amber (#E8912A) does not pass AA at normal size.
Use `#1A1A1A` dark text on Amber buttons OR increase button text to 18px bold (large text threshold).
**Recommended: Use #1A1A1A (dark navy-black) for all text on Amber backgrounds.**

### Touch Targets (Mobile)

| Target Type | Minimum Size | Preferred |
|---|---|---|
| Standard interactive elements | 48 x 48dp | 56dp height |
| Floor app inputs and buttons | 56 x 56dp | 72dp for numeric |
| Icon buttons | 44 x 44dp | 48 x 48dp |
| Text links (mobile) | Full row height 48dp | — |
| Checkboxes and radios | 44 x 44dp tap area | Full row tappable |
| Navigation items | Full nav bar height | — |

### Semantic HTML Requirements

```html
<!-- Always use semantic elements -->
<button> not <div onclick>
<label for="id"> not aria-label as replacement
<nav> for navigation
<main> for page content
<h1>→<h6> in correct hierarchy (never skip levels)
<table> with <thead><tbody><th scope="col/row">
<ul><ol> for lists
<dialog> for modals

<!-- Always required -->
aria-label on icon-only buttons
aria-describedby linking inputs to error messages
aria-invalid="true" on error state inputs
aria-live="assertive" on offline banner and critical alerts
aria-live="polite" on toast notifications
role="alert" on error messages
aria-expanded on dropdowns and collapsible sections
aria-modal="true" on modals with focus trap
```

### Focus Management

```
Tab order must follow visual reading order (top-left to bottom-right)
Focus ring: 3px solid var(--client-primary), offset 2px — never remove
  (outline: none is NEVER acceptable without a visible replacement)
Modal open: focus moves to first focusable element inside modal
Modal close: focus returns to trigger element
Bottom sheet open: focus moves to first interactive element
Bottom sheet close: focus returns to trigger
```

### Screen Reader Support

- All images have `alt` text (or `alt=""` if purely decorative)
- Charts have text summaries (e.g., "Stock trend: Maize declining 15% week-over-week")
- Loading states announced via `aria-live`
- Dynamic content changes announced appropriately
- Icon-only navigation has `aria-label` with full description

---

## 10. Do's and Don'ts

### ✅ DO — Always

```
DO use var(--client-primary) for ALL primary action colours — never hardcode Amber hex
DO implement offline banner on every mobile screen as a global component
DO use Indian number formatting: 1,00,000 not 100,000
DO maintain 48dp minimum touch targets — 56dp preferred on floor app
DO use semantic HTML elements — <button>, <label>, <nav>, <main>
DO add aria-live="assertive" to all critical system alerts
DO show loading state immediately on any network-dependent action
DO use skeleton loaders — never show blank white space while loading
DO confirm before any destructive or high-stakes action (2-step)
DO design mobile-first — add complexity upward, never strip down
DO use pre-filled expected values in Teal to reduce floor worker data entry
DO show unsynced entries with visual indicator (amber dot)
DO keep MD dashboard to 5 metrics maximum without scroll
DO use role-colour system for avatars consistently across all screens
DO test every screen at 375px (mobile) and 1280px (desktop) minimum
DO add "Powered by ARUSHAI" in footer on all client-facing screens
DO use Inter font loaded from Google Fonts CDN
DO use icon + colour + text for all critical status indicators (never colour alone)
```

### ❌ DON'T — Never

```
DON'T hardcode #E8912A anywhere — always var(--client-primary)
DON'T use colour as the only differentiator for any state
DON'T place critical actions in the top third of mobile screens (unreachable thumb zone)
DON'T use stock photos or literal agricultural imagery in brand panels
DON'T add ARUSHAI logo to client operational screens (only "Powered by" text)
DON'T auto-save critical entries without user confirmation
DON'T use pure cold blue (#2196F3, #0000FF) — this is a warm platform
DON'T use lowercase "arushai" anywhere in the platform
DON'T use pie charts — horizontal bars and line charts only (mobile readability)
DON'T stack two primary (Amber) buttons anywhere
DON'T use outline: none without a visible focus replacement
DON'T use <div onclick> — always <button> for interactive elements
DON'T remove the offline banner from any mobile screen
DON'T place interactive elements closer than 8dp apart (floor app glove concern)
DON'T use white text on Amber (#E8912A) at small sizes — fails contrast
DON'T use abbreviations in floor app UI — spell out full words
DON'T build feature screens before reading this design system in full
DON'T apply client branding to error pages, super admin screens, or ARUSHAI admin portal
DON'T use generic AI imagery (robot hands, neural network graphics, brain icons)
DON'T use literal religious symbols (crescent, star, cross) — geometric patterns only
```

---

## Appendix A — Icon System

Use **Material Icons** (Google) throughout.  
CDN: `https://fonts.googleapis.com/icon?family=Material+Icons+Round`

Round variant preferred — softer, warmer, matches platform personality.

### Core Icon Assignments

| Function | Material Icon Name | Notes |
|---|---|---|
| Home | `home` | |
| Production Log | `assignment` | |
| Inventory / Stock | `inventory_2` | |
| Machine / Equipment | `precision_manufacturing` | |
| Formula / Recipe | `science` | |
| Alerts | `notifications` | Badge count overlay |
| Breakdown / Warning | `warning_amber` | |
| Critical / Error | `error` | |
| Success / Check | `check_circle` | |
| Offline | `wifi_off` | |
| Sync | `sync` | Animate on active sync |
| Settings | `settings` | |
| Profile / User | `person` | |
| Report | `summarize` | |
| AI / Intelligence | `auto_awesome` | Teal colour always |
| Edit | `edit` | |
| Delete | `delete_outline` | |
| Add / Create | `add_circle_outline` | |
| Search | `search` | |
| Filter | `tune` | |
| Export | `download` | |
| Print | `print` | |
| Language | `language` | |
| Back | `arrow_back` | |
| Close | `close` | |
| Expand | `expand_more` | |
| Collapse | `expand_less` | |
| Forward / Next | `arrow_forward` | |
| Fingerprint | `fingerprint` | |
| Lock | `lock` | |
| Dashboard | `dashboard` | |
| Trend Up | `trending_up` | Green |
| Trend Down | `trending_down` | Red |
| Calendar | `calendar_today` | |
| Clock / Time | `access_time` | |
| Photo / Camera | `photo_camera` | Breakdown reporting |
| Voice Note | `mic` | Breakdown reporting |

---

## Appendix B — Animation Principles

**Duration scale:**
```
Instant:     0ms   — state changes (colour, border)
Micro:       100ms — hover effects, icon transformations
Fast:        200ms — modals appearing, toasts appearing
Standard:    300ms — bottom sheets, page transitions
Slow:        500ms — success states, progress fills
```

**Easing:**
```
Standard:    cubic-bezier(0.4, 0.0, 0.2, 1)  — most transitions
Enter:       cubic-bezier(0.0, 0.0, 0.2, 1)  — elements entering screen
Exit:        cubic-bezier(0.4, 0.0, 1, 1)    — elements leaving screen
Bounce:      cubic-bezier(0.34, 1.56, 0.64, 1) — bottom sheet arrival, success states
```

**Floor App Rule:** Respect `prefers-reduced-motion` media query.
If set, eliminate all non-essential animations. Offline banner still animates (safety critical).

---

## Appendix C — Data Visualisation Standards

**Chart library:** Chart.js (CDN available, lightweight, mobile-capable)

**Approved chart types:**
- Horizontal bar chart — stock levels, comparisons
- Line chart — trends over time (consumption, production)
- Simple progress bar — daily targets, batch progress
- Spark lines — compact trend indicators in KPI cards

**Forbidden chart types:**
- Pie / donut charts — poor mobile readability, misleading proportions
- 3D charts — never
- Complex multi-axis charts in mobile view

**Colour in charts:**
- Use semantic colour tokens only (success/warning/error for status data)
- For categorical data: Navy → Teal → Amber → then neutrals
- Never use more than 4 colours in a single chart
- Always include a legend if 2+ series are shown

---

*ARUSHAI Enterprise Solutions · Design System v1.0 · February 2026*  
*Amanah · Ihsan · Khidmah · Islah*  
*This document is the law. Every screen is built from it. Nothing is built without it.*
