---
name: follow-through
description: Use when a contact, promise, event, or follow-up needs tracking. Atomic notes, follow-up matrices, carry-forwards, reminders, and the weekly analytics pull.
---

# Follow-through

Works with: collateral-library (owed materials), files-of-record (corrections reach recipients), intake-routing (event follow-up runs as a workflow, not ad hoc). Folder layout and the schedule defaults are in the README's Setup and Schedule defaults sections.

## Contact notes

One atomic note per contact at `<root>/contacts/<person>.md` (template: `examples/contact-note.md`). Status lines update as the relationship moves. One note per person, not per conversation; a second thread gets a second status line in the same note. A booked call is a status line with its date.

Matching a conference contact to an existing note: match on name and org, and on email when both records carry one; same name and same org is the same person. Name matches but the org differs: ask the owner; never auto-merge two people who share a name.

The agent never sends, so it never sees a send happen. After each send, the owner tells the agent what went to whom; the agent writes the sent-log line, the contact-note line, and the matrix status. Every send gets a line; a reply that carries no asset is logged as asset "reply: <subject>". The sent log (`<root>/sent-log.md`, template: `examples/sent-log.md`) is how corrections find recipients later; an empty sent log means a correction reaches no one.

## Before a partner call

The agent pulls the record index and any audience package for that partner's workstream (the package names its record) and puts them in front of the owner before the call. If neither exists, the agent hands the owner the contact note and says so; prep is what exists, not what should. Prep is the agent's; the call is the owner's.

## Follow-up matrix

An event is a workflow in the registry ("event follow-up", trigger: the event ends). The registry ships empty: on the first event the agent proposes the entry per intake-routing; the owner's yes makes it Pilot, and it goes Active after the two-use review. Time-sensitive work is never held up by the proposal: the agent builds the matrix and sets reminders while the proposal waits.

Its folder is `<root>/events/<event>/` with the source list (badge scans, exports, notes: whatever the raw list is, saved as `source-list.md`) and `follow-up-matrix.md` (template: `examples/follow-up-matrix.md`): one row per promise (a person with two promises gets two rows) with org, what was promised, material owed, due date, and status.

- The matrix is the record for event promises; the weekly carry-forward is the record for everything else. Where files disagree, the matrix wins for event promises and the weekly file for everything else; contact-note status lines are working notes, not the record. Open matrix rows stay in the matrix and are reviewed there at the Friday review.
- Undated promises get a row with a blank Due and a "needs date" flag, and the agent asks the owner for the date the same day the row is added; still-undated rows are listed together at the weekly review. A promise without a date is a flagged row, not a working promise: no reminder, no done state, until it has a date.
- When the source list changes, rebuild the matrix from the source. A rebuild adds and removes rows for the people the source change adds or removes; Due and Status carry over for every existing row.
- Status: open (nothing sent) / sent (material left the building; the owner sent it) / done (the recipient responded, or the owner closes the loop).
- The agent drafts the follow-ups as one card per event; the owner sends every one.

## Carry-forward

The week's file (`<root>/weekly/<YYYY>-W<NN>.md`, template: `examples/weekly-file.md`) ends with a carry-forward section. At the Friday review, unfinished non-event work moves into next week's file. Nothing dies in a quiet week.

## Reminders

A promise due within 3 days is time-sensitive: it gets a one-shot scheduled reminder (a cron job that fires once) on top of the matrix row or weekly line, never instead of it. When a reminder fires, the owner sends or finishes the item that day, or sets a new date.

## Analytics

The weekly pull runs Friday (the agent), across platforms and the website, logged to `<root>/analytics/log.md`: date, platform, metric, value, note. Anomaly checks on traffic quality and sources; a spike from bot regions is not growth.

## Rules

- The tracking record lives in plain files you control, not a SaaS sheet that dies with someone else's login.
- Every promise has a date or a "needs date" flag.
- The weekly review is mandatory: the carry-forward section of the old file is the primary input to the new one.
