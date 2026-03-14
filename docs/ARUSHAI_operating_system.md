# ARUSHAI Operating System Document

| Field | Value |
|-------|-------|
| Version | 0.3.0 |
| Last Updated | 2026-03-14 |
| Author | Irfan |
| Status | Sections 1-3 complete, Sections 4-8 scaffolded |

---

## Table of Contents

1. [Company Identity and Mission](#section-1--company-identity-and-mission)
2. [The Decision-Making Framework](#section-2--the-decision-making-framework)
3. [The Product Development Lifecycle](#section-3--the-product-development-lifecycle)
4. [The CC Interaction Protocol](#section-4--the-cc-interaction-protocol)
5. [The Context Management System](#section-5--the-context-management-system)
6. [The Financial Framework](#section-6--the-financial-framework)
7. [The Security and Governance Framework](#section-7--the-security-and-governance-framework)
8. [The Evolution Roadmap](#section-8--the-evolution-roadmap)

---

## Section 1 — Company Identity and Mission

### Company Name

ARUSHAI Systems Private Limited

### Registration

India (Private Limited Company). The company targets the Indian market as its primary customer base. Operations are managed remotely from Qatar by the founder.

### Founded By

Irfan — 15-16 years of hands-on technology experience spanning full-stack development, AI/ML, and systems architecture.

### Company Vision

Build a multi-generational wealth platform from the ground up. ARUSHAI is not a single product or a single industry — it is a family institution built on technology. Starting with AI and software as the first vertical (because that is where the founder's deepest expertise lies), with the explicit intention to expand into other domains as opportunities arise. The name "Systems" is deliberate — it is broader than software, broader than SaaS, broader than any single market.

### The Three Layers of Purpose

**Layer 1 — Personal:** Financial freedom and entrepreneurial independence. Not an employee building someone else's vision — a founder building his own.

**Layer 2 — Family:** A platform that the next generation inherits — not just wealth but infrastructure. Younger family members entering the workforce will have ready-built tools, systems, knowledge, and a foundation rather than starting from scratch.

**Layer 3 — Community:** Create employment opportunities. Solve real problems that real people face in their day-to-day lives, using the simplest and most optimized solutions possible.

### Operating Philosophy

- Technology and AI is the starting point, not the ceiling.
- Every product solves a real human problem — not technology for technology's sake.
- Simplest approach, best solution, most optimized delivery.
- Build from the ground up — no shortcuts, no half-measures.
- If it goes well (Alhamdulillah), it refactors into something much bigger.
- Multi-generational thinking: every decision weighted against long-term compounding value, not short-term metrics.

### What ARUSHAI Is NOT

- Not a SaaS company — it is a systems company that may build SaaS products among other things.
- Not locked to any single industry or business model.
- Not a lifestyle business — it is designed for scale and generational transfer.
- Not limited to the founder's current skillset — the platform is designed to grow beyond any individual.

### Current Vertical: Technology and AI

- **TradeOS** — Algorithmic intraday trading system for NSE via Zerodha KiteConnect (wealth generation engine).
- **Flint** — AI-powered message polishing for professionals (B2C/B2B SaaS product).
- **VIZBOARD** — Internal visual strategy board for ARUSHAI client meetings (operational tool).
- **Future products** — Determined by market problems identified, not predetermined roadmap.

### What Makes ARUSHAI Different

- Founder-operator with 15-16 years of deep technology experience executing hands-on.
- AI-augmented operating model — one person operating at the capacity of a full team through AI agents and intelligent tooling.
- Problem-first approach: starts with the human problem, works backward to the technology solution.
- Multi-generational intent: decisions are made for decades, not quarters.
- The motivation behind the company — family, legacy, and genuine desire to help others — drives a discipline that pure profit-seeking cannot sustain.

---

## Section 2 — The Decision-Making Framework

### 2.1 — The Nemawashi Protocol

Every significant decision at ARUSHAI follows the Nemawashi principle: deep planning before any implementation begins.

The ratio: 60-70% planning, 30-40% implementation. Planning is considered complete not by a checklist but by a judgment call — when the founder can see enough of the big picture with sufficient detail to define an MVP, it is time to move from brainstorming to building.

**Nemawashi Completion Signals:**

- The problem is clearly defined and validated.
- The architecture or approach has been explored with alternatives considered.
- Edge cases and risks have been identified (not necessarily all solved, but acknowledged).
- An MVP scope is visible — the minimum version that tests whether the brainstorming holds up in reality.
- The founder has the conviction that the direction is clear enough to start building.

**The MVP Bridge:** Nemawashi does not mean planning everything to 100%. It means planning enough to build an MVP that validates the thinking. The cycle is: Brainstorm, build MVP, learn from reality, refine, build more. Real-world feedback from an MVP is worth more than additional theoretical planning.

**What Nemawashi looks like in practice:**

- Web session deep-dive with research, evidence gathering, and structured analysis.
- Alternatives compared (frameworks, approaches, architectures).
- Decision locked with rationale documented.
- CC prompt generated only after the decision is locked.
- Living document updated with the decision and context before moving on.

### 2.2 — Decision Classification

Every decision falls into one of four categories. The category determines who makes it and how.

**STRATEGIC (Founder only — never delegated):**

- New product decisions (what to build, for whom, why).
- Architecture overhauls or major technology changes.
- Market positioning and pricing.
- Company direction and expansion into new domains.
- Partnership and business development decisions.
- Capital allocation between products.

Process: Always requires a dedicated web session brainstorm. Always documented in OSD or product living document. No time pressure — take the time needed to get it right.

**TACTICAL (Founder decides, AI agents can propose):**

- Feature prioritization within a product.
- Sprint planning and task sequencing.
- Technology selection within an established architecture (which library, which tool).
- Bug severity classification and triage priority.

Process: Can be decided in a web session or during CC prompt preparation. AI agents (Stage 3+) may recommend, but the founder approves.

**OPERATIONAL (Fully delegated to CC/agents):**

- Code implementation details (naming, structure, patterns).
- Test writing and test strategy within established quality standards.
- Git operations (commits, branches, merges).
- Documentation updates following established templates.
- Routine dependency updates.

Process: CC and future agents handle these autonomously within the boundaries set by CLAUDE.md, project skills, and quality gates. No approval needed.

**FINANCIAL (Founder approval always required):**

- Any spend above established budget thresholds.
- Trading capital allocation changes (TradeOS).
- New subscription or service commitments.
- Switching AI providers or plans.

Process: No agent may commit financial resources without explicit founder approval. Budget monitoring is automated; spending decisions are human.

### 2.3 — Bug Triage Protocol

Bugs are prioritized by severity, with a bias toward fixing before building new features.

**Philosophy:** Code in production should run with minimum bugs. Fixing bugs takes priority over new features in most cases. A clean, stable codebase compounds in value — technical debt compounds in cost.

**Severity Classification:**

- **Critical:** System is broken, data is at risk, trades are affected, users are blocked. Drop everything and fix immediately.
- **High:** Feature is degraded but system functions. Fix before starting any new feature work.
- **Medium:** Non-blocking issue, workaround exists. Schedule in the next build cycle.
- **Low:** Cosmetic, minor UX, or edge case. Fix when convenient or batch with related work.

**The Fix Protocol:**

- Deep-dive to find the root cause — never patch symptoms.
- Fix the root cause.
- Run the full test suite after the fix.
- Verify the fix does not introduce new bugs (no regression).
- If the fix touches critical paths, add new test cases to prevent recurrence.
- Batch related bug fixes into a single commit; separate architecturally distinct fixes into their own commits.

### 2.4 — Financial Framework: AI Spend

**Primary AI investment:** Anthropic Max Plan (~$200/month). This is the core engine for all ARUSHAI operations — web session brainstorming, Claude Code execution, and future multi-agent workloads. The goal is to maximize value extraction from this subscription before spending elsewhere.

**Allocation priority for the Max Plan:**

- Strategic brainstorming (web sessions like FORGE sessions) — highest value per token.
- CC execution for product builds — direct output generation.
- Future multi-agent operations — as Stage 3+ unfolds.

**Secondary provider:** OpenRouter as a fallback for cases where the Anthropic subscription cannot be used. Budget kept minimal (~$30-40 credit reserve). This is Plan B, not a parallel system.

**The Cost Principle:** Maximize the subscription already being paid for. Do not split spend across multiple providers unless there is a clear technical reason (model not available, specific capability needed). Every dollar spent on a secondary provider should have a justification for why the Max Plan could not handle it.

**Future cost scaling:** As the company grows and multi-agent workloads increase, API costs will be evaluated quarterly. The approach is to tier costs — expensive models for planning and orchestration, cheaper models for execution — rather than using one model tier for everything.

**TradeOS Trading Capital Risk Limits:** [TO BE DEFINED — trading drawdown limits, daily/monthly loss caps, and system pause triggers will be established as TradeOS strategies mature in live trading. Reference TradeOS_context.md for current slot-based position sizing parameters.]

### 2.5 — The Escalation Protocol

When should an AI agent (Stage 3+) stop and ask the founder?

**Always escalate when:**

- The task involves financial commitment or spend above threshold.
- The action is irreversible (production deployment, trade execution, data deletion, user-facing communication).
- The agent encounters ambiguous or conflicting requirements.
- The agent's confidence in its approach is low.
- An error occurs that the agent cannot self-resolve after one retry.
- The task crosses product boundaries (requires coordination between multiple ARUSHAI products).
- Security-sensitive operations (API key rotation, access changes, infrastructure changes).

**Never escalate when:**

- Routine code implementation within established patterns.
- Test writing and running.
- Git operations following branch discipline.
- Documentation updates following templates.
- Dependency updates that pass all tests.

---

## Section 3 — The Product Development Lifecycle

### 3.1 — Overview

Every ARUSHAI product follows a five-phase lifecycle. No phase is skipped. Each phase has defined inputs, outputs, and quality gates before moving to the next.

The phases: Research and Validation, Architecture and Planning, Build, Deploy and Validate, Operate and Iterate.

This lifecycle applies to new products, major features, and significant architectural changes. Minor bug fixes and routine updates follow the Bug Triage Protocol (Section 2.3) instead.

### 3.2 — Phase 1: Research and Validation

**Purpose:** Determine whether a problem is worth solving and whether ARUSHAI can solve it differently or better than what exists.

**Activities:**

- Identify a real human problem — not a technology looking for a problem.
- Conduct a FORGE session (web session deep-dive) to research the domain, market, competitors, and technical feasibility.
- Gather evidence: market size, existing solutions, gaps in current offerings, relevant technologies.
- Every claim must be backed by evidence — web search results, published data, or verifiable sources. No assumptions presented as facts.
- Apply the differentiation check: if ARUSHAI cannot offer something meaningfully different or better, do not build.

**Outputs:**

- FORGE session summary stored in arushai-hq/arushai-os/docs/forge-sessions/.
- GO / NO-GO decision documented with rationale.

**Quality Gate:** The founder must be able to articulate in one sentence what problem this solves, for whom, and why ARUSHAI is the right one to solve it. If this sentence is unclear, the product stays in research.

### 3.3 — Phase 2: Architecture and Planning

**Purpose:** Design the solution completely before writing any code. This is the Nemawashi phase — the heaviest investment of thinking time.

**Activities:**

- Define the technology stack with rationale for each choice.
- Design the data model, API structure, and system architecture.
- Identify deployment strategy (VPS, Vercel, Docker, etc.).
- Model costs: API costs, hosting costs, projected revenue if applicable.
- Explore edge cases, failure modes, and security considerations.
- Compare alternative approaches — never commit to the first idea without evaluating at least one alternative.
- Create the product living document ([Product]_context.md) at the repo root as the single source of truth.
- Set up the repo with appropriate skills installed at project level (per the Skill Installation Protocol defined in Section 4).
- Write comprehensive CLAUDE.md defining CC's role, boundaries, and conventions for this project.
- Generate CC prompts only after architecture decisions are locked.

**Outputs:**

- Product living document created and populated with architecture decisions.
- Repo initialized with CLAUDE.md, skills, README.md, and project structure.
- First CC prompts ready for execution.

**Quality Gate:** Architecture decisions are locked. The founder can describe the full system — stack, data flow, deployment, and cost model — without hesitation. Any open questions have been resolved or explicitly deferred with rationale.

### 3.4 — Phase 3: Build

**Purpose:** Execute the plan through CC. The founder generates instruction-only prompts; CC writes the code.

**Activities:**

- CC executes prompts following the CC Interaction Protocol (Section 4).
- Every CC prompt specifies: git branch, skills to activate, context reference, what to build, acceptance criteria, do-not list, and when-done actions.
- CC prompts never contain actual code — only intent, requirements, and constraints. CC has its own skills and project context to determine implementation.
- Test suite grows with every feature. The benchmark is TradeOS: 340+ tests, zero failures.
- README.md updated with every feature addition.
- Living document updated after every concluded discussion or build cycle.
- Batch related changes into single commits. Separate architecturally distinct changes into their own commits.

**The Build Rhythm:**

- Web session: brainstorm and lock the next feature or fix.
- Generate CC prompt with full context.
- CC executes and delivers.
- Founder reviews output against acceptance criteria.
- If acceptance criteria met: merge, update living document, move to next.
- If not met: identify gaps, generate follow-up CC prompt, iterate.
- After each build cycle: run full test suite, verify zero failures.

**Outputs:**

- Working code committed to feature branch.
- Tests passing with zero failures.
- README.md and living document current.
- Feature branch ready for merge to main.

**Quality Gate:** All acceptance criteria from the CC prompt are met. Full test suite passes with zero failures. README.md and living document are updated. No known regressions.

### 3.5 — Phase 4: Deploy and Validate

**Purpose:** Put the product into production and verify it behaves correctly in the real environment.

**Activities:**

- Deploy following the product-specific deployment process (git pull on VPS for TradeOS, Vercel deploy for Flint, Docker Compose for VIZBOARD).
- Run smoke tests in the production environment — verify core functionality works end-to-end.
- Set up monitoring appropriate to the product: automated notifications (Telegram for TradeOS), error tracking, log monitoring.
- Monitor actively for the first 24-48 hours — do not deploy and walk away.
- Establish a notification cadence: regular health check signals (e.g., TradeOS sends Telegram notifications every 30 minutes during market hours). If a scheduled notification is missed, immediately check server logs.
- Document any production-specific configuration or environment differences.

**The Monitoring Philosophy:** Production is not "set and forget." Every deployed product is actively monitored. Missed notifications or unexpected silence from monitoring triggers immediate investigation. The founder checks monitoring regularly and treats monitoring gaps as potential incidents.

**Outputs:**

- Product live in production.
- Monitoring configured and verified.
- First 24-48 hours monitored without critical issues.
- Any production issues documented and fed back into the Build phase.

**Quality Gate:** Product is running in production with active monitoring. No critical bugs in the first 24-48 hours. Monitoring notifications are arriving on schedule.

### 3.6 — Phase 5: Operate and Iterate

**Purpose:** Continuously run, monitor, improve, and decide the product's future.

**Activities:**

- Ongoing monitoring per the established cadence.
- Bug triage following Section 2.3 protocol.
- Session debriefs after significant operating periods (TradeOS pattern: run the system, identify issues, fix them, document findings, as done in Sessions 01-04).
- Feature iteration: new ideas and improvements enter through the Nemawashi process (Phase 1-2 lite for features within an existing product).
- Performance tracking: is the product delivering on its intended purpose?

**Idea Capture:** Currently, new ideas and feature requests live in the founder's mind until a web session begins. This is a known gap. A structured capture system (voice notes, quick-entry tool, or simple backlog file per product) is on the roadmap to ensure ideas are not lost between sessions. Until that system exists, the living document serves as the capture point during active sessions.

**Product Survival Criteria:** If a deployed product consistently fails to deliver value (no revenue, no traction, ongoing costs with no return) over a sustained period (2-3 months post-launch), the founder evaluates:

- Is the problem real? (Revisit Phase 1 research.)
- Is the solution wrong? (Iterate on approach.)
- Is the market wrong? (Pivot or expand audience.)
- Is it time to sunset? (Remove from production, reduce costs, reallocate effort.)

The default is to iterate (Deploy, Validate, Operate, Iterate), not to kill. Products are given multiple iteration cycles before a sunset decision. But cost-awareness is maintained — a product running at a loss with no improvement trajectory is paused, not left running indefinitely.

**Outputs:**

- Ongoing stable operation with monitoring.
- Bugs fixed, features added through the standard lifecycle.
- Periodic session debriefs documented in living document.
- Clear-eyed evaluation of product viability at regular intervals.

### 3.7 — The Lifecycle Applied to ARUSHAI Products

Current product status mapped to lifecycle phases:

- **TradeOS:** Phase 5 (Operate and Iterate) — S1 strategy in production on main branch, HAWK AI engine in active development on feature/hawk branch.
- **Flint:** Phase 3-4 (Build transitioning to Deploy) — Multi-provider AI abstraction layer built, local testing and Vercel deployment pending.
- **VIZBOARD:** Phase 3 (Build) — Product definition locked, CC prompts generated, build execution in progress.

---

## Section 4 — The CC Interaction Protocol

The rules governing how the founder interacts with Claude Code. Covers the web session vs CC separation, the CC prompt template, branch discipline, documentation discipline, quality gates, and the no-code-in-prompts rule. This section is directly translatable into CLAUDE.md files for each product repo.

[TO BE COMPLETED]

---

## Section 5 — The Context Management System

How knowledge flows through the organization. Covers the living document pattern, session continuity protocol, knowledge hierarchy (company, product, session, execution), the FORGE session pattern for research, and context archival rules.

[TO BE COMPLETED]

---

## Section 6 — The Financial Framework

Cost tracking per product, budget thresholds and alerts, revenue tracking, the cost-quality tradeoff rule for AI model selection, and trading capital allocation rules. This section becomes the rulebook for the future Finance Agent.

[TO BE COMPLETED]

---

## Section 7 — The Security and Governance Framework

Secret management, access control per agent, audit trail requirements, the company-wide "Do Not" list, and irreversible action approval gates. This section becomes the guardrails layer for every agent in the organization.

[TO BE COMPLETED]

---

## Section 8 — The Evolution Roadmap

Maps the five stages from solo developer to AI-operated organization: Stage 0 (Human Orchestrator), Stage 1 (Formalize OS), Stage 2 (Extend CC), Stage 3 (First AI Hires), Stage 4 (Orchestration Layer), Stage 5 (One-Person Multi-Million Org). Includes stage transition criteria and metrics to track.

[TO BE COMPLETED]
