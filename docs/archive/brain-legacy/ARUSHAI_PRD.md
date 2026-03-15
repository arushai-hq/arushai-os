> Migrated from arushai-hq/brain on 2026-03-15. This content is archived — it reflects an earlier business direction. Preserved for historical reference.

# ARUSHAI_PRD.md
# Product Requirements Document — Master
**Company:** Arushai Systems Private Limited
**Version:** 1.0 | **Started:** March 2026
**Status:** LIVE DOCUMENT — Updated via delta files from each session
**Repo:** arushai-hq/brain

---

## HOW THIS DOCUMENT WORKS

This is the single source of truth for everything ARUSHAI is building.
- Each specialist session contributes via a delta file (FIND/REPLACE blocks)
- Claude Code applies deltas. Never edited manually.
- Every section has a STATUS tag: `[DEFINED]` `[IN PROGRESS]` `[PENDING]` `[OPEN FLAG]`
- When complete — this document is handed to the developer as the full build spec.

**Delta naming convention:** `ARUSHAI_PRD_DELTA_[session-name]_v[X].md`
**Apply command:** See `APPLY_PRD_DELTA_COMMAND.md`

---

## DOCUMENT INDEX

1. Company & Vision
2. Partner — MVPL Context
3. Platform Architecture
4. IoT Hardware Specification
5. Module M1 — Feed Mill Intelligence
6. Module M2 — Multilingual Field App
7. Module M3 — WhatsApp-to-ERP Agent
8. Module M4 — Transport Optimizer
9. Module M5 — Layer Intelligence
10. Module M6 — HATCHWATCH
11. Module M7 — BROODWATCH
12. Module M8 — PanchAngIntel
13. Infrastructure & Stack
14. Security & Multi-Tenancy
15. Open Flags Register
16. Session Contribution Log

---

# ════════════════════════════════════════
# 1. COMPANY & VISION
# ════════════════════════════════════════
**STATUS:** [DEFINED]

## Company
**Arushai Systems Private Limited**
- Family legacy acronym — each letter = a family member. Non-negotiable name.
- Founded by Irfan, operating from Doha, Qatar
- Building AI-first operational intelligence for Indian agribusiness SMBs

## Vision
Deliver McKinsey-caliber intelligence to SMBs who cannot afford traditional consulting.
Turn competitor-published manual frameworks into automated AI modules.

## Strategy — Three Layers
| Layer | Name | Description |
|---|---|---|
| 1 | Discover | Entry via Business Discovery AI Agent |
| 2 | Intelligise | AI modules that automate domain-specific intelligence |
| 3 | Scale | Productize for SMBs across verticals |

## Primary Competitive Intelligence Source
**Tulasi Technologies** — publishes manual operational frameworks for poultry.
ARUSHAI automates each Tulasi framework into an AI module.
Their published playbooks = ARUSHAI's product specs.

## Revenue Model
- Monthly SaaS license per integrator
- Per-farm/per-shed tiered pricing
- Hardware (IoT) as optional add-on or separate BOM
- Co-founder equity in anchor client (MVPL) = first revenue + validation

---

# ════════════════════════════════════════
# 2. PARTNER — MVPL CONTEXT
# ════════════════════════════════════════
**STATUS:** [DEFINED]

## About MVPL
**Maner Ventures Pvt. Ltd. (MVPL)** — Karnataka poultry integrator, IPO-bound.
- Rebranding: Effective April 1, 2026
- Scale: 600 farmers | 105 staff | 54 buyers | 30 vendors
- Farms: 470+ farms | 940 broiler sheds
- Operations: Hatchery + Soya Mill + Feed Mill + Contract Broiler Farming
- Pipeline: Breeder farm, Layer farm, Cutting plant, Rendering, B2C, Exports
- Geography: Karnataka (primary), Goa and Maharashtra (expansion)

## MD: Toufiq Maner
- Rejected SAP — wants home-grown AI
- Has offered Irfan technology co-founder role with equity
- Structure: Bond paper now → converts to actual IPO shares at listing
- Key insight: Strong believer that Hindu Panchang drives demand planning
- Primary calendar reference: **Mahalaxmi Calendar** — the MD specifically named this as the authoritative source for the Maharashtra-Karnataka belt. This is what traders, shopkeepers, and farmers in this region use day-to-day. Adopt as primary citation for all PanchAngIntel date claims.
- Day-wise granularity: MD wants day-level demand signals, not just month-level. Final product must include day-wise and week-wise planning views.
- MIS integration vision: MD wants PanchAngIntel demand signals visible inside the MIS dashboard — not as a separate module. He wants to see the "whole picture in one view." This reframes PanchAngIntel as platform infrastructure, not a standalone module.
- Gregorian calendar awareness: MD confirmed Easter, Christmas, and other Gregorian events affect his sales and planning. Must be included in the calendar stack.

## ARUSHAI Positioning with MVPL
- **NOT a vendor.** Technology co-founder.
- ARUSHAI owns the intelligence layer. MVPL owns operations.
- IP stays with Arushai Systems Pvt Ltd. MVPL gets exclusive perpetual license.

## IPO Valuation Thesis
| Scenario | Multiple | Valuation |
|---|---|---|
| Without ARUSHAI | 0.64× revenue | ~₹300 Cr |
| With ARUSHAI | 2.5× revenue | ~₹1,250 Cr |
| **ARUSHAI Uplift** | — | **₹950 Cr** |

## ARUSHAI Three Non-Negotiables
1. IP stays with Arushai Systems Pvt Ltd
2. Monthly build cost recovery ₹1–1.5L during development
3. Equity % agreed and written NOW on bond paper

## Profit Share (Agreed)
Max 25% of ARUSHAI profits from MVPL/poultry products only, after all expenses.
Non-MVPL products excluded entirely.

## Key Contacts
- **Toufiq Maner** — MD, decision maker, equity partner
- **Ashraf Tahsildar** — Internal tech champion, operational contact for hardware/deployment

## Incumbent System: Poloxy
- Architecture: JSP Java (2003-era) on E2E Networks
- 12 confirmed gaps: No AI, no mobile app, no photo verification, no cross-module automation,
  no Tally integration, single user per session, no real-time alerts, no predictive analytics,
  no IoT integration, no multilingual support, no WhatsApp integration, no API layer

## ARUSHAI Deployment Strategy
**Option B — Intelligence layer ON TOP of Poloxy.**
Not replacing Poloxy. MD wants to keep it for transaction recording.
ARUSHAI handles everything Poloxy cannot.

---

# ════════════════════════════════════════
# 3. PLATFORM ARCHITECTURE
# ════════════════════════════════════════
**STATUS:** [DEFINED — High Level] [PENDING — Detailed]

## Core Layers
```
┌─────────────────────────────────────┐
│  ARUSHAI Intelligence Layer         │  ← ARUSHAI owns this
│  AI Engine | Alerts | Analytics     │
│  Module Suite M1–M8                 │
├─────────────────────────────────────┤
│  IoT Data Ingestion Layer           │  ← ARUSHAI builds this
│  Go microservice | MQTT | 4G SIM    │
├─────────────────────────────────────┤
│  Data Layer                         │  ← ARUSHAI builds this
│  PostgreSQL | TimescaleDB | pgvector│
├─────────────────────────────────────┤
│  Field Layer                        │  ← MVPL operates this
│  Farm Sensors | Hatchery IoT        │
│  Feed Mill IoT | Transport GPS      │
└─────────────────────────────────────┘
         │ reads from
         ▼
┌─────────────────────────────────────┐
│  Poloxy (Incumbent)                 │  ← MVPL operates, ARUSHAI reads
│  Transaction records only           │
└─────────────────────────────────────┘
```

## Multi-Tenancy
- PostgreSQL Row Level Security (RLS) via Supabase
- Each integrator = isolated tenant
- MVPL = first tenant (anchor)
- Future: other poultry integrators onboarded as tenants

## AI Orchestration (Internal Dev Pipeline)
- Orchestrator: OpenClaw (MiniMax M2.5 via OpenRouter) on VPS
- Workers: Claude Code + Gemini CLI via tmux sessions
- Interface: Telegram
- Output paths: Claude Code → `/root/projects/test-code/cl-code/`

---

# ════════════════════════════════════════
# 3B. ARUSHAI KNOWLEDGE INGESTION PIPELINE
# ════════════════════════════════════════
**STATUS:** [DEFINED — Architecture complete. Build pending.]

## Strategic Purpose
Every ARUSHAI module requires external knowledge: festival calendars, operational
manuals, government bulletins, price circulars, hatchery breed specs.
The Knowledge Ingestion Pipeline is the shared infrastructure that converts
any external document into queryable, structured intelligence for all modules.

Built once. Used by every module. PanchAngIntel (Mahalaxmi Calendar) is
the proof-of-concept use case that validates the architecture.

