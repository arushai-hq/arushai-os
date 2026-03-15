> Migrated from arushai-hq/brain on 2026-03-15. This content is archived — it reflects an earlier business direction. Preserved for historical reference.

# ARUSHAI PRD DELTA — Sessions March 5 → March 10, 2026
**Target file:** ARUSHAI_Context_Brief.md (v5.5 → v5.6)
**Source sessions:** IoT BOM Verification, PanchAngIntel Audit, MVPL MD Meeting Debrief, Phased ROI Design
**Apply using:** CC_PROMPT_ApplyDelta_ContextBrief.md

---

## DELTA 1 — Founder Current Status Update

### FIND:
```
| Current Status | 3-4 day thinking period on MVPL Technology Partnership offer. MD also thinking and will propose equity structure. Next conversation pending. |
```
### REPLACE WITH:
```
| Current Status | Technology co-founder role accepted in principle. ARUSHAI × MVPL partnership active. IoT BOM verified across A–E series (₹4.71 Cr model, E3 version). MD meeting held March 2026 — phased investment model being prepared. Next step: deliver Phased ROI Excel + one-page letter to Toufiq. |
```
### REASON:
Status was "thinking period" — now well past that. Partnership is active and IoT work is done.

---

## DELTA 2 — Tech Stack Correction (Critical)

### FIND:
```
| Cloud | AWS — VPC, Kubernetes, Secrets Manager, CloudFront, BullMQ |
| Frontend | React.js (web) + React Native (mobile, offline-first) |
| Backend | Node.js / Express REST APIs |
| Database | MongoDB — MERN stack |
| AI / LLM | Vendor-agnostic LLM router |
| Auth | Auth0 — SSO, MFA, SAML 2.0 |
| IoT | OPC-UA for PLC · Temperature/humidity sensors · Automated weighing · Feed silo sensors |
| Build Method | Claude Code + AI agents. Human QA mandatory. |
```
### REPLACE WITH:
```
| Cloud | DigitalOcean Mumbai (primary) + Vultr Bangalore (DR/warm standby) + Wasabi (offsite backup). NOT AWS — rejected for cost at current scale. |
| Frontend | React + Vite + Tailwind CSS (web). Mobile: React Native (planned). |
| Backend | FastAPI (Python) — APIs + AI orchestration. Go — IoT data ingestion (high throughput). |
| Database | PostgreSQL via self-hosted Supabase + TimescaleDB (IoT time-series) + pgvector (AI embeddings). MongoDB REJECTED — SSPL license + ACID requirements. |
| AI / LLM | OpenClaw orchestrator (MiniMax M2.5 via OpenRouter). Claude Code + Gemini CLI workers via tmux. Telegram interface for Irfan. Edge-first: YOLO on RPi4, Coral TPU. External API only for LLM narratives. |
| Auth | Supabase Auth (built-in). Auth0 deferred. |
| Security | Cloudflare Pro (WAF + CDN). Tailscale VPN. Let's Encrypt SSL. |
| IoT Hardware | SHT31-DIS-F2.5KS PTFE sensor (sheds). UPVC turbine DN25 flow meter. Rudrra RSL-310 load cell + ESP32 controller. Vajruino RS485 IoT gateway 4G. CP Plus 4MP PoE IP67 cameras. Teltonika FMC130 (fleet). OPC-UA for PLC integration (feed mill). |
| IoT Rejected | HX711 load cell controller — REJECTED (noise, no RS485). SIM800L — REJECTED (2G sunset, no GPS). |
| Infra Management | Docker Compose + Coolify (self-hosted). NOT Kubernetes at current scale. |
| Build Method | Claude Code + AI agents. Human QA mandatory. AI orchestration: OpenClaw → Claude Code + Gemini CLI workers. |
| USD/INR Rate | ₹92 (active rate for all hardware BOM calculations). |
```
### REASON:
Entire tech stack was re-decided across multiple sessions. Context brief still shows rejected stack (AWS, MongoDB, Node.js). This is the most critical correction.

---

## DELTA 3 — MVPL Scale Correction

