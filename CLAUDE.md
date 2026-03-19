# CLAUDE.md — arushai-os

## Repo Purpose

This repo contains the ARUSHAI company operating system — strategic documents, operating protocols, and knowledge base. This is NOT a code repo.

## CC's Role

CC's role here is strictly documentation: writing, updating, and maintaining markdown documents with precision.

## Rules

- Never invent company strategy or decisions — only write what is explicitly instructed.
- Maintain consistent formatting across all documents.
- Use professional but clear language.
- No marketing fluff — every sentence must carry meaning.
- No emoji in headers or section titles.
- All documents must use clean, professional Markdown with proper heading hierarchy.
- Use explicit [TO BE COMPLETED] markers for unfinished sections — never use placeholder content that looks like real content.

## Available Skills

Repo-specific skills live in `.claude/skills/`. Reusable skills (shared across projects) live in `skills/`.

### Repo-Specific (.claude/skills/)

#### arushai-osd-writer

- **Location:** `.claude/skills/arushai-osd-writer/SKILL.md`
- **Use when:** Updating, expanding, or refining any section of the OSD (`docs/ARUSHAI_operating_system.md`).
- **Triggers:** "update OSD", "write section", "expand section", "operating system document", "company document"
- **Always use this skill when touching the OSD file.**

### Reusable (skills/)

#### arushai-project-scaffold

- **Location:** `skills/arushai-project-scaffold/SKILL.md`
- **Use when:** Scaffolding a new ARUSHAI repository following the ASPS standard.
- **Triggers:** "scaffold", "new project", "init project", "set up project structure", "setup SDD", "spec-driven project"
- **Always use this skill when initializing a new repo under arushai-hq/.**

#### cc-prompt-generator

- **Location:** `skills/cc-prompt-generator/SKILL.md`
- **Use when:** Creating a CC prompt for any ARUSHAI project.
- **Triggers:** "generate CC prompt", "create prompt", "write prompt for CC", "build instruction"
- **Always use this skill when the output is a CC prompt.**

#### forge-session-summarizer

- **Location:** `skills/forge-session-summarizer/SKILL.md`
- **Use when:** Converting raw FORGE session output into a structured, referenceable summary.
- **Triggers:** "summarize FORGE session", "create session summary", "archive session", "FORGE summary"
- **Always use this skill when archiving FORGE session results.**

#### sdd-workflow

- **Location:** `skills/sdd-workflow/SKILL.md`
- **Use when:** Executing the Spec-Driven Development workflow (brief -> spec -> plan -> tasks).
- **Triggers:** "generate spec", "feature spec", "create plan", "task breakdown", "SDD", "spec-driven"

#### osd-compliance

- **Location:** `skills/osd-compliance/SKILL.md`
- **Use when:** Checking code or plans against the 15 engineering standards.
- **Triggers:** "OSD compliance", "engineering standards", "compliance check", "standards audit", "quality gate"