## Document Sources (current + planned)

| Source | Format | Consumer Module | Ingestion Frequency |
|---|---|---|---|
| Mahalaxmi Calendar (Kannada + Marathi editions) | PDF (image-based) | PanchAngIntel | Annual (Diwali) |
| Tulasi Technologies operational manuals | PDF | M1–M7 module specs | One-time + updates |
| Karnataka Govt gazette holidays | PDF | PanchAngIntel | Annual |
| Veterinary disease bulletins | PDF/web | BROODWATCH M7 | Monthly |
| Soya/maize feed price circulars | PDF/web | Feed Mill M1 | Weekly |
| MVPL Poloxy export data | CSV/Excel | All modules | Monthly |
| Hatchery breed specification manuals | PDF | HATCHWATCH M6 | Per breed update |

---

## Pipeline Architecture — Full Specification

```
DOCUMENT SOURCES (external PDFs, web pages, exports)
        │
        ▼
STEP 1 — ANNUAL/PERIODIC TRIGGER
  Monitor source URL for changes
  Method: SHA-256 hash comparison vs stored hash
  Secondary check: content-level diff (not hash-only — catches same-content/different-hash edge case)
  If changed → trigger ingestion pipeline
  If unchanged → log check, exit
        │
        ▼
STEP 2 — PDF PREPROCESSING
  Convert PDF pages → high-resolution PNG images
  Minimum resolution: 300 DPI
  Tool: pdf2image (Python, wraps poppler)
  Store raw images in ARUSHAI document store (Hetzner volume)
        │
        ▼
STEP 3 — DUAL-TRACK EXTRACTION

  TRACK A — Primary (Structured Extraction via Claude Vision API)
  ─────────────────────────────────────────────────────────────────
  Send each page image to Claude Vision API
  Prompt: domain-specific per document type
  For Mahalaxmi Calendar:
    "Extract all dates, festival names, event types, tithi references,
     and regional notes from this calendar page.
     Return ONLY valid JSON array:
     [{date_gregorian, festival_name_original_script,
       festival_name_english, event_type, severity_hint,
       regional_note, page_number}]
     No preamble. No explanation."
  Output: clean structured JSON
  Cost: ~12 API calls/year for Mahalaxmi. Negligible at ₹50 total/annual run.

  TRACK B — Validation (Raw OCR via PaddleOCR-VL)
  ─────────────────────────────────────────────────────────────────
  Run PaddleOCR-VL (v3.0 PP-OCRv5, 109 languages including Kannada + Devanagari)
  Output: raw extracted text per page in original script
  Purpose: cross-validation only, not primary extraction
  Catches Claude Vision hallucinations via text-level disagreement

        │
        ▼
STEP 4 — ASTRONOMICAL VALIDATION ORACLE
  For every date extracted:
    Compute expected Gregorian date from tithi definition
    using PyJHora or Swiss Ephemeris
  Flag any record where:
    extracted Gregorian date ≠ computed date by >1 day
  Flagged records → human review queue (Ashraf / Irfan)
  Only approved records enter the live planning table

        │
        ▼
STEP 5 — TRANSLITERATION (for Indic script documents)
  Tool: AI4Bharat IndicTrans2 (open source, 22 scheduled Indian languages)
  Convert: Kannada script → English transliteration
  Convert: Devanagari (Marathi) → English transliteration
  Store all three: original_kannada, original_marathi, english_transliteration
  Curated override dictionary for top 50 known festivals
  (prevents IndicTrans2 errors on common terms like Dussehra, Ugadi)

        │
        ▼
STEP 6 — EMBEDDING + DUAL STORAGE

  VECTOR STORE (pgvector — semantic queries)
  ─────────────────────────────────────────────────────────────────
  Embedding model: BGE M3 (BAAI — 100+ languages, hybrid dense+sparse)
  Why BGE M3: hybrid retrieval (dense semantic + sparse BM25) is critical
  for Panchang data — festival names need exact-match BM25 AND
  contextual semantic retrieval simultaneously
  Secondary/validation: Vyakyarth (Krutrim AI — 10 Indic languages, 768-dim)
  Consumer: AI assistant interface — MD asks natural language questions

  RELATIONAL TABLE (PostgreSQL — deterministic planning engine queries)
  ─────────────────────────────────────────────────────────────────
  Consumer: PanchAngIntel planning engine — batch placement calculator
  CRITICAL: Planning engine NEVER queries vector store — always relational table
  Reason: batch placement decisions affecting ₹ crore operations must be
  deterministic, not probabilistic/fuzzy

        │
        ▼
STEP 7 — DIFF REPORT + HUMAN SIGN-OFF
  Generate diff vs previous version: what changed?
  Alert operations team (Ashraf): "N events modified in [source] [year] v[X]"
  Human approval required before patching live planning table
  Audit log: every change timestamped with source version + approver

        │
        ▼
STEP 8 — MONITORING (ongoing, monthly cron)
  Re-fetch source URL
  Hash check → content diff if hash changed
  If changed: re-trigger pipeline from Step 2
  If unchanged: log check timestamp, exit
```

---

## Database Schema — panchang_events Table

```sql
CREATE TABLE panchang_events (
  id                        UUID PRIMARY KEY DEFAULT gen_random_uuid(),

  -- Tithi definition (astronomical truth — never changes)
  tithi_masa                INTEGER,        -- Hindu month number (1=Chaitra, etc.)
  tithi_paksha              VARCHAR(10),    -- 'Shukla' or 'Krishna'
  tithi_day                 INTEGER,        -- 1–15
  calendar_system           VARCHAR(20),    -- 'Amanta' or 'Purnimanta'
  is_adhik_masa             BOOLEAN DEFAULT FALSE,

  -- Gregorian equivalents (year-specific)
  year                      INTEGER NOT NULL,
  date_gregorian_start      DATE NOT NULL,
  date_gregorian_end        DATE,           -- NULL for single-day events

  -- Event identity
  event_name_kannada        TEXT,
  event_name_marathi        TEXT,
  event_name_english        TEXT NOT NULL,
  event_type                VARCHAR(30),    -- 'crash', 'spike', 'minor_dip', 'neutral'
  severity_estimate         DECIMAL(4,2),   -- ARUSHAI estimate (-1.0 to +1.0)
  severity_validated        DECIMAL(4,2),   -- NULL until MVPL sales data confirms
  severity_source           VARCHAR(20),    -- 'arushai_estimate' or 'mvpl_validated'

  -- Regional scope
  region_primary            TEXT[],         -- e.g. ['Karnataka', 'Maharashtra']
  region_modifier_coastal   DECIMAL(4,2),   -- NULL until Phase 2 geo-segmentation
  region_modifier_urban     DECIMAL(4,2),   -- NULL until Phase 2 geo-segmentation
  region_modifier_rural     DECIMAL(4,2),   -- NULL until Phase 2 geo-segmentation

  -- Source + audit
  source_calendar           VARCHAR(100),   -- 'Mahalaxmi Kannada 2026'
  source_publisher          VARCHAR(200),   -- Full publisher name
  source_page               INTEGER,
  source_version_hash       VARCHAR(64),
  extraction_method         VARCHAR(30),    -- 'claude_vision' or 'manual'
  validated_by              VARCHAR(100),   -- Approver name
  validation_date           TIMESTAMP,
  ingestion_date            TIMESTAMP DEFAULT NOW(),

  -- Astronomical validation
  astro_computed_date       DATE,           -- PyJHora computed Gregorian equivalent
  astro_validation_passed   BOOLEAN,        -- extracted date matches computed date ±1 day
  astro_discrepancy_days    INTEGER,        -- if failed, how many days off

  -- Planning engine fields
  affects_batch_planning    BOOLEAN DEFAULT TRUE,
  cascade_group_id          UUID,           -- links events merged by Cascade Rule
  planning_note             TEXT
);
```

---

## OCR Engine Decision Matrix

| Engine | Kannada Support | Devanagari | Layout | Complexity | Decision |
|---|---|---|---|---|---|
| Tesseract 5.x | ⚠️ Fails on conjunct chars | ✅ OK | ❌ Poor grid/table | Low | REJECTED — Indic conjunct failure |
| PaddleOCR-VL v3.0 | ✅ 109 langs incl. Kannada | ✅ Strong | ✅ Good | Medium | ✅ VALIDATION TRACK |
| dots.ocr (Qwen2.5-VL) | ✅ Explicit Kannada training | ✅ | ✅ | Medium | ✅ BACKUP PRIMARY |
| Claude Vision API | ✅ Native multilingual | ✅ | ✅ Excellent | Very Low | ✅ PRIMARY EXTRACTION |
| Google Cloud Vision | ✅ 50+ languages | ✅ | ✅ | Low | ⚠️ Avoided — cloud dependency + cost |