### FIND:
```
| Scale | 470+ active contract farms, 214 live flocks, feed mill, hatchery, processing plant, fleet |
```
### REPLACE WITH:
```
| Scale | 600 farmers, 105 staff, 54 buyers, 30 vendors, 470+ farms, 940 broiler sheds, 40 fleet vehicles, 2 hatcheries, 1 soya mill, 1 feed mill. Expansion: breeder farm, layer farm, cutting plant, exports. |
```
### REASON:
940 shed count is the verified operational number used in all IoT BOM calculations. Previous entry was incomplete.

---

## DELTA 4 — MVPL Key Contacts Update

### FIND:
```
| Leadership | MD (operations + customer relations) + Brother/Co-founder (sales) — neither from technical background |
```
### REPLACE WITH:
```
| Leadership | MD: Toufiq Maner (Muslim, deep market knowledge, rejected SAP, wants home-grown AI). Internal tech champion: Ashraf Tahsildar (ARUSHAI's primary contact for technical integration). Brother/Co-founder: sales. Neither MD nor brother from technical background. |
```
### REASON:
Toufiq and Ashraf names confirmed and critical for all future sessions.

---

## DELTA 5 — Module List Update (Add M8)

### FIND:
```
| M7 | BROODWATCH — Brooding Precision Intelligence | 0–14 day brooding control for breeder pullets. Continuous 3-zone IoT temperature monitoring, automated Day-7 and Day-14 body weight CV%, 6-hour crop fill alert, water intake trend detection. Predicts 20-week reproductive performance from Day-14 uniformity score. | Future |
```
### REPLACE WITH:
```
| M7 | BROODWATCH — Brooding Precision Intelligence | 0–14 day brooding control for breeder pullets. Continuous 3-zone IoT temperature monitoring, automated Day-7 and Day-14 body weight CV%, 6-hour crop fill alert, water intake trend detection. Predicts 20-week reproductive performance from Day-14 uniformity score. | Phase 2 |
| M8 | PanchAngIntel — Panchang Demand Planning | Karnataka Amanta Panchang calendar intelligence for backward-planning hatch dates. Identifies demand crash periods (Shravan, Adhik Maas, Chaturmas) and suppression windows. Automates STOP-HATCH, TARGET-HATCH, RESUME-HATCH calculations. Cross-market: Amanta states (KA/MH/GJ/AP) + Purnimanta (North India). 2026 key dates: Shravan Aug 13–Sep 11, Chaturmas Jul 25–Nov 20, Adhik Maas May 17–Jun 15. | In Design |
```
### REASON:
M8 PanchAngIntel designed and partially built. PPT and Word document generated and audit-corrected (v1.1).

---

## DELTA 6 — Partnership Structure (Replace Proposed with Confirmed)

### FIND:
```
### Proposed Partnership Structure (ARUSHAI position)
- MVPL receives 15-20% equity in ARUSHAI (founding anchor client + operational laboratory)
- Irfan receives 3-5% equity in MVPL (technology co-founder, formalised April 1)
- ARUSHAI retains full IP ownership, licenses platform to MVPL
- MVPL pays ARUSHAI retainer covering build costs during development phase
- ARUSHAI can serve other clients — MVPL gets first-mover advantage + preferential pricing
```
### REPLACE WITH:
```
### Confirmed Partnership Structure (ARUSHAI non-negotiables — communicated to MD)
- IP stays with Arushai Systems Private Limited. MVPL gets exclusive perpetual license only.
- Monthly build cost recovery ₹1–1.5L during development (non-negotiable).
- Equity % agreed and written on bond paper before work begins.
- Profit share: max 25% of ARUSHAI profits from MVPL/poultry products only, after all expenses. Non-MVPL products excluded.
- ARUSHAI identity: NOT disclosed to MD as separate entity yet. Presented as Irfan's technology vehicle.
- ARUSHAI can serve other clients. MVPL gets first-mover advantage + preferential pricing.
- IPO valuation thesis: Without ARUSHAI ~₹300 Cr (0.64× revenue). With ARUSHAI ~₹1,250 Cr (2.5× revenue). ARUSHAI creates ₹950 Cr uplift — equity justification.

### MD Meeting Outcome (March 2026)
- Investment Model E3 (₹4.71 Cr total) presented. MD positive but concerned at total figure.
- MD requested: (1) per-shed/per-item pricing breakdown, (2) month-by-month phased cashflow from Month 1.
- MD background: seasonal loss cycles — cannot evaluate on turnover alone. Previous partnerships caused significant losses still being repaid.
- MD instruction: "Don't keep high expectations." Interpreted as: needs to feel in control, not rushed into commitment.
- Equity: MD has not proposed a number. ARUSHAI position: leave open, let MD propose after seeing phased model.
- WheelsEye: MD confirmed fleet already using WheelsEye (₹11,000/vehicle/year). M4 rearchitected to API layer only.
- Factory IoT: Pune company already installed sensors for water/boiler. Integration play confirmed.
```
### REASON:
Partnership has moved well beyond "proposed" stage. MD meeting outcome materially changes posture.

