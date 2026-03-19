# ASPS Sync Checklist

Use this checklist when a new ASPS version is released. Ensures all dependent artifacts stay aligned with the current specification.

---

## 1. Scaffold Skill

- [ ] `skills/arushai-project-scaffold/SKILL.md` — Verify the dynamic ASPS reader instruction still points to the correct `docs/standards/` path
- [ ] Verify all Step references match current ASPS section numbers (directory structure, tier requirements, agent architecture)
- [ ] Review resource templates for consistency with the latest ASPS templates:
  - [ ] `resources/claude-md-template.md` — matches ASPS Root CLAUDE.md Template
  - [ ] `resources/sub-claude-md-template.md` — matches ASPS Subdirectory CLAUDE.md Template
  - [ ] `resources/context-md-template.md` — matches ASPS Living Document Structure
  - [ ] `resources/gitignore-template` — matches ASPS .gitignore Standard
  - [ ] `resources/agent-template.md` — matches ASPS Agent File Format (Section 7.6)
  - [ ] `resources/code-reviewer-template.md` — matches ASPS Mandatory Agent spec (Section 7.4) and covers all 15 Engineering Standards (OSD Section 4.9)
  - [ ] `resources/config-default-template.yaml` — matches ASPS Config Directory standard (Section 9.4)
  - [ ] `resources/secrets-example-template.yaml` — matches ASPS Config Directory standard (Section 9.4)
- [ ] Verify tier requirements in SKILL.md match ASPS tier system (what is required at LIGHT/MEDIUM/HEAVY)
- [ ] Verify composition patterns in SKILL.md match ASPS patterns (A/B/C/D directory structures)

## 2. Global Skill Copy

- [ ] Re-copy updated scaffold skill from `skills/arushai-project-scaffold/` to target projects after changes

## 3. OSD References

- [ ] `docs/ARUSHAI_operating_system.md` — Update any ASPS version references
- [ ] `README.md` — Update ASPS version in Document Index

## 4. Product Repos

For each repo in the Product Registry:

- [ ] Check if the repo's structure still aligns with the new ASPS pattern requirements
- [ ] Check if the repo's CLAUDE.md references the correct ASPS version
- [ ] Check if the repo's agent setup matches the new agent architecture requirements (if applicable)

## 5. Verification

- [ ] Run the scaffold skill in a test directory to verify it produces a valid structure
- [ ] Verify the generated CLAUDE.md is under 200 lines
- [ ] Verify the generated subdirectory CLAUDE.md files are under 150 lines each
- [ ] Verify no `{PLACEHOLDER}` variables remain in generated output (except genuinely unknown values marked `[TO BE COMPLETED]`)

---

*Use this checklist as a PR template or session task list whenever ASPS is versioned up.*
