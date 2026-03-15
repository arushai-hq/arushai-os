# ARUSHAI Standard Project Structure (ASPS) v1.2.0

**Version:** 1.2.0
**Date:** 2026-03-15
**Status:** Locked
**Author:** ARUSHAI Systems Private Limited
**Session:** ARUSHAI-FORGE-002

---

## 1. Purpose

This document defines the standard folder structure, CC (Claude Code) configuration, and context management patterns for all repositories under `arushai-hq/`. Every new project MUST follow this standard. Existing projects SHOULD be migrated when a maintenance window allows.

The goals are:
- Every CC session starts fully oriented within 30 seconds of reading CLAUDE.md
- Context tokens are minimized through progressive disclosure
- Skills, hooks, and agents are scoped correctly so CC loads only what's relevant
- Any ARUSHAI contributor (human or AI) can navigate any repo using the same mental model

---

## 2. Design Principles

### 2.1 Progressive Disclosure, Not Progressive Bloat
CC should load the minimum context needed. CLAUDE.md is the map, not the encyclopedia. Skills hold domain knowledge. Docs hold the deep reference. Nothing loads until needed.

### 2.2 Two Audiences
Every project has two consumers — CC (needs machine-parseable context) and the human (needs readable docs). These overlap at CLAUDE.md and README.md but diverge after that.

### 2.3 Separation of Concerns in the .claude/ Layer
- Skills = knowledge (what CC should know)
- Hooks = automation (what CC must always do)
- Agents = delegation (who CC can spawn)
- Commands = shortcuts (what the human triggers)
These are distinct — never mix them.

### 2.4 Living Documents Over Static Docs
The `{project}_context.md` rolling-window living document is the source of truth for current state. README.md is the snapshot for humans. Context archive holds resolved history.

### 2.5 CLAUDE.md Under 200 Lines
CLAUDE.md gets loaded every single session. Every line costs tokens on every prompt. The hard ceiling is 200 lines. Everything else uses progressive disclosure via skills or docs references.

### 2.6 Subdirectory CLAUDE.md as Skill Router
Each component directory (frontend/, backend/, cli/, etc.) gets its own CLAUDE.md that is lazy-loaded only when CC touches files in that directory. This CLAUDE.md explicitly instructs CC which skills to use, providing automatic skill routing without wasting context on irrelevant components.

---

## 3. The CC Configuration Layer (.claude/)

Every ARUSHAI repo has a `.claude/` directory at the project root containing CC's configuration. This follows the 4-Layer Architecture:

| Layer | Location | When Loaded | Token Cost |
|---|---|---|---|
| L1: CLAUDE.md | Project root | Every session start | Always (keep <200 lines) |
| L2: Skills | .claude/skills/ | On-demand (description only at startup) | ~98% savings vs CLAUDE.md |
| L3: Hooks | .claude/hooks/ | Always (shell scripts, zero LLM tokens) | Zero context cost |
| L4: Agents | .claude/agents/ | Only when spawned | Separate context window |

### 3.1 Standard .claude/ Structure

```
.claude/
├── settings.json              # Permissions, hooks config, env vars
├── settings.local.json        # Personal overrides (gitignored)
├── CLAUDE.md                  # Personal project overrides (gitignored)
├── skills/                    # L2: Domain knowledge modules
│   ├── {skill-name}/
│   │   ├── SKILL.md           # <500 lines, high-level instructions
│   │   ├── resources/         # Deep reference (loaded on-demand only)
│   │   └── scripts/           # Deterministic scripts (only output enters context)
├── hooks/                     # L3: Automation scripts
│   └── bash/
├── agents/                    # L4: Subagent definitions
└── commands/                  # Slash commands
```

### 3.2 Skill Naming Convention

Skills are named with a prefix that indicates their scope:

- `{project}-*` — Project-wide skills (e.g., `tradeos-architecture`, `flint-conventions`)
- `frontend-*` — Frontend component skills (e.g., `frontend-patterns`)
- `backend-*` — Backend component skills (e.g., `backend-patterns`)
- `docker-*` — Infrastructure/deployment skills (e.g., `docker-deploy`)

The YAML `description` field in each SKILL.md must include keywords that indicate when CC should activate the skill. This is the primary mechanism for automatic skill invocation.

### 3.3 Skill Size Limits

- SKILL.md body: <500 lines
- If content exceeds 500 lines, split into `resources/` subdirectory files
- Resources are loaded on-demand only when SKILL.md references them
- Scripts in `scripts/` are executed via bash; only their output enters context

