# Provenance

Where the rules came from, stated in capability terms rather than file paths, so the
record survives any reorganization.

## Sources

| Source | What it contributed |
|---|---|
| Architecture workflow — discussion phase | Restate the goal, one question at a time, simpler-path check, option comparison, assumption check, execution spec |
| Architecture workflow — exploration | Read before write, sampling budget, findings summary before proposals |
| Repository agent guide | Instruction hierarchy, definition of done, scope discipline, change report, sanitization |
| Planning workflow | Decision note, execution spec, queue as index, blocker protocol, completion report, batch limits |
| Coding agent workflow | Define done, stay in scope, self-verification, retry limit, plain-language reporting |
| Documentation workflow | Infer vs ask, two audiences, distill not transcribe, no overwrite, migration safety |
| Output style guidance | Lead with the action, numbered steps, list caps, progress state, time estimates |
| Delegation practice | Handoff fields, one owner per decision, structured message envelope |
| Review practice | Named anti-patterns, evidence over assertion |

## Mapping

| Rule | Source |
|---|---|
| P1, P2, P3 | Architecture workflow, discussion phase |
| P4 | Documentation workflow, infer-vs-ask rule |
| P5 | Scope discipline, general agent rules |
| P6, P8, P9 | Architecture workflow, exploration |
| P7 | Repository agent guide, no fabrication |
| P10 | Repository agent guide, instruction priority |
| P11, P12, P13, P15 | Architecture workflow, design and output |
| P14 | General agent rules, destructive-action confirmation |
| P16, P18 | Coding agent workflow, definition of done |
| P17 | General agent rules, change scope |
| P19 | Coding agent workflow, self-verification |
| P20 | Coding agent workflow, retry limit |
| P21, P22, P23 | Documentation workflow and quality requirements |
| P24 | Output style guidance |
| P25 | Delegation practice, context transfer |

## What was excluded

- **Tool-specific procedures.** Provider setup, upload flows, and platform recipes belong
  in their own docs; they age quickly and say nothing about process.
- **Environment detail.** No hostnames, no machine paths, no organization names, no
  service identifiers. Examples use placeholders.
- **Credential handling specifics.** The book states the rule — do not commit secrets —
  and leaves storage mechanics to the reader's platform.
- **Personal preference.** Rules that only make sense in one person's workflow were
  dropped, even when they were habits worth keeping.

## How this book is maintained

1. A rule earns a place only after a real failure traced to it.
2. Every rule keeps the same shape: Do, Why, Don't.
3. Numbering is stable. Retiring a rule leaves a gap rather than renumbering, because the
   checklist and reviews cite numbers.
4. When two rules fight, the decision belongs in the chapter's tension table, not in a new
   rule.
