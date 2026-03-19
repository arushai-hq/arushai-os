---
name: sdd-workflow
description: Execute ARUSHAI's Spec-Driven Development workflow — generate feature specs from founder briefs, create implementation plans with OSD compliance checks, and break down tasks with TDD-first ordering. Use when asked to generate a spec, write a feature spec, create a plan from a spec, break down tasks, do spec-driven development, process a feature brief, create a task breakdown, do TDD task ordering, write acceptance criteria, check OSD compliance for a plan, or run any phase of the SDD pipeline. Also triggers for "spec-writer", "spec agent", "feature specification", "implementation plan from spec", and "task list from plan".
---

# SDD Workflow

You are executing ARUSHAI's Spec-Driven Development (SDD) workflow. This is a three-phase process that turns a founder's feature brief into a formal spec, an implementation plan, and a TDD-first task breakdown. Each phase has a gate where the founder must approve before you proceed.

The full process definition lives in OSD Section 4.13. This skill teaches you HOW to execute each phase well.

## The Operating Model

The founder operates as CTO — providing direction, constraints, and strategic intent. You operate as PM — translating intent into formal specifications. Build agents operate as engineers — executing approved tasks. The founder retains approval at every phase gate.

```
Founder writes Feature Brief (2-5 paragraphs)
  → You generate spec.md (founder reviews/approves)
    → You generate plan.md (founder reviews/approves)
      → You generate tasks.md (founder reviews/approves)
        → Build agents execute tasks one by one
```

## The #1 Rule

**ASK CLARIFYING QUESTIONS when the brief is ambiguous. Never assume.**

Re-state the problem in your own words and ask: "Is my understanding correct?" If anything is unclear, ask before proceeding. This is non-negotiable — it is the single most important behavior in this entire workflow.

If the brief is 2 sentences long, it is probably too short. Ask: "Can you expand on what success looks like?" and "What are you worried about?"

Do NOT proceed to the next phase if the current phase has unresolved questions. Flag unknowns as **NEEDS CLARIFICATION** and stop.

---

## Phase 1: Specify (Brief → spec.md)

Read the founder's feature brief. It captures intent in 2-5 paragraphs covering: what problem, what success looks like, constraints, out of scope, and concerns.

### How to generate a good spec

1. **Re-state the problem.** Write it in your own words. If your restatement doesn't match the founder's intent, you misunderstood something — ask.

2. **Write testable acceptance criteria.** Every criterion must be specific, measurable, and verifiable in a test.

   Bad acceptance criteria (vague, untestable):
   - "System should be fast"
   - "Handles errors gracefully"
   - "Good user experience"
   - "Data is secure"

   Good acceptance criteria (specific, testable):
   - "Query returns results in under 500ms for datasets up to 10K rows"
   - "All API endpoints return structured JSON error with `code`, `message`, and `request_id` for every failure path"
   - "Form validation shows inline error within 200ms of field blur, with specific message per validation rule"
   - "All PII fields encrypted at rest using AES-256; decryption requires authenticated session token"

   When you see a vague criterion, rewrite it with numbers and ask: "Is this what you meant?"

3. **Check dependencies against the actual codebase.** Use Read, Grep, and Glob to verify that assumed dependencies actually exist. Never claim "the auth module handles this" without checking that the auth module exists and does what you think.

4. **Document questions and answers.** Every question you asked and every answer the founder gave goes into a Questions/Clarifications table in the spec. This is an audit trail of intent — future readers need to understand WHY decisions were made, not just what was decided.

5. **Define out of scope explicitly.** If something is NOT in scope, say so. Ambiguous scope boundaries cause scope creep during build.

Use the template at `resources/spec-template.md`.

### Phase 1 output

Present spec.md to the founder. They will: approve, reject with notes, or request revisions. Do NOT proceed to Phase 2 until you have explicit approval.

---

## Phase 2: Plan (spec.md → plan.md)

Read the approved spec.md. Generate an implementation plan that maps the spec to concrete technical decisions.

### How to generate a good plan

1. **Propose architecture that fits existing patterns.** Use Grep and Glob to understand how the codebase is currently structured. Match the existing patterns — do not introduce new architectural patterns without explicit justification.

2. **Complete the OSD compliance table.** Map these four standards to specific approaches for this feature:

   | Standard | OSD Ref | Your Approach |
   |---|---|---|
   | Externalized configuration | 4.9.1 | How will this feature handle config? |
   | Structured logging | 4.9.2 | What will be logged and at what level? |
   | Testing | 4.9.4 | What test strategy? Unit, integration, E2E? |
   | Error handling | 4.9.5 | How will errors be caught, logged, and returned? |

   If you leave a row empty, the plan is incomplete. Every feature touches all four standards.

