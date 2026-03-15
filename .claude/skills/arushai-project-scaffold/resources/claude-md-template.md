# {PROJECT_NAME}

## What
{DESCRIPTION}. Stack: {STACK}. Repo: arushai-hq/{REPO_NAME}.

## Commands
```
{BUILD_COMMAND}
{TEST_COMMAND}
{LINT_COMMAND}
{RUN_COMMAND}
```

## Structure
```
{DIRECTORY_MAP}
```

## Rules
- {RULE_1}
- {RULE_2}
- Branch discipline: feature branches off main, PR or direct push per OSD Section 4.
- Commit convention: type(scope): description (feat, fix, docs, chore, refactor, test).

## Skills

| Skill | Use when |
|---|---|
| {SKILL_NAME} | {SKILL_TRIGGER} |

## Do Not
- Do not commit secrets, .env files, or credentials.
- Do not push directly to main without testing locally.
- Do not invent requirements — only implement what is explicitly specified.

## Deep Context
- For project state and open tasks: `{PROJECT_NAME}_context.md`
- For architecture patterns: `.claude/skills/{PROJECT_NAME}-architecture/`
- For company-wide rules: `arushai-hq/arushai-os` → `docs/ARUSHAI_operating_system.md`
- For project structure standard: `docs/standards/ASPS-v1.0.0.md`
