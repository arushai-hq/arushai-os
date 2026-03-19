# Plan: {Feature Name}

**Feature ID:** F{NNN}
**Date:** {date}
**Status:** Draft | Approved
**Spec Version:** {spec version or date approved}

---

## Technical Approach

{Describe how the feature will be built. Reference existing codebase patterns. Explain architectural decisions and why they fit.}

## OSD Compliance Check

| Standard | OSD Ref | Approach |
|---|---|---|
| Externalized configuration | 4.9.1 | {How this feature handles config — env vars, config files, defaults} |
| Structured logging | 4.9.2 | {What will be logged, at what level, structured format} |
| Testing | 4.9.4 | {Test strategy — unit, integration, E2E, approximate test count} |
| Error handling | 4.9.5 | {How errors are caught, logged, and returned to callers} |

## Risk Assessment

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| {Specific risk description} | Low/Medium/High | Low/Medium/High | {Concrete mitigation action} |

## Research Items

Items flagged as needing investigation before or during build.

- [ ] {NEEDS CLARIFICATION: description}
- [ ] {NEEDS CLARIFICATION: description}

If any research items are unresolved, this plan is not ready for approval.

## File Impact

Files verified against codebase using Glob/Grep.

| Action | File Path | Notes |
|---|---|---|
| Create | {path} | {what this file does} |
| Modify | {path} | {what changes} |
| Delete | {path} | {why removed} |
