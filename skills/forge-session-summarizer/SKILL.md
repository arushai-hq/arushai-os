---
name: forge-session-summarizer
description: Summarize FORGE research sessions into structured documents for the ARUSHAI knowledge base. Use this skill when converting raw FORGE session output into a referenceable summary. Triggers: "summarize FORGE session", "create session summary", "archive session", "FORGE summary".
---

# FORGE Session Summarizer

## What Are FORGE Sessions

FORGE sessions are deep-dive research and brainstorming sessions conducted in Claude web sessions. They produce raw output that needs to be distilled into structured, referenceable summaries.

## Output Location

Each summary goes into `docs/forge-sessions/` with filename format `FORGE-[NNN]-summary.md`.

## Summary Structure

Every FORGE summary must include these sections, in this order:

1. **Session ID** — FORGE-[NNN]
2. **Date** — Date the session was conducted
3. **Topic** — One-line description of the research topic
4. **Key Findings** — Bulleted list with source references where applicable
5. **Repos Discovered** — With stars, URLs, and one-line descriptions (if applicable)
6. **Decisions Made** — Any decisions reached during the session
7. **Open Questions** — Unresolved questions for future sessions
8. **Connection to OSD Sections** — Which OSD sections this session informs or impacts

## Rules

- Preserve all source references and URLs — these are the evidence base.
- Keep summaries concise but complete — a reader should understand what was learned without reading the full session transcript.
- If findings impact specific OSD sections, note which sections should be updated.
- Use sequential numbering for session IDs (FORGE-001, FORGE-002, etc.).