**Decision rationale:**
Claude Vision as primary: 12 API calls/year for Mahalaxmi. Negligible cost.
Returns structured JSON directly — eliminates OCR → parse pipeline complexity.
PaddleOCR-VL as validation track: cross-checks Claude output.
Astronomical oracle as final validation: catches both OCR and Vision errors.

---

## Embedding Model Decision

| Model | Kannada | Marathi | Hybrid Retrieval | Self-hostable | Decision |
|---|---|---|---|---|---|
| BGE M3 (BAAI) | ✅ 100+ langs | ✅ | ✅ dense+sparse+multi-vector | ✅ | ✅ PRIMARY |
| Vyakyarth (Krutrim) | ✅ explicit Indic | ✅ explicit Indic | ❌ dense only | ✅ | ✅ VALIDATION |
| paraphrase-multilingual-mpnet | ✅ | ✅ | ❌ | ✅ | ❌ Weaker than BGE M3 |
| text-embedding-3-large (OpenAI) | ✅ | ✅ | ❌ | ❌ | ❌ Cloud dependency |

**Decision: BGE M3 primary + Vyakyarth validation.**

---

## Multi-Year Forward Planning Architecture

**The RAG-only approach has a hard ceiling: ~12 months.**
The 2027 Mahalaxmi Calendar is not published until Diwali 2026.
Planning engine needs 18-month rolling forward visibility.

**Resolution — Three-layer date sourcing:**

| Source | Coverage | Accuracy | Use |
|---|---|---|---|
| Mahalaxmi Calendar (RAG) | Current year only | Ground truth | Live planning year |
| Panchang API (Prokerala / drikpanchang) | Multi-year forward | High | Next year forward planning |
| Astronomical computation (PyJHora/Swiss Ephemeris) | Unlimited forward | Computed | Validation oracle + 2+ years out |

**Architecture:**
```
For current year dates  → Mahalaxmi Calendar RAG (verified source)
For next year dates     → Panchang API (programmatic, REST)
For 2+ year dates       → Astronomical computation engine
Annual verification     → Mahalaxmi Calendar patches all sources for current year
```

**Action: Evaluate Prokerala Panchang API and drikpanchang API before Phase 1 build.**
See Flag F18.

---

## Failure Mode Registry

| Failure | Detection | Impact | Fallback |
|---|---|---|---|
| Mahalaxmi PDF URL changes / goes behind paywall | Monitor returns 404/403 | Annual ingestion breaks | Mirror PDF in ARUSHAI Hetzner volume at each ingestion |
| Claude Vision API unavailable during ingestion | API error response | Primary extraction fails | Switch to PaddleOCR-VL (Track B) as primary |
| PDF layout redesign (new calendar format) | Extraction returns <80% expected records | Prompt fails silently | Human-in-loop flag + prompt update |
| IndicTrans2 wrong transliteration | Override dictionary miss | Wrong English event name in DB | Curated override dict for top 50 events, expand annually |
| Hash false negative (different hash, same content) | Spurious re-ingestion | Wasted processing | Secondary content-level diff before triggering pipeline |
| Astronomical validation fails >5% records | Validation oracle | Data quality risk | Block ingestion, alert Irfan, manual review required |
| PaddleOCR/Claude Vision date discrepancy >2 events | Cross-check diff | Conflicting extraction | Human review queue for all flagged records |

---

## Legal + IP Considerations (OPEN FLAG F11)

Mahalaxmi Calendar is copyright Saraswati Publishing Co. Pvt. Ltd.
ARUSHAI builds commercial SaaS using their festival data.

**Three-path resolution:**

Path A — Publisher licence agreement
  Contact: editor@mahalaxmipanchang.com
  Proposal: ARUSHAI cites Mahalaxmi as named source in product + pays licence fee
  Publisher benefit: product placement in an IPO-trajectory tech platform
  Risk: licence terms unknown, timeline uncertain

Path B — Facts are not copyrightable (legal principle)
  Dates of festivals are facts, not creative expression
  Layout, descriptions, images are copyrighted — ARUSHAI stores neither
  ARUSHAI stores: dates + event names only
  Requires: Indian legal opinion confirming this position
  Risk: low but non-zero — get legal opinion before go-live

Path C — Astronomical independence
  ARUSHAI computes all dates independently (PyJHora / Swiss Ephemeris)
  Mahalaxmi Calendar used for verification only, not as data source
  Copyright dependency disappears entirely
  This is the architecturally cleanest long-term position

**Recommended path: B + C in parallel. Legal opinion on B. Build C for Phase 2.**
**Must resolve before commercial go-live. See Flag F11.**

---

## Adhik Maas Handling

Adhik Maas (extra lunar month) occurs every ~32–33 months.
2026 has Adhik Jyeshtha (May 17–Jun 15).
Next occurrence: approximately 2029.

**Pipeline must treat Adhik Maas as a year-level parameter, not an event row.**

```sql
-- Year-level metadata table
CREATE TABLE panchang_year_metadata (
  year              INTEGER PRIMARY KEY,
  has_adhik_masa    BOOLEAN DEFAULT FALSE,
  adhik_masa_name   TEXT,           -- e.g. 'Adhik Jyeshtha'
  adhik_masa_start  DATE,
  adhik_masa_end    DATE,
  cascade_impact    TEXT,           -- human note on how it shifts dead zones
  severity_multiplier DECIMAL(4,2) DEFAULT 1.0  -- 1.5 for Adhik year
);
```

Planning engine checks `panchang_year_metadata` first on every calculation.
If `has_adhik_masa = TRUE`: apply Adhik Maas severity multiplier to all
overlapping and downstream suppressed periods. Recalculate Cascade Rule.

---

# ════════════════════════════════════════
# 4. IoT HARDWARE SPECIFICATION
# ════════════════════════════════════════
**STATUS:** [IN PROGRESS — Verification session underway]

## Scope
Full MVPL lifecycle IoT — NOT farms only.
Farms + Hatchery + Feed Mill + Soya Mill + Transport Fleet

## Base Unit
940 sheds (470 farms × 2 sheds each)
All per-shed costs × 940 = total fleet cost.

## Section A — Contract Broiler Farm Sheds (940 units)

### C01 | Temperature + Humidity Sensor
**STATUS:** [DEFINED — VERIFIED]
- Part: SHT31-DIS-F2.5KS (PTFE filter membrane) — NOT bare DIS-B
- Reason: Poultry ammonia degrades bare sensor within weeks
- Verified price: ₹700/shed (assembled BOM)
- Source: Robu.in SKU R154994 ₹576 incl.GST + BOM ₹124 = ₹776 retail. Bulk 940u ~₹575.
- Model was ₹1,000 → **CORRECTED to ₹700**

### C02 | Water Flow Meter
**STATUS:** [DEFINED — VERIFIED] [OPEN FLAG F01]
- Part: UPVC Turbine DN25, ±5% accuracy, pulse output, LCD totalizer
- Rejected: YF-S201 (±10% — useless for AI signals)
- Rejected: Industrial RS485 (₹24K+ — overkill)
- Verified price: ₹2,000/shed (BOM: meter ₹1,800 + fittings ₹150 + cable ₹50)
- Source: IndiaMART UPVC turbine DN25 ₹1,500–2,500 retail 2025
- Model was ₹2,000 → **CONFIRMED CORRECT**
- ⚠️ **FLAG F01:** 1 meter per shed inlet (₹18.8L) vs 1 per drinker line (₹94L) — UNRESOLVED

### C03 | Feed Load Cell + Controller
**STATUS:** [DEFINED — VERIFIED] [OPEN FLAGS F02, F03]
- Application: Outdoor feed bin/silo weighing (industry standard for FCR tracking)
- Rejected: Indoor hopper + HX711 (EMI drift from motors/fans — unreliable)
- Recommended: Outdoor bin + ARUSHAI custom ESP32 controller (Scenario C)
- Load cells: 3× Rudrra RSL-310 500kg alloy steel
- Controller: Custom ESP32 + NAU7802/ADS1231 24-bit industrial ADC (not HX711)
- Verified price: ₹9,000/shed (custom IoT controller scenario)
- Sources: Rudrra RSL-310 ₹1,800–3,250 (rudrrasensor.com). Spark Drives RS485 indicator ₹7–9K (sparkdna.co.in).
- Model was ₹3,000 → **CORRECTED to ₹9,000 — ₹56.4L underestimate at 940 sheds**
- ⚠️ **FLAG F02:** Outdoor bin vs indoor hopper confirmed? — UNRESOLVED
- ⚠️ **FLAG F03:** Build custom ARUSHAI ESP32 weighing board? ₹5.6–7.5 Cr savings. Hardware IP. — NEEDS REVIEW

### C04 | IoT Gateway
**STATUS:** [PENDING VERIFICATION]
- Model: ₹1,500/shed
- Note: F03 decision (custom weighing board) may consolidate with gateway

