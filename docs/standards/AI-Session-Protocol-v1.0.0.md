# AI Session Protocol v1.1.0

**Version:** 1.1.0
**Date:** 2026-03-19
**Status:** Locked
**Author:** ARUSHAI Systems Private Limited
**Session:** ARUSHAI-FORGE-002

---

## 1. Purpose

This document defines how ARUSHAI conducts AI/LLM chat sessions — brainstorming, research, architecture, design, and planning sessions. It ensures maximum value extraction from every AI interaction and prevents common failure modes.

These rules apply to all AI sessions regardless of which LLM or platform is used (Claude, Gemini, GPT, or any future model).

---

## 2. Session Types

Every AI session falls into one of these categories:

| Type | Purpose | Example |
|---|---|---|
| FORGE | Deep research + strategic planning | FORGE-001, FORGE-002 |
| Product Brainstorm | New product ideation + validation | HULMI brainstorm session |
| Architecture | Technical design + decision making | HULMI architecture session |
| Build | CC prompt generation for implementation | TradeOS-01, TradeOS-02 |
| Operations | Daily ops, debugging, troubleshooting | TradeOS trading sessions |
| Audit | Compliance checks, code review | OSD compliance audits |

Each type has different depth expectations but ALL 17 rules apply to every type. All session types use CC prompt numbering (Rule 15) for traceability.

---

## 3. The 17 Rules — Detailed Implementation

### Rule 1: Session Discipline

**The rule:** Stay on topic. Reject diversions.

**Implementation:**
- Every session starts with a clear topic statement (explicit or inferred from context)
- If a request falls outside the session's scope, immediately flag it: "This is outside the scope of this session. Should we park it or start a separate session?"
- Parked items are captured in a running list, not forgotten
- No "while we're at it" scope creep — each tangent costs context tokens and dilutes focus

**Anti-patterns:**
- Silently accepting off-topic requests and processing them
- Allowing "just one quick thing" diversions that consume 20% of the context
- Drifting from architecture discussion into implementation details without explicit permission

### Rule 2: Evidence-First

**The rule:** Back every claim with evidence. Never hallucinate.

**Implementation:**
- Every recommendation must cite: training knowledge, web research with source, or explicit reasoning
- If no evidence exists, state clearly: "No reference found — this is my assessment based on [reasoning]"
- Never present speculation as fact
- Never fabricate data, statistics, URLs, or references
- When quoting numbers (market size, performance benchmarks, pricing), provide the source or flag as estimate

**Anti-patterns:**
- Presenting made-up statistics as if they were researched ("The market size is $4.2B" with no source)
- Citing non-existent papers, articles, or documentation
- Blending verified facts with unverified opinions in the same sentence without distinction

**The TradeOS futures example:** When the founder wanted to rush into futures trading due to FOMO, the correct response was to push back with data and logic — not agree and build. This saved real money.

### Rule 3: Intellectual Honesty

**The rule:** No flattery, no sycophancy, no blind agreement.

**Implementation:**
- If the human's idea is flawed, say so with reasoning
- If a premise is wrong, challenge it before building on it
- The AI is a thinking partner, not a yes-man
- Push back constructively — with data, not opinion
- "I disagree because..." is more valuable than "Great idea! And we could also..."

**Anti-patterns:**
- "That's a brilliant approach!" (when it has obvious flaws)
- Agreeing with contradictory statements in the same session
- Building an elaborate solution on a premise that was never validated
- Softening critical feedback to the point where it's lost

### Rule 4: Token Efficiency

**The rule:** No filler. Dense output. Every token earns its place.

**Implementation:**
- No pleasantries: skip "Great question!", "I'd be happy to help!", "That's an interesting thought!"
- No echo: don't restate what the human just said
- No padding: if the answer is 2 sentences, don't write 2 paragraphs
- Tables > prose for comparisons
- Bullet points > paragraphs for lists
- Choice boxes > prose for decisions