---

## DELTA 7 — Add IoT BOM Verified Decisions (New Section Before Section 14)

### FIND:
```
## 14. Locked Decisions
```
### REPLACE WITH:
```
## 13B. IoT BOM — Verified Hardware (MVPL 940 Sheds)

**Reference files:** ARUSHAI_MVPL_Investment_Model_E3.xlsx | ARUSHAI_MVPL_IoT_Verification_Register.docx
**Verified:** March 2026 | Indian supplier prices | SKU + source confirmed per component

### A-Series — Per Shed (×940 sheds + ×1,000 install target)
| Component | Verified ₹ | Install ₹ | Notes |
|---|---|---|---|
| SHT31-DIS-F2.5KS PTFE T/RH Sensor | 700 | 150 | PTFE membrane for poultry environment |
| UPVC Turbine DN25 Flow Meter | 2,000 | 300 | Water flow per shed |
| Rudrra RSL-310 Load Cell + ESP32 | 9,000 | 500 | Feed weight. HX711 rejected. |
| Vajruino RS485 IoT Gateway 4G | 4,500 | 500 | Edge gateway per shed |
| CP Plus 4MP PoE IP67 Camera | 3,000 | 500 | Shed surveillance |
| Wiring + PoE switch + UPS | 7,110 | 2,000 | Per shed infrastructure |
| **Per-shed total** | **₹26,310** | **₹3,950** | |

### B-Series — Hatchery (×2)
| Component | Verified ₹ |
|---|---|
| RS485 Industrial Multi-zone T/RH Sensor | 3,000 |
| Egg Counter Camera (RPi4 + USB cam) | 6,000 |
| Chick Quality CV Camera (Coral TPU + RPi4) | 12,800 |
| IoT Gateway + HEN Server (incremental) | 3,700 |
| **Per-hatchery total** | **₹25,500** |

### D-Series — Fleet (×40 vehicles — WheelsEye already active, hardware = ₹0)
M4 rearchitected: ARUSHAI builds AI intelligence layer on WheelsEye API only.
Fleet hardware line removed from BOM. Saving: ₹12.56L hardware + ₹3.36L annual connectivity.

### E-Series — Annual Recurring
| Item | Annual ₹ |
|---|---|
| Shed SIMs (₹50/mo bulk M2M) | 6,00,000 |
| Fleet SIMs | ₹0 (WheelsEye covers) |
| Cloud Infrastructure (DO Mumbai primary) | 15,10,344 |
| Maintenance Reserve | 10,15,700 |

### 24-Month Investment Summary (E3 — WheelsEye adjusted)
- IoT Hardware total: ~₹2.80 Cr (one-time)
- Annual connectivity: ₹23.17L
- Software build: ₹52.50L
- 24-month total with 15% contingency: ~₹3.60 Cr (WheelsEye-adjusted from ₹4.71 Cr)

### Open Hardware Flags
| ID | Question | Cost Swing | Status |
|---|---|---|---|
| F01 | A02 Flow Meter: 1/shed inlet vs 1/drinker line? | ₹18.8L vs ₹94L | 🔴 UNRESOLVED |
| F02 | A03 Load Cell: outdoor bin vs indoor hopper? | ₹22.6L vs ₹84.6L | 🔴 UNRESOLVED |
| F03 | A03: Build custom ARUSHAI ESP32 controller? | ₹5.6–7.5 Cr savings | 🟡 IRFAN DECIDES |
| F04 | A04: Consolidate SIU into gateway board? | Design decision | 🟡 IRFAN DECIDES |
| F05 | A05: 1 vs 2 cameras per shed? | Cost impact pending | 🟡 IRFAN DECIDES |
| B-F01 | Hatchery egg counting: camera vs mechanical? | Architecture decision | 🔴 UNRESOLVED |
| E-F01 | Hatchery 4G backup SIM: LAN or active? | ₹0 vs ₹24K/yr | 🔴 UNRESOLVED |

## 14. Locked Decisions
```
### REASON:
Entire IoT BOM verification series complete. This is foundational reference data for all future MVPL sessions.