---

## 4. The CLAUDE.md Standard

### 4.1 Root CLAUDE.md Template

Every project root CLAUDE.md follows this structure:

```markdown
# {PROJECT_NAME}

## What
{One-line description. Stack summary. Repo URL.}

## Commands
{build, test, lint, run — essential commands only, no explanations}

## Structure
{5-10 line directory map — what's where. Component map for multi-component projects.}

## Rules
{Project-specific rules CC must follow. Branch discipline, commit conventions, etc.}

## Skills
{Table: skill name → one-line description of when to use it.
CC uses this to know what's available without loading full skill content.}

## Do Not
{3-5 lines of things CC must never do in this project.}

## Deep Context
{Pointers to living document, skills, and docs for deeper information.
Format: "For X, read path/to/file.md"}
```

Hard ceiling: 200 lines. If the root CLAUDE.md exceeds 200 lines, content must be moved to skills or docs.

### 4.2 Subdirectory CLAUDE.md Template

Each component directory (frontend/, backend/, core/, cli/, docker/) gets its own CLAUDE.md:

```markdown
# {Component Name} — {Framework/Stack}

## Skills
When working in this directory, use these skills:
- {skill-name} — {when to use}
- {skill-name} — {when to use}

## Commands
{Component-specific build/test/lint commands}

## Conventions
{Component-specific patterns, naming, style rules}

## Gotchas
{Non-obvious things CC gets wrong in this component}
```

These are lazy-loaded — CC only reads them when touching files in that directory. This provides automatic context scoping and skill routing.

Hard ceiling: 150 lines per subdirectory CLAUDE.md.

### 4.3 CLAUDE.md Hierarchy

```
~/.claude/CLAUDE.md           → Global ARUSHAI preferences (all projects)
./CLAUDE.md                   → Project root (committed to git, shared)
./.claude/CLAUDE.md           → Personal overrides (gitignored)
./frontend/CLAUDE.md          → Frontend component (lazy-loaded)
./backend/CLAUDE.md           → Backend component (lazy-loaded)
./core/CLAUDE.md              → Core engine (lazy-loaded)
./docker/CLAUDE.md            → Infrastructure (lazy-loaded)
```

Later/deeper files append to context — they do not override parent files.

---

## 5. Application Composition Patterns

ARUSHAI projects follow one of four composition patterns based on their architecture. The pattern determines which top-level directories exist.

### 5.1 Pattern A: Single-Stack App

For projects where one framework handles both frontend and backend (e.g., Next.js App Router).

```
project/
├── CLAUDE.md
├── README.md
├── .claude/
│   └── skills/
├── app/                    # Framework-specific (e.g., Next.js App Router)
├── components/             # UI components
├── lib/                    # Shared utilities
├── public/                 # Static assets
├── config/
├── docs/
└── tests/
```

Examples: Flint (Next.js 14)

### 5.2 Pattern B: Engine + Tools

For projects with a core engine/service plus auxiliary tools, scripts, and CLI — typically single-language.

```
project/
├── CLAUDE.md
├── README.md
├── {project}_context.md
├── .claude/
│   └── skills/
├── core/                   # Core engine modules
│   ├── CLAUDE.md           # Engine-specific context + skill routing
│   └── {module}/
├── tools/                  # CLI tools, reports, utilities
│   └── CLAUDE.md
├── scripts/                # Automation scripts
├── bin/                    # CLI entry points
├── config/
├── docker/
│   ├── CLAUDE.md
│   └── docker-compose.yml
├── docs/
│   ├── context_archive.md
│   ├── decisions/
│   ├── runbooks/
│   └── specs/
├── tests/
│   ├── unit/
│   └── integration/
└── logs/                   # Runtime (gitignored)
```

Examples: TradeOS (Python trading engine + CLI + tools)

### 5.3 Pattern C: Frontend + Backend

For projects with distinct frontend and backend technology stacks communicating over an API.

```
project/
├── CLAUDE.md               # Project overview + component map
├── README.md
├── {project}_context.md
├── .claude/
│   └── skills/
├── frontend/
│   ├── CLAUDE.md           # Frontend conventions + skill routing
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   └── utils/
│   ├── public/
│   ├── tests/
│   └── package.json
├── backend/
│   ├── CLAUDE.md           # Backend conventions + skill routing
│   ├── src/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── middleware/
│   │   └── utils/
│   ├── tests/
│   └── package.json (or requirements.txt)
├── shared/                 # Cross-component types, constants
│   ├── CLAUDE.md
│   └── types/
├── docker/
│   ├── CLAUDE.md
│   ├── docker-compose.yml
│   └── nginx/
├── config/
├── docs/
│   ├── context_archive.md
│   └── decisions/
└── tests/
    └── e2e/                # End-to-end tests spanning components
```

