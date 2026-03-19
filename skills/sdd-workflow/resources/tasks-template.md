# Tasks: {Feature Name}

**Feature ID:** F{NNN}
**Date:** {date}
**Status:** Draft | Approved
**Plan Version:** {plan version or date approved}

---

## Size Legend

| Size | Time Estimate | Guidance |
|---|---|---|
| S | Under 30 min | Config, scaffold, docs, single-file changes |
| M | 30-90 min | Core logic, test suites, API endpoints |
| L | Over 90 min | Consider splitting into multiple tasks |

## Task List

TDD-first ordering: scaffold → test → implement → integrate → document.
Each task = exactly one CC prompt. Task IDs map 1:1 to CC prompt IDs.

| ID | Task | Size | Depends On | Test Count |
|---|---|---|---|---|
| T001 | Scaffold directory structure and config files | S | — | — |
| T002 | Write unit tests for {component} | M | T001 | ~{N} tests |
| T003 | Implement {component} — all T002 tests must pass | M | T002 | — |
| T004 | Write unit tests for {component} | M | T001 | ~{N} tests |
| T005 | Implement {component} — all T004 tests must pass | M | T004 | — |
| T006 | Write integration tests for {components} | M | T003, T005 | ~{N} tests |
| T007 | Implement integration layer — all T006 tests must pass | M | T006 | — |
| T008 | Update documentation and changelog | S | T007 | — |

## Progress Tracker

| ID | Status | CC Prompt ID | Commit |
|---|---|---|---|
| T001 | Pending | — | — |
| T002 | Pending | — | — |
| T003 | Pending | — | — |

Update this table as tasks are completed. Each row links to the CC prompt ID and commit hash for full traceability.
