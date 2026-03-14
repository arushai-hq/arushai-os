# ARUSHAI Operating System Document

| Field | Value |
|-------|-------|
| Version | 0.5.0 |
| Last Updated | 2026-03-14 |
| Author | Irfan |
| Status | Sections 1-5 complete, Sections 6-8 scaffolded |

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

### 4.1 — Overview

All ARUSHAI code is written by Claude Code (CC). The founder never writes code directly. The founder's role is strategic: brainstorm, plan, decide, and generate instruction-only prompts. CC's role is execution: write code, run tests, manage git, update documentation.

This separation is non-negotiable. It scales — the founder's thinking time is the bottleneck, not coding speed. As ARUSHAI grows, the same protocol extends to multiple CC sessions and future AI agents.

### 4.2 — The Two-Layer System

ARUSHAI operates on two layers that never mix:

**Layer 1 — Web Session (Claude.ai / Claude Web):** This is the brainstorming and orchestration layer. Used for strategic planning, research (FORGE sessions), architecture decisions, CC prompt generation, and session debriefs. The web session acts as the founder's thinking partner — it challenges assumptions, gathers evidence, structures decisions, and translates raw ideas into actionable CC prompts. The web session never generates actual code.

**Layer 2 — Claude Code (CC):** This is the execution layer. Primary environment is Antigravity; CC CLI is the secondary environment. CC receives instruction-only prompts and writes all code, tests, documentation, and git operations. CC has its own skills and project context (CLAUDE.md, .claude/skills/) to determine implementation details. CC never makes strategic or architectural decisions — it executes within the boundaries defined by its prompts and project configuration.

**The boundary:** The web session decides WHAT to build and WHY. CC decides HOW to implement it. This boundary is strict. If the web session starts writing code, it has crossed the line. If CC starts making product decisions, it has crossed the line.

### 4.3 — The CC Prompt Standard

Every CC prompt follows this exact structure. No exceptions.

**Structure:**

- **Branch:** Always explicit. Never assume the current branch. State the branch name and include checkout command if needed. Active branches must be known (e.g., main for production, feature/hawk for development).
- **Skills to activate:** List project-level skills that are relevant to the task.
- **Context:** Reference the product living document or OSD section that provides background. CC should read this before starting work.
- **What to build:** Intent, requirements, and constraints described in plain language. This is the WHAT and WHY, never the HOW. No code blocks, no function bodies, no implementation details. CC has skills and project context to determine implementation.
- **Acceptance criteria:** Measurable outcomes that define "done." These are what the founder reviews against after CC delivers.
- **Do not:** Explicit exclusions — things CC must avoid. Prevents scope creep and unintended changes.
- **When done:** Post-completion actions. Always includes: update README.md, update living document, run tests, commit with descriptive message, push to branch.

**Rules:**

- Never include actual code in a CC prompt — not even as examples or hints. CC writes code using its own skills.
- Every prompt must specify the git branch. If the branch does not exist, include branch creation in the prompt.
- Keep prompts token-efficient. Do not restate what CC already knows from its CLAUDE.md and project skills.
- One prompt per logical unit of work. Do not overload a single prompt with unrelated tasks.

### 4.4 — The Branch Discipline

All ARUSHAI repos follow this branching model:

- **main:** Production branch. Never commit directly. All changes arrive via merge from feature or fix branches.
- **feature/[name]:** Active feature development. One branch per feature or major work item.
- **fix/[name]:** Bug fix branches. One branch per bug or related bug batch.

CC handles ALL git operations — branch creation, commits, merges, pushes. The web session never gives raw git commands to the founder. The only exception: VPS-specific manual commands (git pull, tradeos CLI, docker commands) that CC cannot execute remotely — these are given directly to the founder with clear instructions.

**Commit discipline:**

- Batch related changes into a single commit.
- Separate architecturally distinct changes into their own commits.
- Commit messages are descriptive and follow the format: type(scope): description (e.g., feat(execution): add trailing stop loss manager, fix(session): resolve ghost position from exit fill processing).

### 4.5 — The Documentation Discipline

Documentation is not optional. It is part of every CC prompt's "When done" section.

**README.md:** Must be kept up to date with every feature addition. Every CC prompt includes a requirement to update README.md with new commands, features, and current project status.

**Living Document ([Product]_context.md):** The single source of truth for each product, stored at the repo root. Updated after every concluded discussion or build cycle. Structure: Current state, Active work, On the horizon, Key learnings, Tools and resources.

