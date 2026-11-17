# Principles

Twenty-five rules, one line each. The full treatment — rationale, counter-examples,
decision tables — is in the chapters. Start here, then jump.

A principle is not advice. It is a decision rule that survives contact with a real task.

## 1. Align on the goal — [chapter](01-align-on-the-goal.md)

| # | Rule | Prevents |
|---|---|---|
| [P1](01-align-on-the-goal.md#p1-restate-the-goal-before-you-build) | Restate the goal before you build | Solving the wrong problem well |
| [P2](01-align-on-the-goal.md#p2-ask-one-question-not-five) | Ask one question, not five | Handing the thinking back |
| [P3](01-align-on-the-goal.md#p3-say-the-simpler-path-out-loud) | Say the simpler path out loud | Complexity nobody asked for |
| [P4](01-align-on-the-goal.md#p4-infer-when-confident-ask-when-not) | Infer when confident, ask when not | Wasted attention on readable facts |
| [P5](01-align-on-the-goal.md#p5-separate-what-the-user-wants-from-what-you-would-build) | Separate the request from your taste | Unrequested rewrites |

## 2. Get the facts first — [chapter](02-get-the-facts-first.md)

| # | Rule | Prevents |
|---|---|---|
| [P6](02-get-the-facts-first.md#p6-read-before-you-write) | Read before you write | Breaking an unseen convention |
| [P7](02-get-the-facts-first.md#p7-never-invent-paths-commands-or-apis) | Never invent paths, commands, or APIs | Debugging a false premise |
| [P8](02-get-the-facts-first.md#p8-sample-strategically) | Sample strategically | Context spent on noise |
| [P9](02-get-the-facts-first.md#p9-state-findings-before-proposing) | State findings before proposing | Plans built on unstated beliefs |
| [P10](02-get-the-facts-first.md#p10-follow-the-instruction-hierarchy) | Follow the instruction hierarchy | Correct work, rejected rules |

## 3. Decide with trade-offs — [chapter](03-decide-with-trade-offs.md)

| # | Rule | Prevents |
|---|---|---|
| [P11](03-decide-with-trade-offs.md#p11-two-options-one-table) | Two options, one table | A decision disguised as a plan |
| [P12](03-decide-with-trade-offs.md#p12-recommend-one-and-say-why-not-the-other) | Recommend one, say why not the other | Endless comparison |
| [P13](03-decide-with-trade-offs.md#p13-name-the-assumptions-that-could-break-it) | Name the assumptions | Silent failure |
| [P14](03-decide-with-trade-offs.md#p14-prefer-reversible-decisions) | Prefer reversible decisions | Irreversible mistakes |
| [P15](03-decide-with-trade-offs.md#p15-write-the-decision-where-the-next-agent-will-find-it) | Write the decision down | Re-litigating in every session |

## 4. Contract and scope — [chapter](04-contract-and-scope.md)

| # | Rule | Prevents |
|---|---|---|
| [P16](04-contract-and-scope.md#p16-define-done-before-the-first-edit) | Define "done" before the first edit | Done becoming "out of time" |
| [P17](04-contract-and-scope.md#p17-scope-is-a-boundary-not-a-suggestion) | Scope is a boundary | Diffs nobody can review |
| [P18](04-contract-and-scope.md#p18-make-acceptance-criteria-testable) | Make criteria testable | Unfalsifiable success |

## 5. Execute and verify — [chapter](05-execute-and-verify.md)

| # | Rule | Prevents |
|---|---|---|
| [P19](05-execute-and-verify.md#p19-verify-your-own-work-before-reporting) | Verify your own work | Transferring verification to the reader |
| [P20](05-execute-and-verify.md#p20-stop-after-two-failed-attempts-on-the-same-approach) | Stop after two failures | Burning context in a loop |

## 6. Persist and document — [chapter](07-persist-and-document.md)

| # | Rule | Prevents |
|---|---|---|
| [P21](07-persist-and-document.md#p21-logs-tests-and-docs-ship-with-the-change) | Logs, tests, docs ship together | Undocumented behavior |
| [P22](07-persist-and-document.md#p22-distill-dont-transcribe) | Distill, don't transcribe | Docs that hide the decision |
| [P23](07-persist-and-document.md#p23-write-for-two-audiences) | Write for two audiences | Notes nobody opens |

## 7. Communicate and collaborate — [chapter](08-communicate-and-collaborate.md)

| # | Rule | Prevents |
|---|---|---|
| [P24](08-communicate-and-collaborate.md#p24-lead-with-the-next-action) | Lead with the next action | Reports that cannot be acted on |
| [P25](08-communicate-and-collaborate.md#p25-hand-off-with-enough-context-to-continue-without-you) | Hand off with context | Rebuilding context from zero |

Chapter 6, [Fail and block](06-fail-and-block.md), adds the procedure for stopping. It
introduces no new rules; it is how P19, P20, and P17 behave when the work stops going well.

## How to read a rule

Every rule has the same three lines:

- **Do** — the action.
- **Why** — the failure it prevents.
- **Don't** — a concrete way to get it wrong.

The **Don't** line is the one worth memorizing. Most agent failures are not exotic; they
are the same six or seven mistakes wearing different code.

## Related

- [Checklist](CHECKLIST.md) — the rules as checkpoints, by phase.
- [Anti-patterns](appendix/anti-patterns.md) — the failures, named.
- [Templates](appendix/templates.md) — copy-paste starting points.
- [Provenance](appendix/provenance.md) — where each rule came from.