Examples: VIZBOARD (React frontend + Node.js backend)

### 5.4 Pattern D: Full Platform

For complex projects combining multiple components: frontend, backend, CLI, worker services, and shared packages.

```
project/
├── CLAUDE.md
├── README.md
├── {project}_context.md
├── .claude/
│   └── skills/
├── frontend/
│   ├── CLAUDE.md
│   └── src/
├── backend/
│   ├── CLAUDE.md
│   └── src/
├── cli/
│   ├── CLAUDE.md
│   └── src/
├── workers/
│   ├── CLAUDE.md
│   └── src/
├── shared/
│   ├── CLAUDE.md
│   ├── types/
│   └── utils/
├── docker/
│   ├── CLAUDE.md
│   └── docker-compose.yml
├── tools/
├── config/
├── docs/
│   ├── context_archive.md
│   ├── decisions/
│   ├── runbooks/
│   └── specs/
└── tests/
```

Examples: Future TradeOS with dashboard, future SaaS products

### 5.5 Pattern Selection Guide

| Question | If Yes → |
|---|---|
| Single framework handles both FE and BE? | Pattern A |
| Core engine + supporting tools, same language? | Pattern B |
| Separate FE and BE stacks? | Pattern C |
| 3+ distinct components (FE + BE + CLI + workers)? | Pattern D |

Start with the simplest pattern that fits. Upgrade when complexity demands it.

---

## 6. Tier System

Projects are tiered by CC complexity. The tier determines which elements of the standard are required vs optional.

### 6.1 Tier 1: LIGHT

For documentation repos, simple tools, and projects in their first week.

**Required:** CLAUDE.md (<100 lines), README.md, .claude/settings.json, 0-3 skills
**Optional:** Everything else
**No living document needed** — sessions are short, context resets aren't painful.

Upgrade trigger: 5+ CC sessions on the project, or re-explaining context to CC repeatedly.

### 6.2 Tier 2: MEDIUM

For active products with regular CC sessions.

**Required:** CLAUDE.md (<150 lines), README.md, {project}_context.md, .claude/skills/ (3-10 skills), docs/context_archive.md, config/ (with default.yaml and README.md)
**Optional:** hooks, agents, commands, docs/decisions/, subdirectory CLAUDE.md files
**Living document active.** Context archive active.

Upgrade trigger: 10+ skills, subagent needs, or daily operational workflows.

### 6.3 Tier 3: HEAVY

For production systems with daily operations and complex CC workflows.

**Required:** CLAUDE.md (<200 lines), README.md, {project}_context.md, .claude/skills/ (10-25 skills), .claude/hooks/, docs/context_archive.md, docs/decisions/, docs/runbooks/, subdirectory CLAUDE.md files for each component, config/ (with default.yaml, README.md, and domain-specific configs)
**Optional:** .claude/agents/, .claude/commands/, docs/specs/
**Full CC infrastructure.** All progressive disclosure patterns active.

---

## 7. Agent Architecture Standard

### 7.1 Purpose

Subagents are specialized CC instances that handle specific types of tasks in their own isolated context window. Each agent has a custom system prompt, specific tool permissions, and returns results to the main CC session without polluting its context.

Agents are workers. Skills are knowledge. Agents reference skills for domain expertise — never duplicate knowledge in agent prompts.

### 7.2 Agent vs Skill Decision Rule

Use an **agent** when: the role requires a distinct worker with its own context window, specific tool permissions, and a focused system prompt. Agents perform work — they write code, review code, run tests, or build architecture.

Use a **skill** when: the knowledge is reference material that any agent (or the main CC session) might need. Skills provide expertise — conventions, patterns, gotchas, checklists. Skills are loaded on-demand by whoever needs them.

Example: "UX design expert" is a skill (`hulmi-ux-patterns`) that the `mobile-developer` agent loads when building UI. "Security expert" is a skill (`project-security`) that the `code-reviewer` agent uses during review. Do not create standalone agents for knowledge that should be skills.

### 7.3 Agent Selection by Tier

