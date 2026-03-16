# ARUSHAI Compliance Readiness Roadmap

**Version:** 1.0.0
**Date:** 2026-03-16
**Status:** Planning document — reviewed annually
**Owner:** Founder / CEO

---

## Purpose

This roadmap maps ARUSHAI's path from startup engineering practices to enterprise-grade compliance and eventual public company readiness. It is designed to be built incrementally — each phase adds to the previous one, nothing is thrown away.

The key insight: companies that build audit trails and documentation discipline from day one have the easiest certification and IPO processes. ARUSHAI's existing practices (living documents, ADRs, session debriefs, git-based change management, structured logging) already form the foundation.

---

## Current State Assessment

### What ARUSHAI Already Has (Strengths)

- 29 engineering/operational/security standards in OSD
- Git-based change management with full commit history
- Living documents per product with session logs
- Architecture Decision Records (ADRs)
- Blameless post-mortem process
- Structured JSON logging
- Secrets management (gitignored, templated)
- Code review via code-reviewer agent
- Product lifecycle pipeline with PRR gate
- Access control awareness (OSD Section 7)

### What ARUSHAI Needs to Add (Gaps by Phase)

## Phase 1: Foundation (Current — Q1-Q2 2026)

**Goal:** Engineering security practices embedded in all products

Deliverables:
- [ ] OSD v1.9.0 security standards implemented (audit trail, encryption, MFA, access register, data inventory, SDL)
- [ ] Access control register created and populated (docs/security/access-control-register.md)
- [ ] MFA verified on all infrastructure accounts
- [ ] Data inventory created for HULMI (first product with personal data)
- [ ] Audit logging implemented in HULMI from Phase 6 build prompts

Status: IN PROGRESS

## Phase 2: Pre-Certification Readiness (Q3-Q4 2026)

**Goal:** Prepare for ISO 27001 gap analysis

Deliverables:
- [ ] Information Security Management System (ISMS) scope defined
- [ ] Risk assessment completed (what are ARUSHAI's information security risks?)
- [ ] Security policies documented:
  - Information Security Policy
  - Access Control Policy
  - Data Classification Policy
  - Incident Response Policy (exists in OSD — formalize)
  - Business Continuity Plan
  - Acceptable Use Policy
- [ ] Vendor security assessment for all third-party services
- [ ] Security awareness training documented (even for solo founder)
- [ ] Internal audit checklist created
- [ ] Gap analysis against ISO 27001 Annex A controls completed

Dependencies: At least one product handling real user data in production

## Phase 3: First Certification (2027)

**Goal:** Achieve ISO 27001 certification

Deliverables:
- [ ] ISMS fully operational
- [ ] Stage 1 audit (documentation review) — passed
- [ ] Stage 2 audit (implementation review) — passed
- [ ] ISO 27001 certificate obtained
- [ ] Surveillance audit schedule established (annual)

Estimated cost: $8,000-30,000 (varies by scope and auditor)
Estimated timeline: 12-16 weeks from gap analysis to certification

## Phase 4: Multi-Framework Compliance (2027-2028)

**Goal:** Add SOC 2 Type II alongside ISO 27001

Deliverables:
- [ ] SOC 2 Trust Services Criteria mapped to existing ISO 27001 controls
- [ ] Additional SOC 2-specific controls implemented
- [ ] SOC 2 Type I report obtained
- [ ] SOC 2 Type II report obtained (requires 6+ months of operating evidence)
- [ ] GDPR compliance verified (if serving EU users)
- [ ] Qatar PDPL compliance verified

Note: 60-70% overlap between ISO 27001 and SOC 2 controls — design once, certify twice.

## Phase 5: IPO Foundation (2028-2029+)

**Goal:** Build governance infrastructure for eventual public listing

Deliverables:
- [ ] Financial controls framework (SOX-ready):
  - Documented close process
  - Internal controls over financial reporting (ICFR)
  - Segregation of duties (as team grows)
- [ ] Board governance:
  - Advisory board established
  - Independent directors identified
  - Audit committee, compensation committee planned
- [ ] Equity management:
  - Cap table formalized
  - Stock option plan documented
  - Vesting schedules tracked
- [ ] Financial reporting:
  - Monthly close process
  - Quarterly financial summaries
  - Annual audited financial statements (PCAOB-aligned auditor)
- [ ] Regulatory tracking:
  - Applicable jurisdictions identified (Qatar, India, US, EU)
  - Per-jurisdiction compliance requirements documented

Timeline: IPO planning should start 18-24 months before intended listing

---

## Compliance Framework Mapping

Shows how a single control satisfies multiple frameworks:

| ARUSHAI Control | ISO 27001 | SOC 2 | GDPR | SOX |
|---|---|---|---|---|
| Audit trail (OSD 4.11.1) | A.8.15 | CC7.2 | Art. 30 | Section 404 |
| Encryption at rest (OSD 4.11.2) | A.8.24 | CC6.1 | Art. 32 | — |
| MFA (OSD 4.11.3) | A.8.5 | CC6.1 | — | — |
| Access control (OSD 4.11.4) | A.5.15 | CC6.1 | Art. 25 | Section 404 |
| Data inventory (OSD 4.11.5) | A.5.12 | — | Art. 30 | — |
| Incident response (OSD 4.10.2) | A.5.24-28 | CC7.3-5 | Art. 33-34 | — |
| Change management (git + PRR) | A.8.32 | CC8.1 | — | Section 404 |
| Backup + DR (OSD 4.10.4) | A.8.13-14 | A1.2 | Art. 32 | — |
| Vendor assessment | A.5.19-22 | CC9.2 | Art. 28 | — |

This mapping demonstrates that building controls once and mapping across frameworks is far more efficient than separate compliance programs.

---

## Annual Review Cycle

This roadmap is reviewed annually by the founder/CEO:
- Q1: Review current phase status, update deliverable checkboxes
- Q2: Assess whether to advance to next phase
- Q3: Update risk assessment and vendor reviews
- Q4: Plan next year's compliance objectives

---

## Document History

| Version | Date | Changes |
|---|---|---|
| 1.0.0 | 2026-03-16 | Initial roadmap created. |

---

*ARUSHAI Systems Private Limited*