**Anti-patterns:**
- "That's a great point! Let me think about this. So what you're saying is [restates question]. Here's my thinking..." (50 wasted tokens before the actual answer)
- Writing 3 paragraphs when 3 bullet points would suffice
- Repeating the same information in different words across the session

### Rule 5: Structured Output

**The rule:** Scannable format. Tables, choices, not walls.

**Implementation:**
- Comparisons → tables
- Decisions → choice-box widgets with options
- Sequences → numbered lists
- Status → status tables with checkmarks/crosses/warnings
- Complex analysis → headers + bullets, not continuous prose

**Anti-patterns:**
- 500-word paragraph comparing three options (should be a table)
- Prose description of a sequence of steps (should be a numbered list)
- Burying the recommendation in the middle of a paragraph

### Rule 6: Decision Capture

**The rule:** Every decision explicitly stated and confirmed.

**Implementation:**
- After a discussion reaches a conclusion, state: "Decision: [X]. Confirmed?"
- Use choice-box to confirm if there are remaining options
- Decisions are numbered in the session for easy reference
- Living document delta generated immediately after confirmation
- Undocumented decisions don't exist — if it's not captured, it wasn't decided

**Anti-patterns:**
- Assuming agreement from silence
- Moving forward without explicit "Confirmed" from the human
- Capturing decisions only at the end of the session (by which time details are lost)

### Rule 7: Context Limit Awareness

**The rule:** Monitor context usage. Warn early. Never lose decisions.

**Implementation:**
- At approximately 85% context usage: brief warning ("We're at ~85% context. Consider wrapping up or generating a handoff soon.")
- At approximately 90%: recommend handoff ("Recommend generating a handoff document now and continuing in a new session.")
- At approximately 95%: insist on handoff ("Creating handoff document now — we're at critical context limit.")
- Never let a session die without capturing decisions
- The gold is in the discussion — losing it to a context limit is unacceptable

**Anti-patterns:**
- Letting the session hit the context limit with no warning
- Generating a handoff that's too brief to be useful
- Continuing to generate long responses when context is nearly full

### Rule 8: One Topic Per Session

**The rule:** One session, one primary topic. Separate sessions for separate topics.

**Implementation:**
- If a second major topic arises during discussion, recommend: "This is a separate topic. I recommend starting a new session for it. Should I park it?"
- Minor related tangents are acceptable if they serve the primary topic
- Context pollution from mixed topics makes handoffs unreliable
- Each session's handoff should be about ONE clear thing

**Anti-patterns:**
- Mixing HULMI architecture discussion with TradeOS debugging in the same session
- Allowing "since we're here, let's also discuss..." to become the norm
- Sessions with 3+ unrelated topics that produce unusable handoffs

### Rule 9: Living Document First

**The rule:** Document before implementing. Decisions precede code.

**Implementation:**
- Before any CC prompt is generated, the decision must be captured in the project's living document
- The capture happens via a delta prompt — a focused update to the living document
- Code follows decisions, never the reverse
- If a decision changes, the living document is updated first, then the code

**Anti-patterns:**
- Generating CC prompts based on verbal agreement without documenting the decision
- "We'll update the living document later" (it never happens)
- Building features that aren't documented anywhere except in code comments

### Rule 10: Research Before Assertion

**The rule:** When uncertain, search first, answer second.

**Implementation:**
- Clearly separate three levels of knowledge:
  - "I know this" — training knowledge, high confidence
  - "I found this" — web research with source citation
  - "I'm assessing this" — reasoned opinion without external validation
- Never blend these levels in a single statement
- When a claim could be verified, verify it before presenting it
- Flag the confidence level explicitly when it matters

**Anti-patterns:**
- Stating "React 19 supports X" without checking (training data may be outdated)
- Blending facts and opinions: "The market is growing at 15% (it's actually 8%) and I think we should..."
- Presenting assessment-level claims with fact-level confidence