| Tier | Agent Requirement |
|---|---|
| LIGHT | None — single CC session is sufficient |
| MEDIUM | code-reviewer (mandatory) + 1-2 project-specific agents |
| HEAVY | code-reviewer (mandatory) + 2-3 project-specific agents + optional qa-tester |

Maximum: 4-5 agents per project. Research shows that more than this decreases productivity rather than increasing it. If you think you need more agents, the excess should probably be skills instead.

### 7.4 Mandatory Agent: code-reviewer

Every MEDIUM and HEAVY tier project MUST have a `code-reviewer` agent. This is the quality gate.

**Configuration:**
- **Tools:** Read, Grep, Glob (read-only — cannot modify code)
- **Model:** sonnet (or inherit)
- **Invocation:** After every code change, before commit
- **References:** project security skill, project conventions skill

The code-reviewer agent enforces: code quality, security patterns, ARUSHAI conventions, test coverage expectations, and documentation completeness.

### 7.5 Project-Specific Agent Selection

Agents are selected based on the project's composition pattern and tech stack. Common agent roles:

| Agent Role | When to Use | Typical Tools |
|---|---|---|
| mobile-developer | Projects with React Native or mobile apps | Read, Write, Edit, Bash, Grep, Glob |
| frontend-developer | Projects with web frontends (React, Next.js) | Read, Write, Edit, Bash, Grep, Glob |
| backend-developer | Projects with server-side code (Node, Python) | Read, Write, Edit, Bash, Grep, Glob |
| api-architect | Projects with complex API or database layers | Read, Write, Edit, Bash, Grep, Glob |
| ai-engineer | Projects with AI/ML pipelines, embeddings, prompts | Read, Write, Edit, Bash, Grep, Glob |
| qa-tester | Projects requiring systematic test coverage | Read, Write, Edit, Bash, Grep, Glob |
| devops-engineer | Projects with complex deployment infrastructure | Read, Write, Edit, Bash, Grep, Glob |

Not every project needs every role. Select based on actual stack complexity.

### 7.6 Agent File Format

Agents are defined as Markdown files with YAML frontmatter in `.claude/agents/`:

```
.claude/agents/
├── code-reviewer.md         # Mandatory quality gate
├── {role-1}.md              # Project-specific
├── {role-2}.md              # Project-specific
└── {role-3}.md              # Project-specific (if needed)
```

Each agent file follows this structure:

```markdown
---
name: {agent-name}
description: {When this agent should be invoked. Include keywords for auto-detection.}
tools: {Comma-separated list of allowed tools}
model: sonnet
---

You are a {role description}.

Before starting work, read these skills:
- .claude/skills/{relevant-skill}/SKILL.md

When working on this project:
1. {Rule 1}
2. {Rule 2}
...
```

### 7.7 Agent-Skill Relationship

Agents reference skills for domain knowledge. This keeps agent prompts focused on workflow and behavior while skills hold the reusable expertise.

**Pattern:**
- **Agent prompt:** defines the workflow, tool permissions, and behavioral rules
- **Referenced skills:** provide domain knowledge, conventions, patterns, and checklists
- **Resources within skills:** deep reference material loaded only when needed

**Example mapping:**

| Agent | References Skill |
|---|---|
| mobile-developer | hulmi-ux-patterns |
| api-architect | hulmi-data-model |
| ai-engineer | hulmi-ai-pipeline |
| code-reviewer | hulmi-security |

### 7.8 Tool Permission Principle

Every agent gets the minimum tools necessary for its role:

| Agent Type | Tools |
|---|---|
| Read-only agents (reviewers, auditors) | Read, Grep, Glob |
| Research agents (analysts) | Read, Grep, Glob, WebFetch, WebSearch |
| Code-writing agents (developers, engineers) | Read, Write, Edit, Bash, Grep, Glob |
| Documentation agents | Read, Write, Edit, Grep, Glob, WebFetch, WebSearch |

Never give write access to review-only agents. Never give web access to agents that do not need external information.

---

## 8. Living Document Standard

Projects at MEDIUM and HEAVY tiers maintain a `{project}_context.md` at the repo root.

### 8.1 Structure

```markdown
# {Project} — Context

## Project Overview
{One-liner}

## Architecture
{Module/component table}

## Current State
{What's working, test count, active branch}

## Key Decisions
{Permanent — numbered list of locked decisions}

## Known TODOs
{Open items only — resolved move to archive}

## Immediate Next Actions
{Prioritized list}

## Session Rules
{Permanent rules that apply across all sessions}

## Session Log
{Last 5 sessions — date, summary, outcome}

## Last Updated
{Date + summary of last change}
```

