# ARUSHAI Systems Private Limited — Operating System

Company-level operating protocols, decision frameworks, and knowledge base for ARUSHAI Systems Private Limited.

This repo is the single source of truth for how ARUSHAI operates — from product development lifecycle to financial frameworks to AI agent governance.

## Overview

The ARUSHAI Operating System Document (OSD) defines the company's identity, decision-making frameworks, product development lifecycle, AI interaction protocols, context management, financial rules, security governance, and evolution roadmap.

Every ARUSHAI product repo and every future AI agent references this document as the company constitution.

## Document Index

- [ARUSHAI Operating System Document](docs/ARUSHAI_operating_system.md) — the core operating system document
- [Forge Sessions](docs/forge-sessions/) — research and discovery session summaries
  - [FORGE-001](docs/forge-sessions/FORGE-001-summary.md) — Foundations of Reasoning, Grounding & Engineering
- [Templates](docs/templates/) — standard templates used across ARUSHAI projects
  - [CC Prompt Template](docs/templates/cc-prompt-template.md) — the mandatory prompt format for all CC interactions

## How to Use

This document is referenced by all ARUSHAI product repos and will be referenced by future AI agents. Each product repo's CLAUDE.md points back to the relevant sections of the OSD for company-wide rules and protocols.

When onboarding a new product, a new agent, or a new team member, start here.

## Skills

Custom Claude Code skills installed in this repo for structured documentation workflows.

| Skill | Purpose |
|-------|---------|
| **arushai-osd-writer** | Write and update sections of the ARUSHAI Operating System Document. Enforces writing style, format, metadata updates, and quality checks. |
| **cc-prompt-generator** | Generate Claude Code prompts in ARUSHAI's standard format. Enforces the Branch/Context/What to Build/Acceptance Criteria structure. |
| **forge-session-summarizer** | Summarize FORGE research sessions into structured documents for the knowledge base. Enforces consistent summary structure and cross-referencing. |

Skills are defined in `.claude/skills/` and are automatically available to Claude Code when working in this repo.

## Contributing

- Only the founder updates strategic sections (company identity, vision, decision frameworks).
- CC updates operational sections via explicit prompts — never autonomously.
- All changes follow the CC prompt protocol defined in the OSD.