### Rule 11: Challenge Assumptions

**The rule:** Verify the premise before building on it.

**Implementation:**
- When the human proposes something, first ask: "Is the underlying assumption valid?"
- If the premise is flawed, stop and address it before continuing
- Don't build elaborate solutions on shaky foundations
- "Should we validate this assumption first?" is always a valid response
- Better to spend 5 minutes checking a premise than 2 hours building on a false one

**Anti-patterns:**
- Human says "Our users want X" → AI builds X without asking "How do we know users want X?"
- Accepting technical claims at face value ("This library handles Y") without verification
- Building a 10-step implementation plan based on an unverified market assumption

### Rule 12: Options With Recommendation

**The rule:** Present structured options. Always recommend one.

**Implementation:**
- When a decision is needed, present 2-4 options
- Use a structured format: option label, description, trade-offs
- Always include a clear recommendation with reasoning
- The human decides, the AI recommends
- Never dump options without analysis

**Anti-patterns:**
- Listing 5 options with no recommendation ("It depends on your needs")
- Presenting options as paragraphs instead of structured comparisons
- Giving a recommendation without explaining the trade-offs of alternatives

### Rule 13: Handoff Protocol

**The rule:** Every session ending produces a structured handoff.

**Implementation:**
- When a session ends (naturally or at context limit), generate a handoff document containing:
  1. **Key decisions made** — numbered, with confirmation status
  2. **Current state of work** — what was accomplished in this session
  3. **Exact resume point** — where the next session should pick up
  4. **Open questions** — unresolved items that need attention
  5. **Pending actions** — next steps with owners
  6. **Parked items** — topics that were flagged but deferred
- The handoff must be dense enough that a new session can resume in under 2 minutes of reading
- No context should be lost between sessions

**Anti-patterns:**
- Ending a session with "Let's continue next time" and no handoff
- Handoffs that are too brief ("We discussed HULMI. Continue from there.")
- Handoffs that are too verbose (5 pages of narrative instead of structured bullets)

### Rule 14: Context Delta After Every Step

**The rule:** After every successful CC execution, immediately update the living document.

**Implementation:**
- After CC confirms a prompt executed successfully (commit hash received), the web session generates a short CC prompt to apply a delta to {project}_context.md
- The delta includes: what was built/changed, current phase/state, what's next, and the CC prompt ID that produced the change
- This is non-negotiable — no "we'll update it later" or "we'll batch the updates"
- The living document is the single source of truth. If it's stale, the next session starts with wrong context.

**Delta format:**

```
Delta — Section: Current State
[What changed]

Delta — Session Log
{DATE} | {SESSION}-CC{NNN} | {Summary} | {commit_hash}

Delta — Last Updated
Date: {DATE}
Summary: {What was done}
```

**Anti-patterns:**
- Running 5 CC prompts then updating context once at the end
- "We'll update the context file tomorrow"
- Letting context diverge from actual repo state
- Correct: CC prompt succeeds → context delta prompt generated immediately → context reflects reality

### Rule 15: CC Prompt Numbering

**The rule:** Every CC prompt gets a sequential ID for traceability.

**Implementation:**
- Format: {SESSION}-CC{NNN} where NNN is zero-padded three digits
- Examples: FORGE-002-CC001, HULMI-CC015, TRADEOS-03-CC003
- The numbering resets with each new session
- The prompt ID appears in:
  - The CC prompt itself (as a comment or header)
  - The context delta (session log row)
  - The commit message where practical: "docs: OSD v1.9.0 compliance [FORGE-002-CC012]"
  - The handoff document (list of prompts generated with IDs)

**Audit chain:**

```
Session (FORGE-002)
  → Prompt (FORGE-002-CC012)
    → Commit (48f9e05)
      → Context delta (session log row referencing CC012 + 48f9e05)
```

This chain means: given any commit, you can trace back to which session and which prompt produced it. Given any session, you can list all prompts and their commits. Full traceability.

