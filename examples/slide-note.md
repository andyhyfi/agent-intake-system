# Parsed slide note format

`library/assets/<deck>/<YYYY-MM-DD>/slides/NN-topic.md` for a record version, `library/assets/<deck>/slides/NN-topic.md` for a plain dropped deck. One per slide or page, fixed sections.

---
deck: [deck-name]
slide: N
topic: [one line]
audience: [tag]
---

## Headline (verbatim)

## Body (all text, verbatim, reading order)

## Data points (numbers with sources; "source: none given" where the deck cites none; a superseded stat gets a correction line here: "corrected YYYY-MM-DD: <old> to <new>")

## Graphics notes (what the image shows)

Flags (truncation, OCR artifacts, near-duplicates) go in the master index row, not hidden here.