### C05 | IP Camera (mortality AI)
**STATUS:** [PENDING VERIFICATION]
- Model: ₹3,500/shed

### C06 | Wiring, Conduit, Power Supply
**STATUS:** [PENDING VERIFICATION]
- Model: ₹1,200/shed

## Section B — Hatchery (HATCHWATCH M6)
**STATUS:** [PENDING — Session required]
- Components TBD: Temperature, humidity, CO2, egg weight sensors, candling camera

## Section C — Feed Mill (M1)
**STATUS:** [PENDING — Session required]
- Components TBD: Silo load cells, motor current sensors, throughput meters

## Section D — Transport Fleet (M4)
**STATUS:** [PENDING — Session required]
- Components TBD: GPS tracker, temperature logger, door/seal sensors

## Section E — Annual Connectivity
**STATUS:** [PENDING — Session required]
- Components TBD: 4G SIM per shed, VPS costs, API/cloud costs

---

# ════════════════════════════════════════
# 5. MODULE M1 — FEED MILL INTELLIGENCE
# ════════════════════════════════════════
**STATUS:** [PENDING — Session required]

## Purpose
[TBD — Brainstorm session needed]

## Key Features
[TBD]

## Data Inputs
[TBD]

## AI Logic
[TBD]

## Integration Points
[TBD]

---

# ════════════════════════════════════════
# 6. MODULE M2 — MULTILINGUAL FIELD APP
# ════════════════════════════════════════
**STATUS:** [PENDING — Session required]

## Purpose
[TBD — Brainstorm session needed]

## Languages Required
Kannada (primary), Hindi, Marathi, English

## Key Features
[TBD]

## Offline Capability
Required — farm connectivity unreliable

---

# ════════════════════════════════════════
# 7. MODULE M3 — WHATSAPP-TO-ERP AGENT
# ════════════════════════════════════════
**STATUS:** [PENDING — Session required]

## Purpose
[TBD — Brainstorm session needed]

## Key Features
[TBD]

## Integration Points
WhatsApp Business API → ARUSHAI backend → Poloxy (read/write)

---

# ════════════════════════════════════════
# 8. MODULE M4 — TRANSPORT OPTIMIZER
# ════════════════════════════════════════
**STATUS:** [PENDING — Session required]

## Purpose
[TBD — Brainstorm session needed]

## Key Features
[TBD]

---

# ════════════════════════════════════════
# 9. MODULE M5 — LAYER INTELLIGENCE
# ════════════════════════════════════════
**STATUS:** [PENDING — Session required]

## Source Framework
Tulasi Technologies — Layer Feed Cost/Dozen framework

## Purpose
[TBD — Brainstorm session needed]

## Key Features
[TBD]

---

# ════════════════════════════════════════
# 10. MODULE M6 — HATCHWATCH
# ════════════════════════════════════════
**STATUS:** [PENDING — Session required]

## Purpose
Hatchery Chick Quality Intelligence

## Source Framework
Tulasi Technologies — Hatchery manual

## Key Features
[TBD — Brainstorm session needed]

## IoT Dependencies
Hatchery sensors (Section B above — pending verification)

---

# ════════════════════════════════════════
# 11. MODULE M7 — BROODWATCH
# ════════════════════════════════════════
**STATUS:** [PENDING — Session required]

## Purpose
Brooding Precision Intelligence — monitors broiler shed environment
from day 1 chick placement to market weight.

## Source Framework
Tulasi Technologies — Brooding manual

## Key Monitoring Parameters
- Temperature (shed) — C01 SHT31 sensor
- Humidity (shed) — C01 SHT31 sensor
- Water consumption — C02 flow meter
- Feed consumption — C03 load cell + controller
- Mortality — C05 IP camera (AI vision)
- Bird weight — [TBD]

## Alert Logic
[TBD — Session required]

## AI Recommendations
[TBD — Session required]

## Key Performance Indicators
- FCR (Feed Conversion Ratio) — primary KPI
- Water-to-feed ratio — early health signal
- Mortality rate — daily tracking
- Growth curve vs target

---

# ════════════════════════════════════════
# 12. MODULE M8 — PANCHANGINTEL
# ════════════════════════════════════════
**STATUS:** [IN PROGRESS — Brainstorm session 1 complete. MD feedback integrated. Phase 2 scope defined.]

---

## Strategic Reframe (Confirmed — March 2026 MD Meeting)

PanchAngIntel is NOT a standalone module.
It is the **Demand Signal Engine** — platform-level infrastructure that feeds every other module.

Every module that involves timing or volume (M6 HATCHWATCH, M7 BROODWATCH, M1 Feed Mill,
M4 Transport) consumes PanchAngIntel demand signals as input.
The MIS dashboard surfaces a demand signal indicator (🟢 / 🟡 / 🔴) on every relevant screen.

**This makes PanchAngIntel structurally irreplaceable. It is the intelligence layer's
backbone, not a feature.**

---

## Purpose
Convert the predictable Hindu Panchang demand oscillation — plus Islamic Hijri and
Gregorian calendar events — into a systematic, rules-based batch planning engine.

Solves: MD currently plans by instinct and experience. At 940-shed scale, instinct
fails. PanchAngIntel gives proactive, mathematically precise, forward-looking batch
placement and halt recommendations.

---

## Primary Geography
Karnataka (primary) | Maharashtra (secondary — Goa + western Maharashtra border)

## Consumer Lens
End consumer = Hindu households (primary) + Muslim households (secondary, Eid events).
NOT about farmer religion. About MARKET demand at the buyer end.

---

## Primary Calendar Source — AUTHORITATIVE
**Mahalaxmi Calendar** — named by MD Toufiq Maner as the ground-truth almanac for the
Maharashtra-Karnataka belt. Published annually. Used by traders, shopkeepers, farmers
in this region as the primary reference.

- All PanchAngIntel date claims must be cited against Mahalaxmi Calendar.
- Secondary verification: drikpanchang.com, hindu-blog.com, GaneshaSpeaks.
- See permanent rule: ALWAYS web-search calendar system per state before any
  cross-market timing claim. Never assume Purnimanta for any state without verification.

---

## Triple Calendar Stack
PanchAngIntel tracks three overlapping calendar systems simultaneously:

| Layer | Calendar | Primary Events |
|---|---|---|
| 1 | Hindu Panchang — Karnataka Amanta | Shravan, Adhik Maas, Chaturmas, Pitru Paksha, Navratri, Dussehra, Diwali, Ugadi, Ekadashi |
| 2 | Islamic Hijri | Eid al-Fitr, Eid al-Adha (Bakrid), Muharram |
| 3 | Gregorian | Christmas (Dec 25, fixed), New Year (Jan 1, fixed), Easter Sunday (computed — Meeus/Jones/Butcher algorithm), Valentine's Day (Feb 14, fixed — restaurant channel signal only) |

**Gregorian Layer Implementation Notes:**
- Easter is the only moveable Gregorian event. Computed algorithmically for any year. Zero annual manual entry.
- Valentine's Day = restaurant/catering channel demand signal. NOT consumer-level signal. Urban Bangalore buyers primary. Rural MVPL farms supply urban restaurants — downstream signal is real even if rural consumers don't observe.
- Christmas and Easter = coastal + urban weighted. Apply F19 region modifiers: full spike for coastal Karnataka, attenuated for rural. Karnataka state avg Christian ~1.9%; coastal Dakshina Kannada/Udupi ~18–22%.
- All four Gregorian events are Phase 1 scope. No further Gregorian events added unless deviation exceeds ±10% materiality threshold.

**CRITICAL — Calendar System Rule:**
Karnataka follows Amanta (month ends on Amavasya/new moon).
Maharashtra ALSO follows Amanta — NOT Purnimanta.
Purnimanta = North India only (UP, Bihar, Rajasthan).
Karnataka Shravan = Maharashtra Shravan = identical dates.
Source: Mahalaxmi Calendar, drikpanchang.com, hindu-blog.com Marathi Shravan.

---

## Verified 2026 Key Dates (Karnataka Amanta unless noted)

