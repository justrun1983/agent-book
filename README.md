# Agent Book

A short book of decision rules for AI coding agents.

Most agent failures are not knowledge failures. The model knew the function; it did not
know what the function was for. It knew the command; it did not run it. It knew the file;
it edited a different one.

Those are process failures, and they happen in a predictable order. This book names them
and gives each one a rule an agent can follow without interpretation.

## The loop

```
Align → Read → Decide → Contract → Execute → Verify → Persist
```

Skips do not save time. They move the cost downstream, where it is harder to see and more
expensive to pay. [Chapter 0](00-mental-model.md) shows that with one worked example.

## Read it three ways

1. **Ten minutes.** [Chapter 0](00-mental-model.md), then the one-line rules in [PRINCIPLES.md](PRINCIPLES.md).
2. **During a task.** Start at [CHECKLIST.md](CHECKLIST.md), find your phase, follow the `P#` into the chapter.
3. **During a review.** Open [appendix/anti-patterns.md](appendix/anti-patterns.md) and name what happened.

## Contents

| File | What it is |
|---|---|
| [00-mental-model.md](00-mental-model.md) | The loop, why order matters, one scenario run twice |
| [01-align-on-the-goal.md](01-align-on-the-goal.md) | P1–P5 · restating, questioning, simpler paths, infer vs ask |
| [02-get-the-facts-first.md](02-get-the-facts-first.md) | P6–P10 · reading, verifying references, findings, instruction priority |
| [03-decide-with-trade-offs.md](03-decide-with-trade-offs.md) | P11–P15 · option tables, recommendations, assumptions, reversibility |
| [04-contract-and-scope.md](04-contract-and-scope.md) | P16–P18 · done criteria, scope boundaries, testability |
| [05-execute-and-verify.md](05-execute-and-verify.md) | P19–P20 · verification ladder, retry limit, commit and publish rules |
| [06-fail-and-block.md](06-fail-and-block.md) | Stopping well: stop rules, blocker report, resumable workspace |
| [07-persist-and-document.md](07-persist-and-document.md) | P21–P23 · logs, tests, docs, audiences, context budget |
| [08-communicate-and-collaborate.md](08-communicate-and-collaborate.md) | P24–P25 · report shape, handoff, delegation, agent messages |
| [PRINCIPLES.md](PRINCIPLES.md) | All 25 rules, one line each, linked |
| [CHECKLIST.md](CHECKLIST.md) | The rules as checkpoints, by phase |
| [AGENTS.md](AGENTS.md) | Machine entry point: routing, style, sanitization |
| [appendix/templates.md](appendix/templates.md) | Contract, decision note, spec, blocker, report, handoff, message |
| [appendix/anti-patterns.md](appendix/anti-patterns.md) | 14 named failures with fixes |
| [appendix/provenance.md](appendix/provenance.md) | Where the rules came from |

Each chapter also carries one **tension table**: two defensible instincts, and the signal
that decides between them. Those tables are the parts people quote back.

## Who it is for

- Agents that read instructions before acting.
- Humans who write those instructions and want a shared vocabulary.
- Reviewers who need to say precisely what went wrong.

## Scope

Process, not tooling. No provider IDs, no internal hostnames, no machine-specific paths.
Examples use placeholders (`src/auth.ts`, `/path/to/repo`, `user@example.com`) so they stay
portable across tools and teams.

## Contributing

Keep entries short, testable, and free of personal or environment-specific detail.
[AGENTS.md](AGENTS.md) defines the style rules and the pre-commit sanitization checks.

## License

No license has been chosen yet. Until a `LICENSE` file is added, all rights are reserved.
