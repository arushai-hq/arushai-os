# Brain Repo Migration Index

| Field | Value |
|-------|-------|
| **Migration Date** | 2026-03-15 |
| **Source Repo** | arushai-hq/brain |
| **Destination** | arushai-hq/arushai-os/docs/archive/brain-legacy/ |
| **Status** | Brain repo archived and read-only. arushai-os is the sole company-level repository. |

---

## File Classification

| File (in brain repo) | Classification | Reason |
|----------------------|---------------|--------|
| `ARUSHAI_Context_Brief.md` | **MIGRATE** | Master context document v5.6. Founder profile, company foundation, Islamic values, product vision, session system, competitor intelligence. Historical record of ARUSHAI's first business direction. |
| `ARUSHAI_PRD.md` | **MIGRATE** | Full product requirements document for FMI/agri-business platform. Covers 8 modules, IoT hardware specs, infrastructure, security. Shows depth of planning methodology. |
| `partnerships/MVPL_Partnership_Context.md` | **MIGRATE** | Technology partnership strategy with MVPL (poultry integrator). Negotiation framework, competitive analysis, decision framework. Valuable strategic thinking reference. |
| `design-system/DESIGN_SYSTEM.md` | **MIGRATE** | Comprehensive UI design system — color tokens, typography, spacing, 14 component specifications, breakpoints, accessibility standards. Contains reusable principles applicable to future ARUSHAI products. |
| `.claude/INSTRUCTIONS.md` | **MIGRATE** | Early Claude Code configuration for the FMI platform. Historical reference for how CC instructions evolved from this to the current CLAUDE.md + skills approach. |
| `README.md` | **MIGRATE** | Original brain repo overview. Part of the historical record. |
| `updates/archive/ARUSHAI_Context_Brief_DELTA_v5.1_to_v5.2.md` | **MIGRATE** | Competitor intelligence update — Tulasi hatchery framework discovery. |
| `updates/archive/ARUSHAI_Context_Brief_DELTA_v5.2_to_v5.3.md` | **MIGRATE** | Company name correction — "Systems" not "Enterprise Solutions." Key decision record. |
| `updates/archive/ARUSHAI_Context_Brief_DELTA_v5.3_to_v5.4.md` | **MIGRATE** | Competitor intelligence — Tulasi brooding precision protocol. |
| `updates/archive/ARUSHAI_Context_Brief_DELTA_v5.4_to_v5.5.md` | **MIGRATE** | New competitor discovery (Poloxy/Techence IT Solutions). MD response analysis. |
| `updates/archive/ARUSHAI_PRD_DELTA_v5.5_to_v5.6.md` | **MIGRATE** | IoT BOM verification, PanchAngIntel audit, MVPL MD meeting debrief, phased ROI design. |
| `specs/README.md` | **SKIP** | Template description only — no actual screen specifications were created. |
| `specs/screens/layer-1-platform-shell/.gitkeep` | **SKIP** | Empty placeholder. |
| `specs/screens/layer-2-fmi/.gitkeep` | **SKIP** | Empty placeholder. |
| `specs/screens/layer-3-opscore/.gitkeep` | **SKIP** | Empty placeholder. |
| `wireframes/README.md` | **SKIP** | Template description only — no actual wireframes were created. |
| `wireframes/screens/layer-1-platform-shell/.gitkeep` | **SKIP** | Empty placeholder. |
| `wireframes/screens/layer-2-fmi/.gitkeep` | **SKIP** | Empty placeholder. |
| `wireframes/screens/layer-3-opscore/.gitkeep` | **SKIP** | Empty placeholder. |
| `updates/.gitkeep` | **SKIP** | Empty placeholder. |
| `updates/archive/.gitkeep` | **SKIP** | Empty placeholder. |

---

## Additional Files Created During Migration

| File | Purpose |
|------|---------|
| `DESIGN_PRINCIPLES_EXTRACTED.md` | Universally applicable design principles extracted from the FMI-era design system. Excludes agri-business-specific patterns. Applicable to Flint, VIZBOARD, and future ARUSHAI products. |
| `INDEX.md` | This file — migration index and classification record. |

---

## Notes

- The brain repo (`arushai-hq/brain`) is archived and read-only. Its README has been replaced with a deprecation notice pointing to arushai-os.
- All migrated markdown files have an archive header noting migration date and context.
- The brain repo reflected ARUSHAI's original agri-business direction (Feed Mill Intelligence, MVPL partnership, OpsCore). The company has since pivoted to technology/AI products (TradeOS, Flint, VIZBOARD) as defined in the ARUSHAI Operating System Document.
- 11 files migrated, 10 files skipped (all empty placeholders or template-only READMEs with no content).
