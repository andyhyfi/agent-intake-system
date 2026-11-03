# Agent intake system

A lightweight operating system for a one-person comms/BD function run with AI agents: how work comes in, how it gets filed and tracked, how promises get followed up, and how partner-facing materials get built from one canonical record.

Four skills, each small enough to load on its own:

1. `intake-routing`: use when an ask, request, or idea arrives from any source and needs a place to go.
2. `files-of-record`: use when a deck or doc is named, or proposed, as the canonical source for a workstream.
3. `collateral-library`: use when a material is dropped (PDF, deck, export) or an audience package is requested.
4. `follow-through`: use when a contact, promise, event, or follow-up needs tracking. Includes the weekly analytics pull.

## Setup

One folder holds the whole system. Default `~/agent-system/`; move it anywhere and treat every path below as relative to it.

```
<root>/
  inbox.md               one line per ask, in any order
  registry.md            the workflow registry
  weekly/<YYYY>-W<NN>.md one file per week, ends with a carry-forward section
  sources/               the original of every inbound ask (email text, chat export)
  library/
    index.md             the collateral master index (one index file only)
    assets/<name>/       dropped materials, record versions, and parsed notes
    copy/                proven outreach copy, stored verbatim as sent
    records/             record indexes, one per workstream: <workstream>-index.md
  contacts/<person>.md   one atomic note per contact
  events/<event>/        source list + follow-up-matrix.md
  sent-log.md            date, asset, recipients, channel: every send
  analytics/log.md       the weekly analytics record
```

Templates for these files are in `examples/`. The event source list is the exception: it is the raw list, saved as-is.

## Roles and authority

Two roles, stated plainly:

- **The owner**: the human. Decides what is worked on, names workstreams and files of record, approves every correction list, and is the only one who sends anything, books anything, or contacts anyone outside the team. The agent never sends email, never books a call, never posts.
- **The agent**: files, drafts, parses, tracks, reminds. Anything that leaves the team is a draft plus a list handed to the owner.

A reviewer pass (a second agent or profile checking deliverables) can sit between drafting and the owner. Optional.

## Schedule defaults

Change any of these; they are defaults, not laws.

- The inbox sweep runs at the end of every working day. The agent runs it.
- A card stalled at the reviewer pass past 24 hours is forced through by the agent: marked done with the draft as-is and flagged to the owner. This applies to the reviewer pass only; the draft still goes to the owner either way.
- The weekly review runs Friday. The carry-forward section of this week's file is the primary input to next week's.
- The analytics pull runs Friday; the agent runs it.
- A promise is time-sensitive when it is due within 3 days. Those get a scheduled reminder on top of the matrix row or weekly line, never instead of it.

## Tools (Hermes Agent defaults)

- Task cards: the Hermes kanban board; create with title, assignee, and a full context brief.
- One-shot reminders: a scheduled job (cron) that fires once.
- Design-tool links: parse via your platform's design-tool API connector if you have one; otherwise ask the owner for a PDF export. Image-only PDFs: render and OCR.
- Reaching the owner: a direct chat message to the owner is the default channel. Flags, questions, forced-through drafts, and fired reminders all land there.

## Starter audience taxonomy

`buyer · platform partner · press · investor · internal`

Tag with this list until the owner replaces it. If an asset fits no tag, ask the owner rather than inventing one.

## Install

Copy the folders under `skills/` into your agent's skills directory (Hermes Agent: `~/.hermes/skills/<category>/`; any category works, and `productivity/` is a fine choice). Copy the templates you need from `examples/`.

## Origin

This is the public, generalized version of a system I have run daily since 2024 in private, IP-gated environments: first at a DeFi lending protocol, now at a fintech. Company data, partner names, deal terms, and employer-specific processes have been removed; the structure is the one in production, and the specifics are placeholders. Where a skill says "partner" or "audience," substitute your own.

## License

MIT; see LICENSE.