3. **Assess risks honestly.** Every plan has at least one risk. If you cannot identify any risks, you have not thought hard enough. Common risks: API changes in external dependencies, performance under load, data migration complexity, unclear requirements that were not fully clarified.

   | Risk | Likelihood | Impact | Mitigation |
   |---|---|---|---|
   | [Be specific] | Low/Medium/High | Low/Medium/High | [Concrete action] |

4. **List file impact with real paths.** Use Glob to verify that the files you plan to modify actually exist. List every file that will be created, modified, or deleted.

5. **Flag contradictions.** If anything in the plan contradicts the approved spec, STOP and flag it. Do not silently deviate from the spec.

Use the template at `resources/plan-template.md`.

### Phase 2 output

Present plan.md to the founder. They will: approve, reject with notes, or request revisions. Do NOT proceed to Phase 3 until you have explicit approval.

---

## Phase 3: Tasks (plan.md → tasks.md)

Read the approved plan.md. Generate a TDD-first task breakdown where each task maps to exactly one CC prompt.

### TDD-first ordering

The ordering is structural, not optional:

1. **Scaffold first** — directory structure, config files, boilerplate
2. **Test task before implementation task** — write the tests first
3. **Implementation task** — make the tests pass
4. **Integration tests after unit work** — test the pieces together
5. **Documentation last** — update docs after everything works

For every unit of work, the pattern is always:
```
T{N}:   Write tests for [component]
T{N+1}: Implement [component] — all tests from T{N} must pass
```

Never reverse this order. Never skip the test task.

### How to generate good tasks

1. **Each task = exactly one CC prompt.** If a task feels like it needs two CC prompts, split it into two tasks. The mapping is 1:1 — task IDs map directly to CC prompt IDs per AI Session Protocol Rule 15.

2. **Test tasks specify what to test.** Include: what behavior to test, expected outcomes, edge cases to cover, and approximate test count. "Write tests" is not a task — "Write 8 unit tests for the auth middleware covering: valid token, expired token, missing token, malformed token, rate limit exceeded, invalid scope, token refresh, and concurrent requests" is a task.

3. **Implementation tasks reference their tests.** Every implementation task must state: "All tests from T{NNN} must pass." This creates a hard dependency — you cannot claim implementation is complete unless the preceding tests pass.

4. **Size appropriately.** S = under 30 minutes, M = 30-90 minutes, L = over 90 minutes. If a task is L, consider splitting it. No task should be larger than L.

5. **Dependencies must be logical.** Each task lists what it depends on. The dependency chain must be sequential and make sense — you cannot test something that has not been scaffolded.

Example task sequence:

| ID | Task | Size | Depends On |
|---|---|---|---|
| T001 | Scaffold directory structure and config | S | — |
| T002 | Write unit tests for auth middleware (8 tests) | M | T001 |
| T003 | Implement auth middleware — all T002 tests must pass | M | T002 |
| T004 | Write integration tests for auth + API layer (5 tests) | M | T003 |
| T005 | Implement API endpoints — all T004 tests must pass | M | T004 |
| T006 | Update documentation and changelog | S | T005 |

Use the template at `resources/tasks-template.md`.

### Phase 3 output

Present tasks.md to the founder. They will: approve, reject with notes, or request revisions. Build agents begin execution only AFTER tasks.md is approved.

---

## Common Mistakes and How to Fix Them

| Mistake | Fix |
|---|---|
| Vague brief with no success criteria | Ask: "What does success look like in measurable terms?" |
| Untestable acceptance criteria | Rewrite with specific numbers, thresholds, or behaviors |
| Plan missing error handling approach | Add the OSD 4.9.5 compliance row — it is mandatory |
| Tasks without preceding test tasks | Add a test task before every implementation task |
| One massive L-sized task | Split into multiple S/M tasks with clear boundaries |
| Proceeding despite NEEDS CLARIFICATION | STOP. Ask the founder. Never assume. |
| Claiming a dependency exists without checking | Use Grep/Glob to verify it exists in the codebase |
| Plan contradicts approved spec | Flag it immediately — do not silently change direction |

---

## When This Process Is Required

| Change Type | Required? |
|---|---|
| New feature | Full SDD (brief → spec → plan → tasks) |
| Significant refactor (>3 files) | Full SDD |
| Bug fix (single file) | Exempt |
| Config change | Exempt |
| Documentation update | Exempt |
| Hotfix | Exempt (spec retroactively if systemic) |

**Threshold:** If work takes more than one CC prompt, it needs a brief and spec.

---

## Resource Templates

Use these templates for consistent output format:

- `resources/brief-template.md` — Feature Brief (founder fills this in)
- `resources/spec-template.md` — Spec document (Phase 1 output)
- `resources/plan-template.md` — Implementation plan (Phase 2 output)
- `resources/tasks-template.md` — Task breakdown (Phase 3 output)

Read the relevant template before generating each document.

---

## Reference

The authoritative source for this workflow is OSD Section 4.13 (Spec-Driven Feature Development). When in doubt, consult the OSD.
