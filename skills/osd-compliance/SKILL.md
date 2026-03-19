---
name: osd-compliance
description: Verify code and plans against ARUSHAI's 15 non-negotiable engineering standards from OSD Section 4.9. Use when asked to check OSD compliance, verify engineering standards, run a compliance check, review code against standards, generate a compliance table for a plan, check quality gates, audit code quality, enforce coding standards, verify config externalization, check test coverage requirements, validate error handling patterns, assess production readiness standards, or do a standards review. Also triggers for "OSD 4.9", "engineering principles", "compliance audit", "standards checklist", "code quality gate", and "are we following the standards".
---

# OSD Compliance

You are verifying compliance against ARUSHAI's 15 non-negotiable engineering standards defined in OSD Section 4.9. These standards exist because HULMI shipped an entire MVP with zero tests and hardcoded config — they prevent expensive retrofits.

## Two Modes

### Mode 1: Plan Compliance

**When:** Generating or reviewing an implementation plan (SDD Phase 2).

Generate a compliance table mapping all applicable standards to the specific approach for this feature. This is the OSD compliance check required by Section 4.13.

Output format:

| Standard | OSD Ref | Approach | Status |
|---|---|---|---|
| Externalized configuration | 4.9.1 | [Specific approach for this feature] | Compliant / Gap / N/A |
| Structured logging | 4.9.2 | [What will be logged, at what level] | Compliant / Gap / N/A |
| ... | ... | ... | ... |

Every applicable standard must have a row. Empty rows = incomplete plan.

### Mode 2: Review Compliance

**When:** Reviewing code, PRs, or completed implementations.

Verify the code against each applicable standard using the checklists below. Report findings as:

| Standard | OSD Ref | Finding | Severity |
|---|---|---|---|
| [Standard name] | 4.9.X | [Specific finding with file:line] | Pass / Warning / Violation |

---

## The 15 Standards

Standards are organized into four groups. Use the verify checklist for each standard to check compliance.

### Foundation (Day-One Requirements)

#### 4.9.1 — Externalized Configuration

Every configurable value lives in config, never inline in code.

Verify:
- [ ] No hardcoded API keys, URLs, tokens, or thresholds in source files
- [ ] `config/` directory exists with `default.yaml` (committed) and `secrets.yaml` (gitignored)
- [ ] `.env.example` documents all required environment variables
- [ ] Runtime overrides via environment variables take precedence over config defaults
- [ ] No magic numbers or string constants that represent operational parameters

The test: can you change any operational parameter without editing application code?

#### 4.9.2 — Structured Logging from Day One

JSON-structured, leveled, contextual logging — no `console.log` or `print()` in production.

Verify:
- [ ] Logging framework initialized (not console.log/print)
- [ ] Log output is structured JSON
- [ ] Log levels used correctly: DEBUG, INFO, WARN, ERROR
- [ ] Log level configurable via environment variable
- [ ] Every log entry includes correlation ID for request tracing
- [ ] External API calls and database queries are timed and logged at INFO

The test: can you trace a single user request from entry to exit using only the logs?

#### 4.9.3 — Config Directory Standard

Standardized `config/` directory structure.

Verify:
- [ ] `config/default.yaml` exists with all non-secret defaults (committed)
- [ ] `config/secrets.yaml` is gitignored
- [ ] `config/README.md` documents every config key, type, default, and purpose
- [ ] Domain-specific configs split into separate files when complex (e.g., `ai.yaml`, `database.yaml`)
- [ ] New developer can clone and run with only defaults file

#### 4.9.4 — Testing: No Code Without Tests

The single most critical standard. Tests and code ship in the same commit.

Verify:
- [ ] Every function/endpoint/component with logic has at least one test
- [ ] Tests written BEFORE or ALONGSIDE code (TDD-first ordering in tasks)
- [ ] Test files mirror source structure (e.g., `src/auth.ts` -> `tests/auth.test.ts`)
- [ ] All tests pass — zero tolerance for failing tests
- [ ] Test pyramid followed: 70% unit, 20% integration, 10% E2E
- [ ] Coverage meets tier requirement: MEDIUM = business logic + API; HEAVY = 80% line coverage

The test: does every CC build prompt include testing requirements and expected test count?

#### 4.9.5 — Error Handling: Standardized Patterns

Every failure path handled explicitly. No swallowed exceptions. No silent failures.

