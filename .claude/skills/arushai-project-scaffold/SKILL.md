---
name: arushai-project-scaffold
description: Scaffolds a new ARUSHAI project following the ASPS (ARUSHAI Standard Project Structure). Use when creating a new project, initializing a repo, or when the user says "scaffold", "new project", "init project", or "set up project structure".
---

# ARUSHAI Project Scaffold Skill

Scaffold a new ARUSHAI repository following ASPS v1.0.0.

Full specification: `docs/standards/ASPS-v1.0.0.md`. Load it for complete details on patterns, tiers, templates, and gitignore rules.

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

Create the directory tree for the selected pattern and tier. Reference `docs/standards/ASPS-v1.0.0.md` Sections 5.1–5.4 for the exact structure per pattern.

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

## Step 5 — Commit

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
