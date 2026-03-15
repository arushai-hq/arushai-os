---
name: arushai-project-scaffold
description: Scaffolds a new ARUSHAI project following the ASPS (ARUSHAI Standard Project Structure). Use when creating a new project, initializing a repo, or when the user says "scaffold", "new project", "init project", or "set up project structure".
---

# ARUSHAI Project Scaffold Skill

Scaffold a new ARUSHAI repository following the ARUSHAI Standard Project Structure (ASPS).

Before scaffolding, read the latest ASPS specification. Look in `docs/standards/` for the highest versioned `ASPS-v*.md` file and follow its current structure for directory layout, CLAUDE.md templates, tier requirements, and agent architecture. If running outside the arushai-os repo, the ASPS spec lives at `arushai-hq/arushai-os/docs/standards/`.

## Step 1 — Gather Inputs

Ask the user for:

1. **Project name** — used for directory names, CLAUDE.md header, and living document filename.
2. **One-line description** — what the project does and its stack summary.
3. **Tech stack** — primary language/framework(s).
4. **Composition pattern** — A, B, C, or D (see pattern guide below).

**Pattern guide:**
- A — Single framework handles both FE and BE (e.g., Next.js)
- B — Core engine + supporting tools, same language (e.g., Python trading engine + CLI)
- C — Separate FE and BE stacks communicating over an API
- D — 3+ distinct components (FE + BE + CLI + workers)

## Step 2 — Determine Tier

Apply this logic:

- **LIGHT** — Documentation repos, simple tools, projects in their first week. No living document needed.
- **MEDIUM** — Active products with regular CC sessions. Living document + context archive required.
- **HEAVY** — Production systems with daily operations and complex CC workflows. Full CC infrastructure required.

Default to MEDIUM for Pattern A/B/C/D application repos unless the user specifies otherwise.

## Step 3 — Create Directory Structure

Create the directory tree for the selected pattern and tier. Reference the current ASPS spec Sections 5.1–5.4 for the exact structure per pattern.

Always create:
- `CLAUDE.md` (root)
- `README.md`
- `.claude/settings.json`
- `.claude/skills/` (empty, ready for skills)
- `docs/`
- `.gitignore`

Add for MEDIUM and HEAVY:
- `{project}_context.md`
- `docs/context_archive.md`

Add for HEAVY:
- `docs/decisions/`
- `docs/runbooks/`
- `.claude/hooks/bash/`

Add subdirectory `CLAUDE.md` files for each component directory (Pattern B/C/D).

## Step 4 — Generate Files

### Root CLAUDE.md
Use template: `.claude/skills/arushai-project-scaffold/resources/claude-md-template.md`
Replace all `{PLACEHOLDER}` variables with the project's actual values.
Hard ceiling: 200 lines.

### README.md
Professional overview: what the project is, stack summary, how to run it, link to CLAUDE.md for CC context.

### Subdirectory CLAUDE.md files (Pattern B/C/D)
Use template: `.claude/skills/arushai-project-scaffold/resources/sub-claude-md-template.md`
Each subdirectory CLAUDE.md must include explicit skill routing — which skills CC should use when working in that directory.
Hard ceiling: 150 lines per subdirectory CLAUDE.md.

### {project}_context.md (MEDIUM and HEAVY only)
Use template: `.claude/skills/arushai-project-scaffold/resources/context-md-template.md`
Fill in known values; leave unknowns as `[TO BE COMPLETED]`.

### .claude/settings.json
```json
{
  "permissions": {
    "allow": [],
    "deny": []
  }
}
```

### .gitignore
Use template: `.claude/skills/arushai-project-scaffold/resources/gitignore-template`

### docs/context_archive.md (MEDIUM and HEAVY only)
```markdown
# {Project} — Context Archive

Append-only. Resolved TODOs and older session log rows are moved here.
Never edit existing entries.
```

## Step 5 — Scaffold Agents (MEDIUM and HEAVY only)

Per the ASPS Agent Architecture Standard, set up the agent layer.

### For MEDIUM tier:

1. Create `.claude/agents/` directory.
2. Create `.claude/agents/code-reviewer.md` using template: `.claude/skills/arushai-project-scaffold/resources/code-reviewer-template.md`. This is mandatory for all MEDIUM and HEAVY projects.

### For HEAVY tier:

1. Everything from MEDIUM above.
2. Ask the user which project-specific agent roles are needed. Present these options from ASPS Section 7.5:
   - mobile-developer
   - frontend-developer
   - backend-developer
   - api-architect
   - ai-engineer
   - qa-tester
   - devops-engineer
3. For each selected role, create `.claude/agents/{role}.md` using template: `.claude/skills/arushai-project-scaffold/resources/agent-template.md`. Replace all `{PLACEHOLDER}` variables with the role's appropriate values. Set tool permissions per ASPS Section 7.8.

Maximum: 4-5 agents per project (including code-reviewer). If the user selects more, advise converting the excess to skills instead.

## Step 6 — Commit

```
chore: scaffold {project-name} — ASPS {pattern} / {tier}
```

## Quality Check

Before finishing, verify:
- Root CLAUDE.md is under 200 lines
- Each subdirectory CLAUDE.md is under 150 lines
- All `{PLACEHOLDER}` variables have been replaced with real values
- No `[TO BE COMPLETED]` markers remain unless the content is genuinely unknown
- `.gitignore` includes `.claude/settings.local.json`, `.claude/CLAUDE.md`, `.env`, `logs/`
