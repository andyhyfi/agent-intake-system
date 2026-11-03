---
name: files-of-record
description: Use when a deck or doc is named, or proposed, as the canonical source for a workstream. One record per workstream, indexed, so every draft defers to it.
---

# Files of record

Works with: collateral-library (the master index links every derived asset to its record), follow-through (corrections reach recipients through the sent log and contact notes). Folder layout is in the README's Setup section.

Each workstream (a product pitch, a partnership, a content package) has ONE file of record: usually the deck or doc the owner actually uses. Everything else is a draft.

## Naming a record

The owner names the record and the workstream. When a new deck arrives, the agent asks the owner once: is this the record for an existing workstream, a new version of an existing record, or a separate draft? If no workstream fits, the owner names a new one. The agent never guesses.

## Copies

The owner edits their own file. When the owner says they have edited it, the agent re-copies the file into the library and rebuilds the record index in the same pass. The Friday review compares the source file to the library copy and catches edits the owner did not report. The library copy is the record; the owner's file is the source. Only the library copy is ever quoted. That is what keeps two copies from meaning two records.

## Versions

Every re-copy is a new version at `library/assets/<name>/<YYYY-MM-DD>/` (a second re-copy the same day takes `<YYYY-MM-DD>-2`). The version folder holds the deck file and its own `slides/` notes, so slide notes always match the version they were parsed from. The master index's built-from links name the version an asset was built from. Old versions stay; nothing a recipient holds is ever edited in place.

## The record index

One index per workstream at `<root>/library/records/<workstream>-index.md` (template: `examples/record-index.md`):

- what the record is, and what it supersedes
- the spine: section order and the key claim of each section
- every stat, its source, and its status: verified / under fact-check / wrong, superseded by [corrected number] ([date])
- the fixed language that must not drift across derived materials
- precedence: drafts defer to the record; where a draft and the record disagree, the record wins

Every master-index row for a derived asset carries a "built from record (version)" link to this index. That link is what makes corrections possible.

## Parsing stats

A number with no source is recorded as "source: none given" and flagged in the master index row; when the deck is a record, also in the record index under fact-check. The source is checked before the stat is repeated anywhere.

## When a stat turns out wrong

The owner confirms the stat is wrong. Until then it stays under fact-check and this procedure does not run.

1. Record index: mark the stat "wrong, superseded by <corrected number> (<date>)". Never erase the old value. Rebuild the index in the same pass; the superseded marking governs until the re-copy lands.
2. Comment on every in-flight card whose output draws on the record: a card drafting during a correction carries the superseded stat until it is told.
3. The correction list includes one owner action: correct the source file. After the owner edits it, the agent re-copies it as a new version and rebuilds the index.
4. Find every asset that carries the stat by searching the master index, the parsed slide notes, and the stored outreach copy for the number. The built-from column is a starting list, not the whole list: older assets can carry the stat with no record link. Mark each affected row Superseded, draft a corrected version as a new row, and hand the corrected versions to the owner to approve (Approved, per collateral-library). Never edit a version recipients hold. Parsed slide notes stay verbatim; add one correction line under Data points ("corrected YYYY-MM-DD: <old> to <new>").
5. List every recipient of affected materials from the sent log and the contact notes. A public post lists its recipients as public; correcting a public post means a correcting post, or an edit where the platform allows, and the owner decides.
6. Hand the owner one correction list: what was wrong, what changed, which assets, which recipients. Nothing is sent until the owner approves it; the agent never sends.
7. Stored outreach copy that carries the stat is a log of what was sent: it stays as sent and is marked "superseded stat, do not reuse unchanged."

## Rules

- One record per workstream. Two records means no record.
- The owner replaces the record; the agent re-copies and re-indexes in the same pass. An index pointing at a superseded file is worse than no index.
- Audience-specific materials are built FROM the record, never beside it: same stats, same fixed language, different framing. That is what makes the experience consistent for every external party.