| Event | Verified Date | Calendar | Source |
|---|---|---|---|
| Ugadi | March 19 | Amanta | Karnataka Govt, drikpanchang.com |
| Eid al-Fitr | March 21 | Hijri | Karnataka Govt |
| Adhik Jyeshtha begins | May 17 | Amanta | shriramtemple.org.in, hindupad.com |
| Adhik Jyeshtha ends | June 15 | Amanta | Confirmed |
| Bakrid (Eid al-Adha) | May 28 | Hijri | Karnataka Govt (gazetted) |
| Chaturmas begins | July 25 (Devshayani Ekadashi) | Both | dharmikvibes.com, panditjionway.com |
| Shravan begins (Karnataka + Maharashtra) | August 13 | Amanta | hindu-blog.com, GaneshaSpeaks |
| Shravan ends | September 11 | Amanta | Confirmed |
| Post-Shravan pent-up window | September 12–25 | — | Derived |
| Pitru Paksha ends (Sarva Pitru Amavasya) | October 10 | Both | dharmikvibes.com |
| Dussehra / Vijaya Dashami | October 20 | Both | calendardate.com, goodreturns.in |
| Diwali / Lakshmi Puja (national) | November 8 | Both | NSE India, timeanddate.com |
| Deepavali (Karnataka Govt holiday) | November 10 | — | ClearTax Karnataka 2026 |
| Chaturmas ends (Devutthana Ekadashi) | November 20 | Both | dharmikvibes.com |
| Good Friday | April 3 | Gregorian | Easter −2. Computed via Meeus/Jones/Butcher algorithm. Coastal Karnataka signal only (Dakshina Kannada, Udupi ~18–22% Christian). ⚠️ F24: schema treatment pending. |
| Easter Sunday | April 5 | Gregorian | Computed via Meeus/Jones/Butcher algorithm — not hardcoded. Range: Mar 22–Apr 25 annually. Phase 1 algorithm implementation: no manual entry ever required. |
| Christmas | December 25 | Gregorian | Fixed |

**DEMAND PERCENTAGES ARE ARUSHAI ESTIMATES — not sourced from published data.
Must always be labelled explicitly as "ARUSHAI estimates" in any document.**

---

## Annual Demand Map — 2026 (Karnataka)

**All demand % = ARUSHAI estimates. Not sourced from published data. Label explicitly in all documents.**

⚠️ THREE PERMANENT CORRECTIONS applied in Points 2/3/4 session (March 8, 2026):
1. Chaitra Navratri (Mar 20–27) was MISSING from prior map. Added.
2. Mysore Dasara / Navratri (Oct 11–20): Signal was WRONG — prior map showed suppress. Karnataka = SPIKE.
3. Post-Shravan framing was WRONG — prior map said "recovery window." Ganesh Chaturthi is an ACTIVE 10-day spike.

| Period | Dates | Signal | Demand vs Baseline (ARUSHAI est.) | Driver |
|---|---|---|---|---|
| Makar Sankranti | Jan 14 | 🟢 SPIKE | +20–30% | Harvest festival; meat consumption traditional |
| Jan–Feb baseline | Jan 15–Feb 25 | 🔵 | Normal | Wedding season ongoing (Chaturmas ended Nov 20) |
| Maha Shivaratri | Feb 26 | 🟡 SOFT DIP | −10–20% | Fast day; single-day, recovers immediately |
| Holi | Mar 4 | 🟢 MILD SPIKE | +10–20% | Celebration; North-leaning but Karnataka impact real |
| Pre-Ugadi baseline | Mar 5–18 | 🔵 | Normal | — |
| Ugadi + Eid convergence [NOTE: Navratri fast starts same day — see row below] | Mar 19 | 🟢🟢 SPIKE | +30–60% | Ugadi peak + Mar 21 Eid amplifies; rare convergence |
| Chaitra Navratri fast dip [CORRECTION: was missing] | Mar 20–27 | 🟡 DIP | −20–30% | 9-day fast follows Ugadi; overlapping window |
| Ram Navami | Mar 27 | 🟡 NEUTRAL | Minimal | End of Chaitra Navratri; minor signal |
| Post-Navratri + Hanuman Jayanti | Mar 28–Apr 2 | 🔵 | Normal | Hanuman Jayanti Apr 2 = minor fast day only |
| Akshaya Tritiya | Apr 19 or 20 | 🟢 SPIKE | +15–20% | ⚠️ F20: Karnataka date ambiguity. Verify from Mahalaxmi Kannada Calendar. |
| Basava Jayanthi | Apr 20 | 🟡 NEUTRAL | Minimal | Karnataka gazetted holiday; cultural only |
| Apr–May baseline | Apr 3–May 16 | 🔵 | Normal | — |
| Adhik Maas | May 17–Jun 15 | 🔴 CRASH | −50–70% | Extra lunar month; widespread meat avoidance |
| Bakrid (inside Adhik Maas) | May 28 | 🟡 PARTIAL OFFSET | Net: −35–55% | Muslim feast partially offsets crash; net still negative |
| Post-Adhik recovery | Jun 16–Jul 24 | 🟢 MILD | +5–20% | Narrow pent-up release; Cascade Rule applies (see below) |
| Early Chaturmas + Varalakshmi Vratam | Jul 25–Aug 12 | 🟡 SOFT SUPPRESS | −25–45% | Chaturmas begins Jul 25; Varalakshmi Vratam Aug 8 intensifies that week |
| SHRAVAN (peak crash) | Aug 13–Sep 11 | 🔴🔴 SEVERE | −60–80% | Deepest vegetarian month; 30-day sustained crash |
| Shravana Somavara Vrat | Aug 17, 24, 31, Sep 7 | 🔴 DEEPEST DAYS | Bottom of Shravan crash | 4 Mondays; maximum suppression days of year |
| Mangala Gauri Vrat | Aug 18, 25, Sep 1, 8 | 🔴 SECONDARY LOW | Compounds Shravan crash Tuesdays | Women's fast; 4 Tuesdays inside Shravan |
| Swarna Gowri Vrata | Sep 13 or 14 | 🟡 MINOR DIP | −10–15% | ⚠️ F23: date conflict. Verify from Mahalaxmi Kannada Calendar. |
| Ganesh Chaturthi — ACTIVE SPIKE [CORRECTION: was labelled recovery] | Sep 14–25 | 🟢🟢 MAJOR SPIKE | +30–50% | 10-day festival; active demand driver, not passive recovery |
| Pitru Paksha | Sep 26–Oct 10 | 🟡 SOFT SUPPRESS | −30–50% | Ancestor fortnight; meat avoidance |
| Mysore Dasara — KARNATAKA SPIKE [CORRECTION: was suppress] | Oct 11–20 | 🟢🟢🟢 STRONG SPIKE | +25–40% | Tourism surge + festivity = net spike. Not North India Navratri suppress. |
| Dussehra / Vijaya Dashami | Oct 20 | 🟢🟢 SPIKE | +20–35% | Fast break; supply gap from crash resolves |
| Post-Dussehra baseline | Oct 21–Nov 5 | 🔵 | Normal | Wedding season building |
| Diwali pre-peak | Nov 6–7 | 🟢 MILD SPIKE | +20–30% | Dhanteras + pre-Diwali |
| Diwali + Naraka Chaturdashi (Karnataka combined) | Nov 8–10 | 🟢🟢🟢 PEAK | +50–70% | Nov 8 = national Diwali + Karnataka Naraka Chaturdashi combined. Nov 10 = Karnataka Deepavali gazetted holiday. Do NOT apply North India Nov 7 Naraka Chaturdashi pattern. |
| Wedding Season (post-Chaturmas) | Nov 11–24 | 🟢🟢🟢 STRONG | +40–70% | Chaturmas ends Nov 20; muhurat season opens fully |
| Kanakadasa Jayanthi | Nov 27 | 🟡 NEUTRAL | Minimal | Karnataka gazetted holiday; cultural significance only |
| December peak | Nov 26–Dec 31 | 🟢🟢🟢 STRONG | +50–80% | Peak wedding + Christmas + year-end catering |

---

## Planning Engine — Core Parameters

| Parameter | Value | Notes |
|---|---|---|
| GOP-MIN | 42 days | Minimum grow-out period |
| GOP-MAX | 58 days | Maximum grow-out period |
| Market Entry Buffer (pre-crash) | 10 days | Placement must finish before demand falls |
| Market Entry Buffer (pre-spike) | 7 days | Targeting lead ahead of peak |
| Chick Procurement Lead Time | 7 days | Alert trigger (not in grow-out calc) |
| Clearance Period (post-crash) | 5 days | Market recovery before next batch |
| GORB — Summer (Mar–May) | +7 days | Added to GOP |
| GORB — Monsoon (Jun–Sep) | +5 days | Added to GOP |
| GORB — Optimal (Oct–Feb) | +0 days | No adjustment |

---

## Three Core Formulas

```
STOP-HATCH  = Crash Start − MEB(10) − GOP-MIN(42) − GORB
TARGET-HATCH = Spike Peak − Pre-Spike MEB(7) − GOP-MAX(58)
RESUME-HATCH = Crash End + Clearance Period(5)
```

**ARITHMETIC RULE (permanent):** Every placement date calculation must be
verified by: Placement Date + GOP days = Target Market Date.
Never allow "rounding" to bridge more than 3 days of GOP gap.

---

## Cascade Rule
When two suppressed periods are separated by fewer than GOP-MIN (42) days,
merge into one continuous dead zone. No placement during the merged block.

