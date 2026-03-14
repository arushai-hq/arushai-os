---
name: cc-prompt-generator
description: Generate Claude Code prompts in ARUSHAI's standard format. Use this skill whenever creating a CC prompt for any ARUSHAI project. Triggers: "generate CC prompt", "create prompt", "write prompt for CC", "build instruction". Always use this skill when the output is a CC prompt.
---

# CC Prompt Generator

## Prompt Structure

Every CC prompt follows this exact structure, in this order:

1. **Branch** — Always explicit, never assumed.
2. **Skills to activate** — List any CC skills relevant to the task.
3. **Context** — Reference to the relevant living document or OSD section. Provide enough context for CC to understand the current state.
4. **What to build** — Intent and requirements only. NEVER include actual code, function bodies, or implementation details.
5. **Acceptance criteria** — Measurable outcomes that define "done." Each criterion must be independently verifiable.
6. **Do not** — Explicit exclusions to prevent scope creep.
7. **When done** — Post-completion steps: update README, update context doc, run tests.

## Rules

- Never include code blocks, function bodies, or implementation details in prompts. CC has its own skills and project context to write code. Prompts are instruction-only.
- The prompt must specify which git branch to work on. If a new branch is needed, include the branch creation command.
- Always include a requirement to update README.md and the product's living document as part of "When done."
- Keep prompts token-efficient — no redundant explanation, no restating what CC already knows from its CLAUDE.md and skills.
- Reference the template at `docs/templates/cc-prompt-template.md` for the canonical format.