Verify:
- [ ] Every function that can fail handles failure with meaningful error messages
- [ ] Typed/structured errors used — not generic strings
- [ ] API error responses follow standard format: `{ error: { code, message, details, request_id } }`
- [ ] No internal stack traces or file paths exposed in API responses
- [ ] All caught exceptions logged at ERROR level with full context
- [ ] External service calls have timeout + retry + fallback logic
- [ ] Stack-specific: Python = custom exception hierarchy; TS = typed error classes; RN = ErrorBoundary

### Quality (Code Health)

#### 4.9.6 — Input Validation: Validate at Every Boundary

All external data validated before processing.

Verify:
- [ ] Schema validation library used (Zod/Joi for TS, Pydantic/marshmallow for Python)
- [ ] Validation happens at boundary — API route handler, webhook receiver, form submission
- [ ] Validates shape, type, range, and format
- [ ] Clear, specific validation error messages — not generic "invalid input"
- [ ] User-provided strings sanitized before database storage or display
- [ ] File uploads validate type, size, and content (not just extension)

#### 4.9.7 — Type Safety

Type systems catch errors at compile time, not runtime.

Verify:
- [ ] TypeScript: `strict: true` in tsconfig.json, no unexcused `any`
- [ ] Python: type hints on all function signatures, Pydantic models for data structures
- [ ] Database queries use typed ORM or parameterized query builder — no raw string SQL
- [ ] Config values loaded through typed schemas (Zod, Pydantic) that validate on startup
- [ ] Every `any` usage has a comment explaining why

#### 4.9.8 — DRY + Single Responsibility

No duplicated logic. Each unit does one thing.

Verify:
- [ ] No copy-pasted logic across files — shared logic extracted to utilities
- [ ] Functions with "and" in the name split into separate functions
- [ ] Functions under 40 lines — longer functions have sub-functions extracted
- [ ] Files under 200 lines — larger files split into focused modules
- [ ] YAGNI: no speculative features built for hypothetical future requirements

#### 4.9.9 — Dependency Management: Pin and Audit

All third-party dependencies version-pinned and audited.

Verify:
- [ ] Exact version pins: `==` (Python), exact versions in lock files (Node)
- [ ] Lock files committed to git — never gitignored
- [ ] No dependency added without justification
- [ ] `npm audit` / `pip-audit` run regularly
- [ ] New dependencies checked for: maintenance status, known vulnerabilities, license

#### 4.9.10 — Code Review: Every Change Reviewed

Every code change reviewed before merge.

Verify:
- [ ] code-reviewer agent reviews every change (ASPS Section 7.4)
- [ ] Review covers: security, error handling, test coverage, naming, no dead code
- [ ] No direct commits to main — all changes via feature branches
- [ ] Reviewer checks for what is MISSING: tests, error handling, validation
- [ ] Tests exist AND pass before merge

### Resilience (Production-Ready)

#### 4.9.11 — Observability: Health Checks + Metrics + Alerts

Production services are observable beyond just logs.

Verify (MEDIUM tier):
- [ ] Health check endpoint (`/health` or `/healthz`) returning service + dependency status
- [ ] Basic metrics: request count, error rate, response time
- [ ] Uptime monitoring configured

Verify (HEAVY tier — all of the above plus):
- [ ] Health checks include dependency verification (database, external APIs, queue)
- [ ] Structured metrics: latency percentiles (p50, p95, p99)
- [ ] Alerting configured: notification when error rate spikes or service goes down
- [ ] Dashboard: visual overview of system health

#### 4.9.12 — CI/CD Quality Gates

Automated checks that must pass before code reaches production.

Verify (current state — manual gates):
- [ ] All tests pass before merge (CC runs test suite)
- [ ] No linting errors (CC runs linter)
- [ ] code-reviewer agent approves
- [ ] Living document updated

Verify (future state — automated gates):
- [ ] CI pipeline (GitHub Actions or equivalent) configured
- [ ] Automated test + lint + security scan on every push
- [ ] Merge blocked if any gate fails

#### 4.9.13 — Database Migration Discipline

Schema changes versioned, reversible, and never manual.

Verify:
- [ ] All schema changes via migration files — no manual SQL in production
- [ ] Migration files numbered/timestamped and committed to git
- [ ] Every migration has a rollback/down path
- [ ] Migrations idempotent and tested before deployment
- [ ] No modification of already-applied production migrations — create new migration instead
- [ ] Stack-specific tool used: Supabase CLI / Alembic / Prisma / Knex