**2026 Cascade:** Adhik Maas (ends Jun 15) → recovery gap 40 days → Chaturmas
(starts Jul 25) → Shravan (Aug 13–Sep 11) → Pitru Paksha (Sep 26–Oct 10).
Gap between Adhik Maas end and Chaturmas start = 40 days (< GOP-MIN 42).
**Effective dead zone: ~Jun 8 STOP-HATCH through mid-October.**

---

## 2026 Batch Planning Calendar (from March 8)

| Date | Action | Trigger | Volume |
|---|---|---|---|
| Jun 8, 2026 | 🛑 STOP-HATCH | Cascade dead zone begins (Chaturmas Jul 25, back-calculated) | — |
| Jun 10, 2026 | ✅ STRATEGIC PLACEMENT | Target Sep 12–25 pent-up window (Jun 10 + 58d + 5d hold = Sep 12) | Calculated |
| Sep 9, 2026 | 🔔 ALERT | 7-day alert before Sep 16 placement | — |
| Sep 16, 2026 | 📈 MAXIMUM VOLUME | Diwali (Nov 8) + Wedding Season (Sep 16 + 53d = Nov 8) | Maximum |
| Oct 8, 2026 | 🔔 ALERT | 7-day alert before Oct 15 placement | — |
| Oct 15, 2026 | 📈 MAXIMUM VOLUME | December peak (Oct 15 + 42d = Nov 26 earliest harvest) | Maximum |

---

## MIS Demand Signal Widget — Specification

PanchAngIntel surfaces as an embedded widget on all timing-sensitive MIS screens.
Not a separate module. Not a separate navigation screen.
The MD sees the demand signal in context — wherever timing or volume decisions are made.

---

### Widget Variant A — Full Widget

Appears on: Batch Planning, Hatchery Schedule, Cutting Plant Calendar, Buyer Order Management.

```
┌─────────────────────────────────────────────────────┐
│  📅 DEMAND SIGNAL — Next 60 Days        🔴 DANGER   │
├─────────────────────────────────────────────────────┤
│  TODAY: Aug 13 — Shravan begins                     │
│  Current signal: SEVERE CRASH  −60–80%              │
│                                                     │
│  ── UPCOMING EVENTS ─────────────────────────────   │
│  Aug 17  Shravana Somavara Vrat  🔴 Deepest day     │
│  Sep 11  Shravan ends                               │
│  Sep 14  Ganesh Chaturthi begins  🟢 SPIKE +30–50%  │
│                                                     │
│  ── BATCH PLANNING ──────────────────────────────   │
│  🛑 STOP-HATCH: Already passed (Jun 8)              │
│  ✅ NEXT PLACEMENT: Sep 16                           │
│  📈 TARGET WINDOW: Nov 8 (Diwali)                   │
│                                                     │
│  ── ACTIVE ALERTS ───────────────────────────────   │
│  ⚠️  Do not accept volume orders for Sep–Oct delivery│
└─────────────────────────────────────────────────────┘
```

---

### Widget Variant B — Light Widget

Appears on: Financial Dashboard / MIS Summary, Transport Planning, Farm Placement Dashboard.

```
┌──────────────────────────────────┐
│  DEMAND  🔴 SEVERE CRASH         │
│  Shravan  Aug 13 – Sep 11        │
│  Next spike: Sep 14 (Ganesh)     │
│  → View full signal              │
└──────────────────────────────────┘
```

Status + one-liner + next event + link to full view.
Does not clutter screens where demand is context, not the primary decision.

---

### Eight MIS Screens — Widget Mapping

| Screen | Widget Variant | Primary Decision |
|---|---|---|
| Batch Planning | A — Full | When to place next chick batch |
| Hatchery Schedule | A — Full | Egg setting dates, hatching calendar |
| Cutting Plant Calendar | A — Full | Slaughter scheduling, capacity allocation |
| Buyer Order Management | A — Full | Accept / negotiate volumes with 54 buyers |
| Feed Procurement | A — Full | Order volume + timing (crash = less feed needed) |
| Transport Planning | B — Light | Delivery routing and volume |
| Farm Placement Dashboard | B — Light | Individual shed placement tracking |
| Financial Dashboard / MIS Summary | B — Light | Top-level P&L + operational overview |

---

### Signal Threshold Logic — Four Levels

Signal is **forward-looking**: driven by worst active event in the **next 30-day window**, not just today.
If today is Aug 1 (Chaturmas 🟡) but Shravan starts Aug 13 (🔴), widget shows 🔴.
Planning horizon sees what is coming. Never just current state.

| Signal | Trigger Condition | Examples |
|---|---|---|
| 🔴 RED | Demand deviation < −30% in next 30 days, OR active STOP-HATCH in effect | Shravan, Adhik Maas, Cascade dead zone |
| 🟡 YELLOW | Demand deviation −10% to −30%, OR planning action required within 14 days | Chaturmas entry, Pitru Paksha, Ekadashi delivery caution |
| 🟢 GREEN | Demand deviation > +15%, OR TARGET-HATCH window active | Dussehra, Diwali, post-Shravan pent-up spike |
| 🔵 BLUE | Within ±10% of baseline — normal operating conditions | Most of Jan, Feb, April |

**60-Day Planning Horizon Rule:**
Full widget always shows next 60 days minimum (GOP-MAX = 58 days).
Highlights 2–3 most significant events in that window.
If any 🔴 event falls within 42 days (GOP-MIN), trigger active placement alert on Batch Planning screen.
Light widget shows current signal + next major event only.

---

### Alert Mechanic

**Mode 1 — Scheduled Push Alerts (calendar-driven, WhatsApp via M3):**
- 14 days before any STOP-HATCH date → WhatsApp alert to MD + Ashraf
- 7 days before any TARGET-HATCH date → WhatsApp alert
- Day-of any 🔴 event start → push notification

**Mode 2 — On-Screen Alerts (passive, while using MIS):**
- Red banner at top of any timing-sensitive screen when active 🔴 condition
- Dismissable per session. Returns on next login if condition still active.

**Cross-Module Dependency — PERMANENT:**
PanchAngIntel generates alert content and triggers.
M3 (WhatsApp-to-ERP Agent) delivers WhatsApp messages.
This is a formal dependency: PanchAngIntel → M3.
Must be reflected in M3 module spec (Section 7) when that session runs.
M3 cannot be built as standalone without PanchAngIntel alert interface defined.

---

## Phase 1 vs Phase 2 Scope

### Phase 1 — CURRENT BUILD
- Month/week level demand map — annual rolling 18-month view
- STOP-HATCH / TARGET-HATCH / RESUME-HATCH formula engine
- Cascade Rule automation
- Triple Calendar Stack (Amanta + Hijri + Gregorian) — date computation only
- 7–10 day advance alerts to operations team
- Volume classification per window (Normal / Strategic / Maximum)
- MIS dashboard demand signal widget — Variant A (full) on 5 screens, Variant B (light) on 3 screens
- Four-level signal system (🔴 / 🟡 / 🟢 / 🔵) — forward-looking 30-day worst-event logic
- Scheduled WhatsApp alerts via M3: STOP-HATCH (14-day) + TARGET-HATCH (7-day) + day-of 🔴
- On-screen red banner alert for active 🔴 conditions
- Easter computed via Meeus/Jones/Butcher algorithm (no manual entry)

### Phase 2 — NEXT BUILD
- **Day-wise demand signal calendar** — granular to individual dates (MD request)
- **Week-wise planning view** — intermediate between monthly and daily
- **Mahalaxmi Calendar deep integration** — all day-level events sourced from it
- Adhik Maas severity scoring with multi-year forward projection
- Regional sub-variation (Goa, western Maharashtra border zones)
- Historical demand data overlay (MVPL sales records by date)
- Full day-wise Mahalaxmi Calendar integration — all 7 data layers (L1–L7) ingested and mapped
- Marriage Muhurat windows as Phase 2 demand signal (50+ dates/year; wedding catering offtake)
- Sankashti Chaturthi monthly tracking (13/year)
- Regional sub-variation by district (coastal, urban, rural observance intensity scoring)

---

## Mahalaxmi Calendar — Data Layers

Seven data layers extracted from the Mahalaxmi Calendar annually:

| Layer | Data Type | 2026 Count | Phase |
|---|---|---|---|
| L1 | Named Annual Festivals | ~25–30 | Phase 1 |
| L2 | Ekadashi (bi-monthly) | 26 | Phase 1 schema |
| L3 | Amavasya (monthly) | 13 | Phase 1 schema |
| L4 | Purnima (monthly) | 13 | Phase 1 schema |
| L5 | Sankashti Chaturthi (monthly) | 13 | Phase 2 |
| L6 | Marriage Muhurats | 50+ windows | Phase 2 |
| L7 | Muhurat Blackout Periods | Aug–Oct block | Phase 1 structural |