**Context Archive (docs/context_archive.md):** Resolved TODOs and old session log rows move here after defined thresholds. This keeps the living document focused on current state while preserving history.

**CLAUDE.md:** Defines CC's role, boundaries, coding conventions, and project-specific rules for each repo. Must be kept current as the project evolves. CC updates CLAUDE.md as part of prompts that change project conventions or add new tools.

### 4.6 — The Skill Installation Protocol

Every new ARUSHAI repo must have appropriate skills installed at project level before any build work begins.

Skills are .claude/skills/[skill-name]/SKILL.md files within the repo. They are project-level, version-controlled, and travel with the codebase.

**Selection criteria:** Skills are chosen based on the repo's primary purpose. Documentation repos get documentation skills. Code repos get framework-specific skills. Hybrid repos get both. Never install skills irrelevant to the repo's purpose — excess skills pollute CC's context and waste tokens.

**Primary source:** Anthropic official skills repository (anthropics/skills). Custom ARUSHAI skills are maintained in arushai-hq/arushai-os and deployed to individual repos as needed.

When evaluating skills from community sources: assess relevance, quality, maintenance status, and token cost before installing. Prefer fewer, high-quality skills over many generic ones.

### 4.7 — The Quality Gate

No code merges to main without meeting these criteria:

- All acceptance criteria from the CC prompt are satisfied.
- Full test suite passes with zero failures.
- No known regressions introduced.
- README.md is updated.
- Living document is updated.
- CLAUDE.md is current (if project conventions changed).

The benchmark standard is TradeOS: 340+ tests, zero failures. Every ARUSHAI product aspires to this level of test coverage and stability.

### 4.8 — Session Continuity

Long CC sessions risk context window exhaustion. The protocol for managing this:

- When approaching context limits in a web session: proactively create a handoff document and start a new session. Do not lose continuity by letting the session die.
- Handoff includes: what was decided, what is in progress, what is blocked, what comes next.
- For session recovery: recent_chats with higher n value is more reliable than conversation_search for retrieving session-level context by title.
- When context-mode is installed on a project: use the --continue flag when resuming multi-session builds to carry forward indexed context. Without --continue, previous session data is deleted.
- The living document is the ultimate fallback for session continuity. If all else fails, the living document has the current state.

---

## Section 5 — The Context Management System

### 5.1 — Overview

Context is the lifeblood of ARUSHAI's AI-augmented operating model. Every decision, every build, every iteration depends on the right context being available at the right time. Without structured context management, knowledge gets lost between sessions, decisions get re-made, and CC wastes tokens re-learning what it already knew.

The context management system defines how knowledge flows through the organization: how it is created, where it is stored, how it is retrieved, and when it is archived.

### 5.2 — The Knowledge Hierarchy

ARUSHAI's knowledge is organized in four layers, from broadest to most specific:

**Level 1 — Company Level:** The ARUSHAI Operating System Document (this document), stored in arushai-hq/arushai-os. Defines how the entire company operates. Referenced by all products and all agents. Changes rarely — only when company-level processes or strategy evolve.

**Level 2 — Product Level:** The product living document ([Product]_context.md) at each repo root. Defines the current state, active work, roadmap, key learnings, and tools for a specific product. Changes frequently — updated after every concluded discussion or build cycle. This is the single source of truth for each product.

**Level 3 — Session Level:** Claude memory and conversation history in web sessions. Contains the working context of the current brainstorming or planning session. Ephemeral by nature — persists only within the session and through Claude's memory system across sessions.

**Level 4 — Execution Level:** CLAUDE.md and .claude/skills/ within each repo. Defines CC's role, boundaries, conventions, and capabilities for a specific project. This is the context CC loads at the start of every session. Changes when project conventions evolve or new skills are added.

**The rule:** Higher levels inform lower levels, never the reverse. The OSD shapes product living documents. Product living documents shape CLAUDE.md and skills. Session context is temporary and must be consolidated into the appropriate permanent layer before it is lost.

### 5.3 — The Living Document Pattern

Every ARUSHAI product has a living document at its repo root: [Product]_context.md (e.g., TradeOS_context.md).

**Purpose:** The single source of truth for the product's current state. When a new session begins — whether web session or CC session — the living document is the first thing read to establish context.

**Structure:**