### Scale (Growth-Ready)

#### 4.9.14 — API Versioning: Version From Day One

Every API versioned from its first endpoint.

Verify:
- [ ] URL path versioning: `/api/v1/resource` (ARUSHAI standard)
- [ ] Version exists from first endpoint — not "added later"
- [ ] Breaking changes require new version (v2)
- [ ] Consistent API response shape: `{ success, data, meta: { version, request_id } }`
- [ ] Deprecated versions remain functional for at least 3 months

#### 4.9.15 — Environment Parity

Dev, staging, and production behave identically.

Verify:
- [ ] Docker/containers used for local development (backend services)
- [ ] Environment-specific config via env vars or config files — no code-level if/else for environments
- [ ] Database schema identical across environments (migration discipline)
- [ ] All environment variables documented in `.env.example` or `config/secrets.example.yaml`
- [ ] Production secrets never used in development

---

## Tier Enforcement Matrix

Not all standards apply equally to all projects. Check the project tier in ASPS.

| Group | Standards | LIGHT | MEDIUM | HEAVY |
|---|---|---|---|---|
| Foundation | 4.9.1 Config | Required | Required | Required |
| Foundation | 4.9.2 Logging | Recommended | Required | Required |
| Foundation | 4.9.3 Config dir | Required | Required | Required |
| Foundation | 4.9.4 Testing | Recommended | Required | Required |
| Foundation | 4.9.5 Error handling | Recommended | Required | Required |
| Quality | 4.9.6 Input validation | Recommended | Required | Required |
| Quality | 4.9.7 Type safety | Recommended | Required | Required |
| Quality | 4.9.8 DRY + SRP | Recommended | Required | Required |
| Quality | 4.9.9 Dependencies | Required | Required | Required |
| Quality | 4.9.10 Code review | Optional | Required | Required |
| Resilience | 4.9.11 Observability | Optional | Basic | Full |
| Resilience | 4.9.12 CI/CD gates | Optional | Manual | Automated |
| Resilience | 4.9.13 DB migrations | N/A | Required | Required |
| Scale | 4.9.14 API versioning | N/A | Required | Required |
| Scale | 4.9.15 Env parity | Optional | Recommended | Required |

**LIGHT tier minimum:** 4.9.1 (config), 4.9.3 (config dir), 4.9.5 (error handling basics), 4.9.9 (dependencies).

**MEDIUM tier minimum:** All Foundation + all Quality standards.

**HEAVY tier:** All 15 standards, no exceptions.

---

## Common Violations and Fixes

| # | Violation | Standard | Fix |
|---|---|---|---|
| 1 | Hardcoded API URL in source file | 4.9.1 | Move to `config/default.yaml` or `.env`; reference via config loader |
| 2 | `console.log("user logged in")` in production code | 4.9.2 | Replace with structured logger: `logger.info({ event: "user_login", userId, correlationId })` |
| 3 | Function with business logic but no test file | 4.9.4 | Write test FIRST (TDD), then update implementation to pass |
| 4 | Bare `try { } catch (e) { }` that swallows the error | 4.9.5 | Log at ERROR with context, then rethrow or return typed error |
| 5 | API accepts user input without schema validation | 4.9.6 | Add Zod/Pydantic schema at the route handler boundary |
| 6 | `any` type used without explanation comment | 4.9.7 | Replace with proper type, or add `// any: reason` comment if genuinely needed |

---

## How to Run a Compliance Check

### For a plan (Mode 1):

1. Determine project tier (LIGHT/MEDIUM/HEAVY) from ASPS
2. Read the plan document
3. For each applicable standard (per tier matrix above), verify the plan addresses it
4. Generate the compliance table with Approach and Status for each standard
5. Flag any gaps as **COMPLIANCE GAP** — the plan is not ready for approval until gaps are resolved

### For code (Mode 2):

1. Determine project tier
2. Read the relevant source files using Grep/Glob/Read
3. Walk through each applicable standard's verify checklist
4. Report findings with specific file:line references
5. Classify each finding: Pass, Warning (non-blocking), or Violation (must fix)
6. Summarize: total standards checked, passes, warnings, violations

---

## Reference

The authoritative source for these standards is OSD Section 4.9 (Engineering Standards — Non-Negotiable Principles). The tier enforcement matrix is defined in OSD Section 4.9 under "Enforcement by Tier." When in doubt, consult the OSD.