**2026 counts elevated due to Adhik Maas (extra lunar month):**
- Standard year: 12 Amavasya, 12 Purnima, 24 Ekadashi, 12 Sankashti
- 2026 (Adhik Jyeshtha): 13 Amavasya, 13 Purnima, 26 Ekadashi, 13 Sankashti
- Recurring event counts must be computed fresh per year — never hardcoded.

**Marriage Muhurat as Phase 2 Demand Signal:**
50+ shubha muhurat dates in 2026, concentrated Jan–Jul and Nov–Dec.
Zero muhurats Aug–Oct (Chaturmas + Pitru Paksha).
Wedding season = catering demand = elevated chicken offtake.
Muhurat blackout = zero wedding demand stacking on top of fasting suppression.
No competitor currently tracks this signal.

---

## Three-Cadence Planning Architecture

PanchAngIntel operates at three time-resolution cadences simultaneously:

**Cadence 1 — Annual Layer** (primary batch planning input)
Named festival events (~25–30/year). The batch scheduling backbone.
STOP-HATCH, TARGET-HATCH, RESUME-HATCH formulas operate at this cadence.
Schema: `recurrence_type = 'annual'`

**Cadence 2 — Monthly Recurring Layer** (delivery scheduling)
Amavasya (13/year), Purnima (13/year), Ekadashi (26/year), Sankashti (13/year).
Minor individual dips on each date. Planning value: avoid delivery scheduling on these days.
2026 counts elevated due to Adhik Maas — confirms recurring counts must be computed
per year from `panchang_year_metadata`, not hardcoded.
Schema: `recurrence_type = 'monthly_lunar'`

**Cadence 3 — Weekly Contextual Layer** (Shravan-specific intensifiers only)
Shravana Somavara Vrat: 4 Mondays (Aug 17, 24, 31, Sep 7) — deepest crash days of year.
Mangala Gauri Vrat: 4 Tuesdays (Aug 18, 25, Sep 1, 8) — secondary crash intensifier.
Planning value: alert operations team; no deliveries on these specific days.
Schema: `recurrence_type = 'weekly_seasonal'`

**Schema consequence (see Flag F13):**
`panchang_events` table needs `recurrence_type` ENUM
`('annual', 'monthly_lunar', 'weekly_seasonal')` and `recurrence_reference` field.
A flat event table cannot correctly represent all three cadences.

---

## Regional Name + Event Notes (Permanent Corrections)

**Gudi Padwa = Ugadi (same event, different regional name)**
Karnataka: "Ugadi" | Maharashtra: "Gudi Padwa"
Same Gregorian date. Same demand signal. Different label only.
Schema: `event_name_kannada`, `event_name_marathi`, `event_name_english` columns handle this.
One row per event. Multiple name fields. Do NOT create two separate rows.
(See Flag F22 for JSONB vs normalised local_names schema decision.)

**Naraka Chaturdashi — Karnataka-specific treatment**
North India: Nov 7, observed separately as standalone Diwali day.
Karnataka: Combined with main Diwali on Nov 8 (Karnataka official holiday list confirmed).
Do NOT apply North India Naraka Chaturdashi pattern to Karnataka.
Karnataka Diwali = Nov 8 (national) + Nov 10 (Karnataka Deepavali gazetted holiday).
Model must store `regional_override = TRUE` for this event.

**Mysore Dasara — permanent signal correction for Karnataka**
⚠️ PERMANENT CORRECTION: Navratri/pre-Dussehra (Oct 11–20) is NOT a suppress signal for Karnataka.
Mysore Dasara = world-famous 10-day festival. Oct 11–20 = tourism surge + festivity = net SPIKE +25–40%.
This is the OPPOSITE of the North India Navratri suppress pattern.
North India Navratri suppress applies ONLY to Maharashtra and states north of Karnataka.

**Chaitra Navratri — was missing from demand map (permanent correction)**
⚠️ PERMANENT CORRECTION: Chaitra Navratri (Mar 20–27) was absent from all prior demand maps.
9-day fast directly overlaps with Ugadi window.
Mar 19 = Ugadi spike. Mar 20–27 = fast dip. Both signals must coexist.
Prior map showed "post-Ugadi baseline" immediately from Mar 19 — this was wrong.

---

## MIS Integration Architecture

PanchAngIntel runs as a background service, not a screen.
Every MIS module that involves timing or volume includes a demand signal widget:

```
┌─────────────────────────────────────────────┐
│  DEMAND SIGNAL   🟡 CAUTION                  │
│  Next 30 days: Chaturmas entry Jul 25        │
│  Effective STOP-HATCH: Jun 8                 │
│  Next spike window: Sep 12 (post-Shravan)    │
└─────────────────────────────────────────────┘
```

This widget appears on: Batch Planning, Hatchery Schedule, Cutting Plant Calendar,
Feed Procurement, Transport Planning — anywhere timing decisions are made.
MD sees the whole picture without navigating to a separate module.

---

## Data Requirements
- Mahalaxmi Calendar (primary source — annual, physical + digital if available)
- Panchang computation library or API (for multi-year forward calculation)
- Islamic Hijri calendar API (for Eid/Bakrid lunar sighting-dependent dates)
- Gregorian event database (static — Easter computation, fixed holidays)
- MVPL historical sales data by date (for Phase 2 demand validation)

---

## Open Questions (see Open Flags)
- F07: Is a digital/API version of Mahalaxmi Calendar available, or manual data entry required?
- F08: Day-wise granularity in Phase 2 — which specific Mahalaxmi events to include beyond what's already mapped?
- F09: MIS integration — does the demand signal widget require Poloxy data read access, or is it purely calendar-driven?
- F10: Module vs Demand Signal Engine — formal architectural decision needed for PRD Section 3 update.

---

# ════════════════════════════════════════
# 13. INFRASTRUCTURE & STACK
# ════════════════════════════════════════
**STATUS:** [DEFINED — Decided. Not to be re-litigated.]

## Backend
- API: FastAPI (Python)
- IoT Ingestion: Go microservice (high-throughput, low-latency)
- Task Queue: Celery + Redis

## Database
- Primary: PostgreSQL via self-hosted Supabase
- Time-series: TimescaleDB (IoT sensor data)
- Vector: pgvector (AI embeddings)
- Auth + RLS: Supabase (multi-tenant isolation)
- **MongoDB: REJECTED** — SSPL license + ACID requirements + migration cost

## Infrastructure
- Hosting: Hetzner/DigitalOcean VPS (NOT AWS — cost)
- Containerization: Docker Compose
- Deployment management: Coolify
- CI/CD: [TBD]

## Frontend
- Framework: React + Vite + Tailwind CSS
- Routing: Hash routing
- Build: [TBD]

## AI / ML
- Embeddings: pgvector
- LLM calls: Anthropic API (Claude)
- Orchestration (dev): OpenClaw → Claude Code + Gemini CLI

## IoT Protocol
- Field to gateway: MQTT
- Gateway to cloud: 4G SIM + HTTPS
- Gateway hardware: ESP32 + 4G SIM module

## Design System
- Colors: Navy #1A2F5E | Amber #E8912A | Teal #0D6B6E | Cream #FAF7F2
- Font: [TBD]
- Style: Warm, precise. Islamic geometric influences.
- UX: Glove-friendly touch targets. Offline-first. Multilingual.

---

# ════════════════════════════════════════
# 14. SECURITY & MULTI-TENANCY
# ════════════════════════════════════════
**STATUS:** [PENDING — Session required]

## Multi-Tenant Architecture
- PostgreSQL RLS — each integrator = isolated tenant
- Supabase handles auth + RLS enforcement
- [Detailed spec TBD]

## Data Privacy
[TBD]

## Access Control
[TBD]

---

# ════════════════════════════════════════
# 15. OPEN FLAGS REGISTER
# ════════════════════════════════════════
**STATUS:** [LIVE — Updated by each session]

