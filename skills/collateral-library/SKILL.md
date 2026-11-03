---
name: collateral-library
description: Use when a material is dropped (PDF, deck, export, link) or an audience package is requested. One indexed library; packages assembled from what already exists.
---

# Collateral library

Works with: intake-routing (a dropped material is also an inbox line), files-of-record (a deck named as record gets a record index), follow-through (owed materials for events). Folder layout is in the README's Setup section; the audience taxonomy is in the README.

Sales and partner materials accumulate in chats, desktops, and exports. This skill turns them into one library at `<root>/library/`.

## Collect

When a material is dropped: file it under `<root>/library/assets/<name>/` the same day, and add one row to the master index at `<root>/library/index.md`, the one index file (template: `examples/master-index.md`). IDs run A-001, A-002, sequential, never reused. Status values: Incoming / Parsed / Approved / Superseded / Dormant. Every row carries an audience tag, and a "built from record (version)" link when the asset derives from a record.

A dropped material is also an intake item: it gets an inbox line (intake-routing), so it is tracked even when nobody has asked for anything yet. A deck with two audiences gets one row; both tags go in the notes.

The owner sets an asset to Approved after reviewing it; Approved means it can be sent and derived from. The agent parses and sets the row to Parsed when the notes are complete.

## Parse

A dropped deck lives at `library/assets/<name>/` with its notes at `slides/NN-topic.md`; when the deck is a record, each version gets its own dated folder `library/assets/<name>/<YYYY-MM-DD>/` with the deck file and its own `slides/` (template: `examples/slide-note.md`). One note per slide or page: headline verbatim, body verbatim in reading order, data points with sources, and what the image shows. Fixed sections, so downstream automation can assemble new decks by picking topics.

- A number with no source is written "source: none given" and flagged in the master index row; if the deck is a record, also in the record index.
- Design-tool links parse via your platform's API connector if you have one; image-only PDFs render and OCR; single complex diagrams get a vision pass, because OCR misses structure and color-coding.
- Text-layer truncation and OCR artifacts (broken dates, garbled numbers) are flagged, never silently trusted.
- One slide, one idea. Near-duplicate ideas across decks are not auto-deleted: list them in the index notes and let the owner pick the canonical copy; record the pick in the index row.
- Parsing a deck longer than a few pages is a card, not a sweep side-task.

A card about a deck attaches the raw PDF (raw sources, never a pre-digested outline) and links the index row. The slide notes live in the library, not on the card.

## Audience packages

An audience package is a small set of materials for one audience, assembled from existing assets plus a few new pieces. Spec it in one file: the audience named, one line per piece (what it is, who owns it), and the claim constraints every piece inherits from the record. The package names its record, which is how a partner maps to a workstream.

- Inventory first: check what already exists before proposing anything new. Packages are based on what you already have, refined, not rebuilt.
- Check live URLs before listing any page.
- If an owed material does not exist yet, it becomes a card through intake-routing.

## Proven outreach copy

Text that actually got a reply is stored verbatim as sent at `<root>/library/copy/`, never polished, with the result noted; it is a log of what worked. Adaptations keep the structure; only the opener and closer change per recipient. Copy carrying a superseded stat is marked "superseded stat, do not reuse unchanged" (files-of-record, the correction procedure).
