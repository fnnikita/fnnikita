# Hi, I'm Nikita

I build practical tools at the intersection of AI workflows, knowledge systems, and product engineering.

## Featured Work

### OneNote to Obsidian Migration Reliability

Status: local workflow validated; checklist published; upstream contribution candidate.

I recently built and tested a privacy-first workflow for moving a large OneNote knowledge base into Obsidian Markdown while preserving structure, attachments, and reviewability.

What this work covers:

- Microsoft Graph based notebook, section, and page import auditing
- Retry-aware migration checks for large OneNote libraries
- Markdown cleanup for OneNote formatting artifacts
- Empty page, duplicate page, and low-information note detection
- Local-only temporary credential handling and post-run cleanup
- Review reports that let users decide before deleting content

Why it matters:

Reliable note migration is not just a file conversion problem. Large personal knowledge bases need completeness checks, failure visibility, privacy guarantees, and cleanup tools that preserve trust.

Case study: [OneNote to Obsidian Migration Reliability](case-studies/onenote-obsidian-migration.md)

Public checklist: [Obsidian Migration Checklist](https://github.com/fnnikita/obsidian-migration-checklist)

## Open Source Direction

I am exploring small, focused contributions to the official Obsidian Importer ecosystem, especially around:

- clearer import summaries
- visible failure reports
- safer retry behavior for large imports
- post-import audit and cleanup workflows

Open issue: [OneNote import: add local summary and failure report for large migrations](https://github.com/obsidianmd/obsidian-importer/issues/580)

Open PR: [Fix OneNote progress for skipped pages](https://github.com/obsidianmd/obsidian-importer/pull/581)

The goal is to make migration tools more trustworthy for people moving years of notes into durable Markdown.
