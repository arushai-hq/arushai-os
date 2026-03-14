# CC Prompt Template

This is the standard CC prompt format used across all ARUSHAI projects. This format is mandatory for all ARUSHAI projects. CC prompts must never contain actual code — only instructions.

## Template

```
CC PROMPT — [Brief Title]

Branch: [target branch — always explicit]

Skills: [list any CC skills to activate, if applicable]

Context:
[Reference to the relevant living document, OSD section, or prior session summary.
Provide enough context for CC to understand the current state without re-reading everything.]

What to Build:
[Clear description of the intent and requirements.
Describe what needs to happen, not how to implement it.
Never include actual code — only instructions.]

Acceptance Criteria:
[Measurable outcomes that define "done." Each criterion should be verifiable.]

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

Do Not:
[Explicit exclusions — things CC must avoid doing in this task.]

- Do not ...
- Do not ...

When Done:
[Post-completion steps — what to update after the task is finished.]

- Update README if applicable
- Update the relevant context/living document
- Run tests if applicable
```

## Rules

- **Branch is always explicit.** Never assume a branch — every prompt specifies where the work happens.
- **No code in prompts.** Prompts describe intent and requirements. CC determines the implementation.
- **Context is mandatory.** Every prompt references the relevant living document or OSD section so CC has the right frame of reference.
- **Acceptance criteria are measurable.** Vague criteria like "works correctly" are not acceptable. Each criterion must be independently verifiable.
- **Do Not section prevents scope creep.** Explicitly state what CC should avoid to keep the task focused.
- **When Done ensures continuity.** Every task ends with documentation and validation steps so context is never lost.
