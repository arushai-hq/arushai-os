> Migrated from arushai-hq/brain on 2026-03-15. This content is archived — it reflects an earlier business direction. Preserved for historical reference.

# ARUSHAI Context Brief — Delta v5.2 → v5.3
**Name Correction + Website Tracking | March 2026**
**Trigger:** Company name clarification + website content tracking update

---

## ⚠️ CRITICAL CORRECTION — Company Name

The correct full legal name is:

```
✅ CORRECT : Arushai Systems Private Limited
❌ WRONG   : ARUSHAI Enterprise Solutions
❌ WRONG   : Arushai Solutions Private Limited
❌ WRONG   : ARUSHAI Enterprise Solutions Private Limited
```

Apply this correction everywhere in the context brief.

---

## DELTA 1 — Section 2: Company Foundation Table — Name Correction

**WHERE:** Section 2, Company Foundation table, Full Name row

**CODE PROMPT:**
```
FILE: ARUSHAI_Context_Brief.md
TASK: Fix the company name in the Company Foundation table in Section 2.

Find:
| Full Name | ARUSHAI Enterprise Solutions |

Replace with:
| Full Name | Arushai Systems Private Limited |
```

---

## DELTA 2 — File Header — Name Correction

**WHERE:** File footer/signature line at the bottom of the document

**CODE PROMPT:**
```
FILE: ARUSHAI_Context_Brief.md
TASK: Fix all instances of wrong company name in the document footer.

Find:
*ARUSHAI Enterprise Solutions · Context Brief v5.2

Replace with:
*Arushai Systems Private Limited · Context Brief v5.3
```

---

## DELTA 3 — Section 19: Documents Index — Add Website Entry

**WHAT:** Track the ARUSHAI website as a live asset in the documents index.

**WHERE:** Section 19 Documents Index table — append new row

**CODE PROMPT:**
```
FILE: ARUSHAI_Context_Brief.md
TASK: Add one row to the Documents Index table in Section 19.

Find the last row in the table:
| FMI Pricing Proposal v1 | OneDrive: 01 — Products → MVPL → Commercial |

Add immediately after:
| arushai.com Website | localhost:3000 (dev) → arushai.com (prod). React+Vite+Tailwind. Hash routing. Agent Prompt v2 applied. |
| Website Agent Prompt v2 | updates/archive/ARUSHAI_Website_Agent_Prompt_v2.md |
```

---

## DELTA 4 — Add New Section: Website & Digital Presence Log

**WHAT:** New standing section to track website state, what has been built, 
what is pending. Living record updated after every website session.

**WHERE:** Add as new Section 20, after Documents Index

**CODE PROMPT:**
```
FILE: ARUSHAI_Context_Brief.md
TASK: Add a new Section 20 after Section 19 (Documents Index).

Find the document footer line:
*Arushai Systems Private Limited · Context Brief v5.3

Insert this entire block immediately before it:

---

## 20. Website & Digital Presence — State Log

### arushai.com
| Field | Detail |
|---|---|
| Status | In development — localhost:3000 |
| Stack | React + Vite + Tailwind CSS |
| Routing | Hash-based (#/) |
| Hosting (target) | Hostinger VPS + Nginx |
| Domain | arushai.com (owned) |
| Last Agent Prompt | Website Agent Prompt v2 — March 2026 |

### Pages & Status
| Page | Route | Content Status |
|---|---|---|
| Home | #/ | v2 prompt applied — hero, positioning strip, stats, industry verticals, ARUSHAI Score, CTA |
| About | #/about | v2 prompt applied — story, values, founder profile |
| Services | #/services | v2 prompt applied — 6 services added |
| Portfolio | #/portfolio | v2 prompt applied — 3 real items added |
| Blog | #/blog | v2 prompt applied — 2 real posts added |
| Contact | #/contact | v2 prompt applied — 3 engagement cards, partner/client/careers |
| Testimonials | #/testimonials | v2 prompt applied — honest placeholder |
| Careers | #/careers | v2 prompt applied — domain expert call-out |

### SEO — Applied
- [x] Title + meta description — multi-industry, India + global
- [x] Keywords — agri, healthcare, logistics, manufacturing, retail, finance, construction
- [x] Open Graph tags
- [x] Twitter Card tags
- [x] JSON-LD structured data (Organization schema)
- [x] robots.txt
- [x] sitemap.xml
- [x] Canonical URL

### Company Name — Must Show As
```
Arushai Systems Private Limited
```
Never: "ARUSHAI Enterprise Solutions" or "Arushai Solutions Private Limited"

### Positioning Applied
All 4 value propositions shown simultaneously on homepage:
1. AI that solves real operational problems — any industry
2. Enterprise intelligence at SMB price
3. Any industry, any domain (8 verticals shown)
4. We automate your manual checklists

### Industry Verticals on Website
| Vertical | Status Badge |
|---|---|
| Agri-Business & Poultry | ACTIVE — IN DEVELOPMENT |
| Healthcare & Hospitals | ROADMAP 2026 |
| Logistics & Supply Chain | ROADMAP 2026 |
| Manufacturing & Factory Ops | ROADMAP 2026 |
| Retail & E-Commerce | ROADMAP 2027 |
| Finance & Accounting | ROADMAP 2027 |
| Construction & Real Estate | ROADMAP 2027 |
| Consulting & Cyber Security | ROADMAP 2027 |

### ARUSHAI Score — On Website
Left panel: Client AI Readiness Score widget (5-question quiz → contact form)
Right panel: ARUSHAI live metrics (1 partner, 4 modules, 8 verticals, March 2025 founded, 16-day MVP)

### Social Links (Placeholders — update when live)
- LinkedIn: linkedin.com/company/arushai
- GitHub: github.com/arushai-hq
- Twitter/X: twitter.com/arushai_ai

### Next Website Tasks (Queue)
- [ ] Deploy to Hostinger VPS behind Nginx
- [ ] Replace placeholder social links with real handles
- [ ] Build interactive AI Readiness Score quiz (5 questions → score → contact)
- [ ] Add real logo once Fiverr Arabic calligraphy designer completes
- [ ] Add real founder photo to About page
- [ ] Write 2 more blog posts — logistics AI + manufacturing AI
- [ ] Google Search Console setup after deployment
- [ ] Google Analytics / privacy-respecting analytics setup
```

---

## Summary — v5.2 → v5.3

| # | Section | Type | What |
|---|---|---|---|
| 1 | §2 Company Foundation | FIX | Name corrected to Arushai Systems Private Limited |
| 2 | File footer | FIX | Version + name updated |
| 3 | §19 Documents Index | ADD | Website + Agent Prompt v2 entries |
| 4 | §20 NEW | ADD | Full website state log — pages, SEO, positioning, queue |

---

## Global Name Rule (Permanent)

Every time the context brief is updated, verify:
```
✅ Arushai Systems Private Limited  ← always this
❌ ARUSHAI Enterprise Solutions      ← never this
❌ Arushai Solutions Private Limited ← never this
```

---

*Arushai Systems Private Limited · Context Brief Delta v5.2→v5.3 · March 2026*
*Amanah · Ihsan · Khidmah · Islah*