| ID | Session | Component | Question | Cost/Impact | Status |
|---|---|---|---|---|---|
| F01 | IoT Verification | C02 Flow Meter | 1 meter per shed inlet vs 1 per drinker line (4–6 lines)? | ₹18.8L vs ₹94L | 🔴 UNRESOLVED |
| F02 | IoT Verification | C03 Load Cell | Outdoor feed bin vs indoor hopper placement? | ₹22.6L vs ₹84.6L | 🔴 UNRESOLVED |
| F03 | IoT Verification | C03 Controller | Build ARUSHAI custom ESP32 weighing board? | ₹5.6–7.5 Cr savings + hardware IP | 🟡 NEEDS REVIEW |
| F07 | PanchAngIntel | Calendar Source | Is Mahalaxmi Calendar available as digital/API, or requires manual annual data entry? | Phase 2 build complexity | 🔴 UNRESOLVED |
| F08 | PanchAngIntel | Phase 2 Scope | Which specific Mahalaxmi Calendar day-level events to include beyond current map? Ram Navami, Akshaya Tritiya, Gudi Padwa — full list needed | Phase 2 feature scope | 🟡 NEEDS REVIEW |
| F09 | PanchAngIntel | MIS Integration | Does demand signal widget require Poloxy data read access, or purely calendar-driven (no Poloxy dependency)? | Architecture decision | 🔴 UNRESOLVED |
| F10 | PanchAngIntel | Architecture | Formal decision: PanchAngIntel as standalone M8 module vs platform-level Demand Signal Engine feeding all modules | Affects Section 3 Platform Architecture | 🔴 UNRESOLVED |
| F11 | Knowledge Pipeline | Legal/IP | Copyright: Can ARUSHAI legally ingest + commercialise Mahalaxmi Calendar data? Three paths: (A) Publisher licence, (B) Facts not copyrightable legal opinion, (C) Astronomical independence. Must resolve before commercial go-live. | Legal risk — commercial product | 🔴 UNRESOLVED |
| F12 | Knowledge Pipeline | Architecture | Multi-year forward planning: RAG-only pipeline limited to ~12 months (current year calendar). Need Panchang API (Prokerala/drikpanchang) for next-year + astronomical engine for 2+ years. Three-source architecture required. | Limits planning horizon | 🔴 UNRESOLVED |
| F13 | Knowledge Pipeline | Schema | Tithi vs Gregorian duality: panchang_events table must store both Gregorian equivalents AND underlying tithi definitions (masa, paksha, tithi_day, calendar_system). Schema must be defined before first record is written — retrofitting painful. | Affects all data integrity | 🔴 UNRESOLVED |
| F14 | Knowledge Pipeline | Logic | Adhik Maas pipeline handling: need panchang_year_metadata table + year-level Adhik Maas flag. Planning engine must check this before every calculation and apply severity multiplier + Cascade Rule recalculation. UPDATED (Points 2/3/4): Adhik Maas also increases recurring event counts (Amavasya 12→13, Purnima 12→13, Ekadashi 24→26, Sankashti 12→13). Recurring counts must be computed from year metadata, never hardcoded. See Three-Cadence Architecture. | Affects planning accuracy in ~1 of every 3 years; recurring counts wrong every Adhik year if hardcoded | 🟡 NEEDS REVIEW |
| F15 | Knowledge Pipeline | Schema | Severity scores are ARUSHAI estimates, not validated data. panchang_events table needs both severity_estimate AND severity_validated columns from day 1. Cannot distinguish estimates from MVPL-validated data without this from schema creation. | Data credibility | 🟡 NEEDS REVIEW |
| F16 | Knowledge Pipeline | Validation | LLM hallucination protocol: Claude Vision extraction must be cross-validated by (1) PaddleOCR-VL raw text and (2) astronomical oracle computed date. Define acceptable discrepancy threshold and human review trigger. | Data accuracy risk | 🟡 NEEDS REVIEW |
| F17 | Knowledge Pipeline | Reliability | Pipeline failure modes: define fallback for (1) Mahalaxmi PDF URL change, (2) Claude Vision unavailable, (3) PDF layout redesign, (4) IndicTrans2 wrong transliteration, (5) hash false negative. Mirror PDF in Hetzner volume at each ingestion. | System reliability | 🟡 NEEDS REVIEW |
| F18 | Knowledge Pipeline | Data Source | Panchang API evaluation: evaluate Prokerala Panchang API and drikpanchang API as complement to Mahalaxmi Calendar for multi-year computation. These solve Gap 2 (forward planning horizon). Decision needed before Phase 1 architecture is finalised. | Architecture dependency | 🔴 UNRESOLVED |
| F19 | PanchAngIntel | Schema | Regional sub-variation within Karnataka: coastal (Mangalore/Udupi), North Karnataka, Bangalore urban, rural (MVPL primary market) have different observance intensities. panchang_events table needs region_modifier columns (coastal, urban, rural) from schema creation — even if all NULL initially. Phase 2 to populate from MVPL sales data. | Data model extensibility | 🟢 PHASE 2 — Schema now, data later |
| F20 | PanchAngIntel | Calendar Data | Akshaya Tritiya Karnataka date: nationally Apr 19 but some South India regional calendars show Apr 20. Must verify from Mahalaxmi Kannada Calendar 2026 before finalising Karnataka demand map entry. Cannot use national date without Karnataka-specific confirmation. | Demand map accuracy | 🔴 UNRESOLVED |
| F21 | PanchAngIntel | Schema | Marriage Muhurat Phase 1 schema decision: should muhurat blackout periods (Aug–Oct) be stored as a separate event type in panchang_events, or as a metadata field on existing events? Decide before schema is written. | Schema design | 🟡 NEEDS REVIEW |
| F22 | PanchAngIntel | Schema | Regional name schema design: Gudi Padwa (Maharashtra) = Ugadi (Karnataka). Should regional names be stored as JSONB `local_names` field on the event row, or as a normalised `event_regional_names` table? JSONB = simpler; normalised = queryable. Decide before schema creation. | Schema design | 🟡 NEEDS REVIEW |
| F23 | PanchAngIntel | Calendar Data | Swarna Gowri Vrata 2026 date conflict: smartpuja.com shows Sep 13; Karnataka official holiday list shows Sep 14. One-day conflict. Must verify from Mahalaxmi Kannada Calendar 2026. Date matters because it determines exact Ganesh Chaturthi relationship (Ganesh Chaturthi = day after Swarna Gowri). | Demand map accuracy | 🔴 UNRESOLVED |
| F24 | PanchAngIntel | Schema | Good Friday schema treatment: is Good Friday a standalone event row with region_modifier_coastal applied (recommended), or a modifier field on the Easter row? Single-day coastal dip Apr 3, 2026. Recommended: standalone row, region_primary = ['Karnataka_Coastal'], severity_estimate = −0.08. Decide before schema creation — cannot retrofit cleanly. | Schema design | 🟡 NEEDS REVIEW |

---

# ════════════════════════════════════════
# 16. SESSION CONTRIBUTION LOG
# ════════════════════════════════════════

| Date | Session Name | Sections Updated | Delta File | Applied |
|---|---|---|---|---|
| Mar 2026 | MVPL Strategy & Partnership | Sections 1, 2, 3 | Context Brief deltas v5.1–5.6 | ✅ |
| Mar 2026 | IoT Hardware Price Verification | Section 4 (C01–C03) | ARUSHAI_PRD_DELTA_IoT_v1.md | 🔲 Pending |
| Mar 2026 | Panchang Intel Brainstorm | Section 12 (partial) | ARUSHAI_PRD_DELTA_Panchang_v1.md | 🔲 Pending |
| Mar 8, 2026 | PanchAngIntel — MVPL MD Meeting Debrief | Sections 2, 12, 15, 16 | ARUSHAI_PRD_DELTA_PanchAngIntel_MeetingDebrief_v1.md | 🔲 Pending |
| Mar 8, 2026 | PanchAngIntel — Point 1 Deep Dive (Panchang Source + Knowledge Pipeline) | Sections 3B, 15, 16 | ARUSHAI_PRD_DELTA_PanchAngIntel_Point1_KnowledgePipeline_v1.md | 🔲 Pending |
| Mar 8, 2026 | PanchAngIntel — Points 2, 3, 4 (Calendar Content + Day-Wise Cadence + Missing Festivals) | Section 12 (demand map corrected, 3 new subsections), Section 15 (F14 updated, F20–F23 added), Section 16 | ARUSHAI_PRD_DELTA_PanchAngIntel_Points234_v2.md | 🔲 Pending |
| Mar 8, 2026 | PanchAngIntel — Points 5 + 6 (Gregorian Scope + MIS Widget Design) | Section 12 (Verified Dates, Triple Calendar Stack, Widget Spec + Alert Mechanic subsections, Phase 1 scope updated), Section 15 (F24), Section 16 | ARUSHAI_PRD_DELTA_PanchAngIntel_Points56_v1.md | 🔲 Pending |
| — | Feed Mill M1 Session | Section 5 | — | 🔲 Not started |
| — | Field App M2 Session | Section 6 | — | 🔲 Not started |
| — | WhatsApp Agent M3 Session | Section 7 | — | 🔲 Not started |
| — | Transport M4 Session | Section 8 | — | 🔲 Not started |
| — | Layer Intel M5 Session | Section 9 | — | 🔲 Not started |
| — | HATCHWATCH M6 Session | Section 10 | — | 🔲 Not started |
| — | BROODWATCH M7 Session | Section 11 | — | 🔲 Not started |
| — | Infrastructure Deep Dive | Sections 13, 14 | — | 🔲 Not started |

---

*ARUSHAI Systems Private Limited | Confidential | arushai-hq/brain*
*This document is the single source of truth for the ARUSHAI product build.*
*Last updated: March 8, 2026 | Version: 1.4*
