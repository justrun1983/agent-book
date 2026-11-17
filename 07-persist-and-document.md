# 7. Persist and document

**The failure this chapter prevents:** knowledge that dies with the session.

The change works. Three weeks later, nobody remembers why the retry lives where it does,
and the next agent — possibly the same model, with no memory — re-litigates the decision
from scratch.

## P21. Logs, tests, and docs ship with the change

**Do** — Add meaningful logs at branches and failures, cover the new behavior with a test, and update the doc that describes the changed behavior.

**Why** — Undocumented behavior is a bug for the next maintainer.

**Don't** — "Tests and docs to follow."

"To follow" means never, because the context that made the doc easy to write is gone by
then. If a doc cannot be written now, name the file and the reason; do not leave it
implicit.

### The three artifacts and what each proves

| Artifact | Proves | Where |
|---|---|---|
| Test | The behavior is intended, not accidental | Next to the code |
| Log | The branch is observable in production | At decisions and failures |
| Doc update | A reader can use the behavior without reading the diff | The doc that already covers that area |

Not every change needs all three. Every change needs the answer to "which of these did
this change require, and did it get them?"

## P22. Distill, don't transcribe

**Do** — Turn discussion into durable rules, decisions, and context. Keep what stays true next month.

**Why** — A transcript hides the decision inside the noise.

**Don't** — Paste a conversation into Markdown and call it documentation.

### Three questions that filter any note

1. **Will this still be true next month?** If no, it is a status update, not documentation.
2. **Is this a rule, a reason, or a record?** Rules go to conventions, reasons to decision notes, records to logs.
3. **Could a reader act on this without the conversation?** If not, the context is missing, not the length.

A transcript fails all three. A four-line decision note passes all three.

### What to delete on the way in

- Conversational scaffolding: "as we discussed", "good question", "let me explain".
- Superseded options presented as still open.
- Anything specific to one session: temporary paths, command output that will rot, timestamps with no meaning.
- Names and identifiers that are not part of the codebase.

## P23. Write for two audiences

**Do** — Separate "what it means" from "how it is built", and route each note where its reader looks.

**Why** — Implementers drown in business prose; decision-makers drown in schema detail.

**Don't** — Put deployment commands in the product overview.

### Routing table

| Knowledge | Goes to | Reader |
|---|---|---|
| Why the feature exists, who it is for | Product or overview doc | Decision-maker |
| A rule the system enforces | Rules or policy doc | Both |
| How a module is built | Architecture or module doc | Implementer |
| How to run, deploy, configure | Operations doc | Operator |
| Why this option won | Decision note near the code | Next agent |
| What changed and when | Changelog or dev log | Maintainer |

When a note serves both audiences, write it twice in two places with different depth. The
duplicate is cheaper than a doc that serves neither.

## The tension: document everything or keep context small

Every file an agent reads costs context. A doc set that is complete but unreadable is worse
than a small one that gets opened.

| Signal | Add documentation | Skip it |
|---|---|---|
| A future reader will ask "why" | ✓ | |
| The fact is already in code and obvious | | ✓ |
| The behavior is a decision with trade-offs | ✓ | |
| The detail changes every sprint | | ✓ — link to the source of truth |
| You are about to explain the same thing twice | ✓ | |

Two rules keep the set small:

1. **One page per fact.** If two docs say the same thing, one of them will be wrong soon.
2. **Link, don't copy.** A copied table is a future contradiction.

### The staleness rule

A stale doc is worse than a missing one: it is a confident wrong answer. When you touch an
area, fix or delete the doc that describes it. Deleting an obsolete paragraph is a valid
contribution, even when nobody asked.

### Where knowledge goes

| Kind of knowledge | Durable location |
|---|---|
| Why the code is shaped this way | Comment above the non-obvious branch, or a decision note |
| How to work in this repo | The repo's agent guide or contributing file |
| What the system does | Overview doc |
| What changed | Changelog |
| What is known to be broken | Known-issues doc |

If none of these exists and the note matters, create the smallest file that fits. Then
register it somewhere a reader will actually look — an index, not a corner.

## Chapter checklist

- [ ] New behavior has a test; new branches and failures have logs. (P21)
- [ ] The doc covering the changed area is updated or explicitly deferred with a reason. (P21)
- [ ] No transcript was pasted as documentation. (P22)
- [ ] Each note sits where its reader looks. (P23)
- [ ] No duplicate of an existing fact was created. (P23)

## Next

[8. Communicate and collaborate →](08-communicate-and-collaborate.md)
