---
name: arushai-osd-writer
description: Write and update sections of the ARUSHAI Operating System Document (OSD). Use this skill whenever updating, expanding, or refining any section of docs/ARUSHAI_operating_system.md. Triggers: "update OSD", "write section", "expand section", "operating system document", "company document". Always use this skill when touching the OSD file.
---

# ARUSHAI OSD Writer

## Document Location

The OSD lives at `docs/ARUSHAI_operating_system.md`.

## Document Structure

The OSD has 8 sections:

1. Company Identity and Mission
2. The Decision-Making Framework
3. The Product Development Lifecycle
4. The CC Interaction Protocol
5. The Context Management System
6. The Financial Framework
7. The Security and Governance Framework
8. The Evolution Roadmap

## Writing Style

- Professional, direct, no marketing fluff.
- Every sentence must carry meaning.
- No emoji in headers or section titles.

## Format

- Clean Markdown with proper heading hierarchy.
- H1 for document title, H2 for sections, H3 for subsections.
- Table of contents at top with internal anchor links.

## Update Protocol

- When adding content to a section marked [TO BE COMPLETED], remove the marker and write the full section.
- When updating existing content, preserve what exists and append or modify only what is instructed.
- Never rewrite sections that are not explicitly targeted.

## Metadata Updates

After every update, do both of the following in the document metadata block at the top:

1. Increment the version number (patch for fixes, minor for new section content, major for structural changes).
2. Update the "Last Updated" date to today's date.

## Quality Check

After writing, verify:

1. All internal links in the table of contents still work.
2. Heading hierarchy is consistent (no skipped levels).
3. No [TO BE COMPLETED] markers remain in completed sections.
4. Update the "Status" field in the metadata to reflect current completion state.
