---
name: intake-routing
description: Use when an ask, request, or idea arrives from any source and needs a place to go. One inbox, written placement rules, task cards with owners and done-whens.
---

# Intake and routing

Works with: follow-through (anything touching a contact), collateral-library (dropped materials), files-of-record (anything that changes a record). Folder layout and the schedule defaults are in the README's Setup and Schedule defaults sections.

## The inbox

Every ask (chat, email, DM, meeting) becomes one line in `<root>/inbox.md`, in any order. The original (the email text, the chat export, the meeting note) is saved to `<root>/sources/` with a date-slug filename, and the inbox line links to it. The one-line inbox and the saved original together are the ask; neither is dropped.

Line format: `examples/inbox-line.md`. A dropped material (PDF, deck, export) is an ask too: it gets an inbox line that links to its library index row (the file itself lives in the library, never in sources/) and files there the same day per collateral-library. The line closes at the sweep once the index row exists; a dropped-material line is never deleted while the asset is in the library.

## The sweep

The sweep runs at the end of every working day (default; the agent runs it) and empties the inbox by placing each line:

1. Fits an existing workflow: file it there, and name the workflow in one line.
2. Stretches one: propose the change to the owner; on approval update `<root>/registry.md` and log the change in the registry.
3. Fits nothing: propose a new workflow as five lines (name, owner, trigger, files, done-when), added to the registry as Pilot on the owner's yes. Review with the owner after two uses; the entry goes Active when the review passes.

One-offs are accepted work: they get a line in the current week's file (`<root>/weekly/<YYYY>-W<NN>.md`), not a workflow. A one-off that needs drafting, including a short reply, gets a card.

Deleting lines: an item that survives three sweeps unplaced AND comes from no named external person is not real work; delete it. An ask from a named external person is never deleted: it goes to the weekly review, and if it is time-sensitive the owner is asked directly.

A workflow unused for four weeks goes Dormant in the registry. One you keep bending goes to Needs-redesign, raised at the weekly review. Registry entry format: `examples/workflow-registry-entry.md`.

## Task cards

Accepted work that needs doing becomes a card on the kanban board with three fields, none optional:

- a named owner (a real agent profile or a person)
- a full context brief: goal, source files, output format, done-when
- raw sources attached: the saved original, the PDF, the link; never a pre-digested outline

Draft, review, owner is the pipeline. A card stalled at the reviewer pass past 24 hours is forced through by the agent: marked done with the draft as-is and flagged to the owner. The draft still reaches the owner either way. Stalled is not a status.

## External people

The agent never replies to an outside ask, books a call, or contacts anyone outside the team. A partner ask from a named person is flagged to the owner the same day, with the saved original attached and the prep the owner needs (see follow-through: before a partner call). When the owner wants to reply, the agent drafts the reply; the owner edits and sends.