- **Purpose and context:** What this product is and what stage it is at.
- **Current state:** What has been built, what is deployed, what is working.
- **Active work:** What is currently in progress, including branch names and status.
- **On the horizon:** Planned features, deferred items, future considerations.
- **Key learnings and principles:** Hard-won lessons, permanent rules, bug patterns to watch for.
- **Tools and resources:** Infrastructure, APIs, dependencies, and development tools in use.

**Update Protocol:**

- Every concluded discussion in a web session triggers a CC prompt to apply a delta update to the living document before moving on.
- Updates are additive — add what is new, modify what has changed, do not rewrite the entire document.
- The living document reflects reality, not aspiration. If something is not built yet, it belongs in "On the horizon," not "Current state."

### 5.4 — The Context Archive

As living documents grow, resolved items and old session history accumulate and clutter the current view. The context archive solves this.

**Location:** docs/context_archive.md within each product repo.

**What moves to the archive:**

- Resolved TODOs and completed work items.
- Old session log rows after the session debrief is complete.
- Bug descriptions after bugs are fixed and verified.
- Superseded decisions (with a note about what replaced them).

**When to archive:** After defined thresholds — when the living document becomes unwieldy or when a natural milestone is reached (e.g., end of a session series, major release).

The archive preserves history without cluttering the active working document. If a question arises about past decisions, the archive is searchable. But the living document remains focused on the present and immediate future.

### 5.5 — The FORGE Session Pattern

FORGE (Foundations of Reasoning, Grounding and Engineering) sessions are deep-dive research and brainstorming sessions conducted in web sessions. They are used for foundational knowledge gathering that informs product decisions, architecture choices, or company strategy.

**Characteristics of a FORGE session:**

- Assigned a unique session ID (e.g., ARUSHAI-FORGE-001).
- Conducted as a dedicated web session with deep research.
- Web search and evidence gathering are mandatory — every claim must be backed by verifiable sources.
- No implementation during a FORGE session — it is pure research and planning.
- Outputs are synthesized into a structured summary for long-term reference.

**FORGE Session Outputs:**

- Session summary stored in arushai-hq/arushai-os/docs/forge-sessions/ with filename FORGE-[NNN]-summary.md.
- Summary structure: Session ID, Date, Topic, Key Findings (with source references), Repos Discovered (with stars, URLs, one-line descriptions), Decisions Made, Open Questions, Connection to OSD Sections.
- Key repos, tools, and resources bookmarked in Claude memory for future reference.
- If findings impact specific OSD sections or product living documents, those updates are noted and queued.

FORGE sessions are numbered sequentially. The current session (FORGE-001) established the foundational AI agent engineering knowledge base covering seven pillars: Agent Architecture, Reasoning Frameworks, Grounding and Hallucination Mitigation, Memory Architecture, Tool Use and MCP, Guardrails Evaluation and Observability, and Multi-Agent Orchestration.

### 5.6 — Session Continuity Protocol

Context loss between sessions is the single biggest productivity killer in the AI-augmented workflow. The continuity protocol prevents this.

**Within a web session:**

- When approaching context limits, proactively create a handoff document before the session ends. Do not let the session die without capturing state.
- Handoff document includes: what was decided, what is in progress, what is blocked, what comes next, and any open questions.
- Update the product living document with any decisions or context generated during the session before ending.

**Between web sessions:**

- Claude's memory system carries key facts across sessions automatically.
- For session recovery, recent_chats with higher n value is more reliable than conversation_search for retrieving session-level context by title.
- The living document is the ultimate fallback. If memory is incomplete and chat history is unclear, the living document has the authoritative current state.

**Within CC sessions:**

- When context-mode is installed on a project, use the --continue flag to carry forward indexed context from the previous session. Without --continue, previous session data is deleted and the session starts fresh.
- CLAUDE.md and project skills provide baseline context that persists regardless of session state.
- For multi-session builds, the living document captures what was completed in each session so the next session can pick up without re-explanation.

**The principle:** No session should end without its knowledge being captured somewhere permanent. Conversations are ephemeral. Documents are durable.

### 5.7 — Context Hygiene Rules

- Never let a living document become stale. If the document says "in progress" but the work finished two weeks ago, the document is lying. Update it.
- Never duplicate context across multiple documents. Each fact lives in one authoritative location. Other documents reference it, they do not copy it.
- Never let session context remain only in chat history. If it matters, it belongs in a document.
- Archive aggressively. A living document cluttered with resolved items is harder to use than one that is lean and current.
- Treat context like code: it has a lifecycle (create, use, update, archive), it needs maintenance, and it degrades if neglected.

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