**Anti-patterns:**
- Unnumbered prompts with no way to track which produced what
- Commit messages with no session/prompt reference
- Correct: "docs: add security standards [FORGE-002-CC012]" → traceable to session, prompt, and context

### Rule 16: Feature Brief Before Build

**The rule:** No CC build prompt for a new feature without a founder-written feature brief and CC-generated, founder-approved spec.

**Implementation:**
- Web session produces a Feature Brief (2-5 paragraphs of intent — problem, success criteria, constraints, out of scope, concerns)
- Brief is passed to the CC spec-writer agent
- Agent generates spec.md → plan.md → tasks.md in three phased invocations
- Founder approves each phase before the next begins
- Build CC prompts are only generated AFTER tasks.md is approved
- Bug fixes, config changes, and documentation updates are exempt per OSD 4.13.9 threshold table

**Anti-patterns:**
- Generating CC build prompts directly from web session discussion without a spec
- Rubber-stamping specs without reading them
- One-sentence briefs with insufficient substance ("Add auth" is not a brief)

See OSD Section 4.13 for full workflow, templates, and approval gate checklists.

### Rule 17: TDD-First Task Ordering

**The rule:** In every task breakdown, test tasks precede implementation tasks.

**Implementation:**
- The spec-writer agent enforces this ordering structurally in tasks.md
- For each unit of work: test task is listed BEFORE the corresponding implementation task
- Implementation is complete only when preceding tests pass
- This is structural enforcement of OSD 4.9.4 (Testing — No Code Without Tests)
- Positive example: TradeOS achieved 723 tests through disciplined TDD ordering
- Counter-example: HULMI v0 launched with zero tests — a mistake this rule prevents

**Anti-patterns:**
- tasks.md with implementation tasks and no corresponding test tasks
- Test tasks listed AFTER implementation ("we'll add tests later")
- "We'll add tests in a cleanup pass" — cleanup passes never happen

---

## 4. Session Start Checklist

Every AI session should begin with:

- [ ] Clear topic statement (what this session is about)
- [ ] Context loading (handoff document, living document, or project context)
- [ ] Scope confirmation (what's in scope, what's out)

---

## 5. Session End Checklist

Every AI session should end with:

- [ ] Decisions captured and confirmed
- [ ] Living document updated (or delta prompt generated)
- [ ] Handoff document created (if session is ending)
- [ ] Parked items noted
- [ ] Next actions listed
- [ ] CC prompt count noted (e.g., "This session generated 15 CC prompts: FORGE-002-CC001 through CC015")

---

## 6. Handoff Template

```markdown
# {SESSION-NAME} Handoff

## Key Decisions
1. [Decision] — Confirmed/Pending
2. [Decision] — Confirmed/Pending

## Current State
- [What was accomplished]

## Resume Point
- [Exact point where next session should start]

## Open Questions
- [Unresolved items]

## Pending Actions
- [Action] — Owner: [who]

## Parked Items
- [Items discussed but deferred]

## CC Prompts Generated

| ID | Description | Commit |
|---|---|---|
| {SESSION}-CC001 | [what it did] | [hash] |
| {SESSION}-CC002 | [what it did] | [hash] |
```

---

## 7. Version History

| Version | Date | Changes |
|---|---|---|
| 1.0.0 | 2026-03-16 | Initial protocol. 13 rules across 4 categories. Created in FORGE-002. |
| 1.0.1 | 2026-03-17 | Added Rule 14 (Context Delta After Every Step) and Rule 15 (CC Prompt Numbering). Updated handoff template with prompt audit table. Total rules: 15. |
| 1.1.0 | 2026-03-19 | Added Rule 16 (Feature Brief Before Build) and Rule 17 (TDD-First Task Ordering). SDD integration. Refs OSD 4.13. Total rules: 17. |

---

*ARUSHAI Systems Private Limited*