### 8.2 Hygiene Rules

- Rolling window: keep last 5 session log rows; older rows move to context_archive.md
- Completed TODOs: move to context_archive.md after 2 sessions
- Key Decisions and Session Rules: stay permanently
- Context archive is append-only, never edited
- Every concluded discussion triggers a CC prompt to apply a delta update before moving on

---

## 9. Documentation Standard

### 9.1 Required Files (All Tiers)

| File | Purpose | Audience |
|---|---|---|
| CLAUDE.md | CC's entry point — project map + rules | CC |
| README.md | Human-readable project overview | Human |

### 9.2 Additional Files by Tier

| File/Directory | LIGHT | MEDIUM | HEAVY |
|---|---|---|---|
| {project}_context.md | — | Required | Required |
| docs/context_archive.md | — | Required | Required |
| config/ (default.yaml + README.md) | — | Required | Required |
| docs/decisions/ | — | Optional | Required |
| docs/runbooks/ | — | — | Required |
| docs/specs/ | — | — | Optional |
| Subdirectory CLAUDE.md | — | Optional | Required (per component) |

### 9.3 Architecture Decision Records (ADRs)

Stored in `docs/decisions/` with format: `{NNN}-{short-name}.md`

Structure:
```markdown
# {NNN}: {Decision Title}

**Date:** YYYY-MM-DD
**Status:** Accepted | Superseded by {NNN}

## Context
{What prompted this decision}

## Decision
{What was decided and why}

## Consequences
{What follows from this decision — positive and negative}
```

### 9.4 Code Standards Cross-Reference

All ARUSHAI projects must follow the Code Standards defined in OSD Section 4.9. The three non-negotiable principles are:

1. **Externalized Configuration** — No hardcoded configurable values. Application defaults in `config/`, secrets in `.env`.
2. **Structured Logging from Day One** — JSON logs, log levels, correlation IDs, timed external calls. No bare `console.log` or `print()` in production code.
3. **Config Directory** — Every MEDIUM and HEAVY project has a `config/` directory with `default.yaml`, `secrets.yaml` (gitignored), and `README.md`.

The `config/` directory is already included in all composition patterns (Sections 5.1–5.4) and is enforced in the `.gitignore` standard (Section 10). The scaffold skill creates the initial config directory structure with template files.

### 9.5 Diagram-First Principle

All significant documents must include Mermaid diagrams per the OSD Diagram-First Documentation principle (OSD Section 5.8). Workflows get flowcharts. Architectures get structural diagrams. Data flows get sequence diagrams. Diagrams go at the top of the relevant section, before the prose explanation.

---

## 10. .gitignore Standard

Every ARUSHAI repo includes these patterns:

```gitignore
# CC personal overrides
.claude/settings.local.json
.claude/CLAUDE.md

# Secrets
config/secrets.yaml
.env
.env.*

# Runtime
logs/
*.log
__pycache__/
node_modules/
.venv/
dist/
build/

# OS
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
```

---

## 11. Current Repo Mapping

| Repo | Pattern | Tier | Status |
|---|---|---|---|
| arushai-hq/tradeOS | B (Engine + Tools) | HEAVY | ~80% aligned, needs core/ restructure |
| arushai-hq/flint-app | A (Single-Stack) | MEDIUM | ~30% aligned, needs living doc + skills |
| arushai-hq/VizBoard | C (Frontend + Backend) | MEDIUM | ~30% aligned, needs restructure + living doc |
| arushai-hq/hulmi | A (Single-Stack) | MEDIUM | Scaffolded, PRD v1.1 locked |
| arushai-hq/arushai-os | Documentation | LIGHT | ~60% aligned, verify CLAUDE.md |

---

## 12. Version History

| Version | Date | Changes |
|---|---|---|
| 1.0.0 | 2026-03-15 | Initial release. Locked in FORGE-002. |
| 1.1.0 | 2026-03-15 | Added Section 7: Agent Architecture Standard — mandatory code-reviewer, tier-based selection, agent-skill relationship pattern, tool permission principle. |
| 1.2.0 | 2026-03-15 | Added Section 9.4: Code Standards cross-reference. config/ added to MEDIUM and HEAVY tier requirements. Documentation Standard table updated. Repo mapping includes HULMI. |

---

*ARUSHAI Systems Private Limited — arushai.com*