---

## DELTA 8 — Add Phased Investment Structure (New Section)

### FIND:
```
## 15. Open Questions
```
### REPLACE WITH:
```
## 14B. MVPL Phased Investment Structure

**Purpose:** Present to Toufiq as month-by-month cashflow with value return — not total lump sum.
**Reference file:** ARUSHAI_MVPL_Phased_ROI_Model.xlsx (CC-generated, dynamic, MD-adjustable)

### Four-Phase Plan

| Phase | Months | Scope | Monthly Retainer | Hardware |
|---|---|---|---|---|
| Phase 1 — Foundation | M1–M3 | M2 Field App + M3 WhatsApp Agent | ₹50,000 | None |
| Phase 2 — Intelligence | M4–M6 | M1 Feed Mill + M7 Broodwatch + Factory IoT integration | ₹75,000 | None |
| Phase 3 — IoT Pilot | M7–M12 | 100-shed IoT pilot + M4 Fleet (WheelsEye layer) + M6 Hatchwatch | ₹1,00,000 | ₹33–34L |
| Phase 4 — Full Rollout | M13–M24 | 940 sheds full IoT + M8 PanchAngIntel + IPO data layer | ₹1,50,000 | ~₹3.10 Cr |

Note: Timeline uses Month 1/2/3 (not calendar dates) — start date TBD pending MD go-ahead.

### Key Reframe for MD
- ₹4.71 Cr is the ceiling at full deployment — not Day 1 commitment.
- Phased 24-month spend: ~₹3.60 Cr (WheelsEye-adjusted).
- Per shed monthly tech cost at full deployment: ₹295/month.
- Break-even: cumulative value exceeds cumulative cost approximately Month 9–10 (conservative scenario).
- One bad FCR day costs more per shed than the technology costs in a month.

### Integration Positioning (MD-facing reframe)
ARUSHAI connects what MVPL already has and makes it intelligent:
- Poloxy (existing ERP) + WheelsEye (existing fleet GPS) + Pune IoT (existing factory sensors) + new ARUSHAI shed sensors → unified intelligence layer → one dashboard for MD.
Message: "We are not replacing what you have. We are making it 10 times smarter."

### Pending Action Items (Ashraf)
- A01: Get WheelsEye API access token from account settings — unlocks M4 at ₹0 hardware cost
- A02: Pune factory IoT — how does it send alerts? (email / SMS / webhook) — determines Phase 2 integration approach

## 15. Open Questions
```
### REASON:
Phased investment structure is now the primary commercial document for MVPL. Must be in context brief.

---

## DELTA 9 — Update Open Questions Section

