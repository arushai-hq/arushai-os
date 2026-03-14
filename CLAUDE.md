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

Custom skills are defined in `.claude/skills/`. Use these skills when their trigger conditions are met.

### arushai-osd-writer

- **Location:** `.claude/skills/arushai-osd-writer/SKILL.md`
- **Use when:** Updating, expanding, or refining any section of the OSD (`docs/ARUSHAI_operating_system.md`).
- **Triggers:** "update OSD", "write section", "expand section", "operating system document", "company document"
- **Always use this skill when touching the OSD file.**

### cc-prompt-generator

- **Location:** `.claude/skills/cc-prompt-generator/SKILL.md`
- **Use when:** Creating a CC prompt for any ARUSHAI project.
- **Triggers:** "generate CC prompt", "create prompt", "write prompt for CC", "build instruction"
- **Always use this skill when the output is a CC prompt.**

### forge-session-summarizer

- **Location:** `.claude/skills/forge-session-summarizer/SKILL.md`
- **Use when:** Converting raw FORGE session output into a structured, referenceable summary.
- **Triggers:** "summarize FORGE session", "create session summary", "archive session", "FORGE summary"
- **Always use this skill when archiving FORGE session results.**
