# Agent Book

A short book of decision rules for AI coding agents.

Most agent failures are not model failures. They are process failures: the goal was
misread, a path was invented, scope drifted, "done" was never defined, or the work was
never verified. This book names those failure points and gives each one a rule an agent
can follow without interpretation.

## Who it is for

- Agents that read instructions before acting (CLI agents, IDE agents, orchestrators).
- Humans who write those instructions and want a vocabulary for them.
- Anyone reviewing agent output who needs to say precisely what went wrong.

## How to use it

1. Read `PRINCIPLES.md`. Twenty-five rules in five domains, each with a reason and a counter-example.
2. Keep `CHECKLIST.md` open while working. It converts the principles into checkpoints.
3. Point your agent at `AGENTS.md` so it knows which file to read for which task.

If you only have thirty seconds, read the five domain names and principle 16.

## Layout

| File | Purpose |
|---|---|
| `PRINCIPLES.md` | The rules. Numbered `P1`–`P25` so they can be referenced. |
| `CHECKLIST.md` | The same rules as checkpoints, plus named anti-patterns. |
| `AGENTS.md` | Machine entry point: task → which section to read, plus repo rules. |

## The core loop

```
Align → Read → Decide → Contract → Execute → Verify → Persist
```

Every principle belongs to one step of that loop. Skipping a step does not save time; it
moves the cost downstream, where it is harder to see and more expensive to pay.

## Scope

This is about process, not tooling. It contains no provider IDs, no internal hostnames,
and no machine-specific paths. Examples use placeholders (`src/auth.ts`,
`/path/to/repo`, `user@example.com`) so they stay portable.

## Contributing

Keep entries short, testable, and free of personal or environment-specific detail.
`AGENTS.md` defines the sanitization rules; run its pre-commit greps before opening a pull
request.

## License

No license has been chosen yet. Until a `LICENSE` file is added, all rights are reserved.