### FIND:
```
- [ ] MVPL MD equity proposal — pending (3-4 day thinking period)
- [ ] ARUSHAI legal entity — India or Qatar? Must resolve before April 1
- [ ] IP ownership agreement — lawyer needed before partnership formalised
- [ ] PLC brand and model at MVPL feed mill
- [ ] Lab results — digital or physical register?
- [ ] On-ground Karnataka person — not yet identified
- [ ] Logo designer — Fiverr Arabic calligraphy not yet initiated
- [ ] Login wireframe — Claude Code to generate from l1-login.md
- [ ] Python context sync script — Product Blueprint session
- [ ] VPS wireframe hosting — Nginx configuration
- [ ] Model comparison — Claude Code vs Gemini CLI on login screen
- [ ] Family conversation about partnership intensity — before MD conversation
- [ ] MVPL hatchery details — batch size, current quality tracking method, parent flock count
- [ ] MVPL breeder farm details — number of breeder sheds, current brooding monitoring method, pullet flock size
- [ ] What equity % is MD thinking? Must be defined before counter-proposal sent
- [ ] Does MD have a lawyer/CS for bond paper? — need to know if ARUSHAI brings own
- [ ] After Poloxy demo March 6 — what was MD reaction? Sign or still evaluating?
```
### REPLACE WITH:
```
- [ ] MVPL equity % — MD has not proposed a number. Awaiting Phased ROI Model review.
- [ ] ARUSHAI legal entity — India or Qatar? Must resolve before April 1. CRITICAL.
- [ ] IP ownership agreement — lawyer needed before partnership formalised
- [ ] PLC brand and model at MVPL feed mill — ask Ashraf
- [ ] Lab results — digital or physical register? — ask Ashraf
- [ ] On-ground Karnataka person — not yet identified
- [ ] Logo designer — Fiverr Arabic calligraphy not yet initiated
- [ ] Login wireframe — Claude Code to generate from l1-login.md
- [ ] Model comparison — Claude Code vs Gemini CLI on login screen
- [ ] Family conversation about partnership intensity — status unknown
- [ ] Poloxy demo outcome (March 6) — what was MD reaction?
- [ ] WheelsEye API access token — Ashraf to retrieve from account settings
- [ ] Pune factory IoT alert protocol — Ashraf to confirm (email/SMS/webhook)
- [ ] Phased ROI Model — update Block B inputs with MVPL actuals (940 sheds, ₹100 Cr revenue etc.) before sending to Toufiq
- [ ] One-page letter to Toufiq — draft pending (next session)
- [ ] Sheet 6 "Notes for MD" — CC prompt ready, add to Excel before sending
- [ ] TradeOS TRADEOS_CONTEXT.md — needs to be created in repo for context recovery
```
### REASON:
Many questions from v5.5 are now resolved or superseded. New open items from March sessions added.

---

## DELTA 10 — Update Immediate Action Queue

### FIND:
```
[URGENT — This Week]
- [ ] Draft and send counter-proposal email to MD
      (IP licensing + retainer + equity % now + lawyer for bond)
- [ ] Observe Poloxy demo outcome March 6 — assess MD reaction
- [ ] Plant "7-day farm prediction" question with MD before/after Poloxy demo
```
### REPLACE WITH:
```
[URGENT — This Week]
- [ ] Finalise ARUSHAI_MVPL_Phased_ROI_Model.xlsx — update Block B with MVPL actuals
- [ ] Add Sheet 6 "Notes for MD" to Excel (CC prompt: CC_PROMPT_Sheet6_NotesForMD.md)
- [ ] Draft one-page letter to Toufiq (ARUSHAI + Claude next session)
- [ ] Contact Ashraf: WheelsEye API token + Pune IoT alert protocol
- [ ] Resolve ARUSHAI legal entity — India or Qatar — before April 1
```
### REASON:
Action queue was pointing to March 6 items now long past. Replaced with current active actions.

---

## VERSION UPDATE

### FIND:
```
**Version 5.5 | March 5, 2026 | Living Document**
```
### REPLACE WITH:
```
**Version 5.6 | March 10, 2026 | Living Document**
Last session: MVPL MD Meeting Debrief + Phased ROI Design
```

---

*Delta generated by: Claude Sonnet 4.6 | ARUSHAI Project Session | March 10, 2026*
*Arushai Systems Private Limited | Confidential*
