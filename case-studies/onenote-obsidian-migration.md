# OneNote to Obsidian Migration Reliability

## Summary

I built a local workflow to make OneNote to Obsidian migration more reliable, auditable, and privacy-preserving.

The core problem was not simply "convert notes to Markdown." The harder problem was proving that the migration was complete, identifying missing or empty pages, cleaning noisy Markdown formatting, and giving the user a safe review step before deletion or reorganization.

## Problem

Large OneNote migrations can fail in ways that are hard to notice:

- some sections or pages may not import cleanly
- large imports can hit API rate limits or transient server failures
- imported Markdown can contain visual-layout artifacts such as extra tabs, broken line wrapping, and excessive blank lines
- empty pages and duplicate pages can make the resulting vault feel untrustworthy
- private notes require careful local-only handling of temporary credentials

## Approach

The workflow uses a staged migration model:

1. Import and count notebooks, sections, pages, and attachments.
2. Preserve source identifiers so repeated runs can detect duplicates.
3. Generate review reports for empty, duplicate, and low-information notes.
4. Clean Markdown formatting while preserving code blocks, tables, lists, images, and attachment links.
5. Remove temporary authentication artifacts after the run.
6. Keep deletion decisions explicit and reviewable.

## Engineering Notes

The most important design choice is auditability. A migration tool should not only say "done"; it should show what it saw, what it imported, what failed, and what still needs review.

Useful implementation patterns:

- source page IDs in frontmatter for idempotency
- retry and backoff behavior for API imports
- import manifests for reconciliation
- deterministic Markdown cleanup with conservative skip rules
- user-facing review reports before destructive actions

## Potential Upstream Contributions

This work can be broken into small contributions to an importer project:

- show pages seen, pages imported, and failures at the end of a OneNote import
- write a machine-readable import manifest
- expose failed sections or pages in the UI instead of only console logs
- add a post-import audit command for empty notes, duplicate notes, and missing attachments
- improve cleanup of common OneNote-to-Markdown formatting artifacts

## Privacy

The workflow is designed to avoid publishing or storing private note content. Public documentation should describe the method and engineering tradeoffs without exposing account details, note titles, personal data, or imported content.

