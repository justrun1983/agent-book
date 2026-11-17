# Checklist

The rules as checkpoints, ordered by when you need them. Each item cites the rule; each
section links to the chapter with the reasoning.

Use the whole file before reporting. Use the first three sections before you start.

Jump to: [Start](#before-you-start) · [Decide](#before-you-decide) · [Report](#before-you-report) · [Publish](#before-you-commit-or-push) · [Hand off](#before-you-hand-off)

---

## Before you start

Chapter: [1](01-align-on-the-goal.md) · [2](02-get-the-facts-first.md) · [4](04-contract-and-scope.md)

- [ ] The goal is restated: outcome, reason, and what "done" looks like. (P1)
- [ ] At most one clarifying question was asked, and only because the answer changes the plan. (P2)
- [ ] The simplest approach that meets the goal was named. (P3)
- [ ] Each fact you needed was read or asked about, not assumed. (P4)
- [ ] The target files, config, and existing tests were read. (P6)
- [ ] Every path, command, and API has a verification source or an "unverified" mark. (P7)
- [ ] Rule conflicts were resolved in order: user → runtime → project guide → file. (P10)
- [ ] "Done" is written as checkable criteria. (P16, P18)
- [ ] In-scope and out-of-scope lists exist. (P17)

## Before you decide

Chapter: [3](03-decide-with-trade-offs.md)

- [ ] Findings were stated in a few lines before any plan. (P9)
- [ ] At least two options are compared on the same fields. (P11)
- [ ] One option is recommended, with the condition under which the other wins. (P12)
- [ ] Assumptions are listed with an "if false" consequence. (P13)
- [ ] One-way doors were escalated rather than assumed. (P14)

## Before you report

Chapter: [5](05-execute-and-verify.md) · [6](06-fail-and-block.md) · [8](08-communicate-and-collaborate.md)

- [ ] The reply leads with the outcome or the next action. (P24)
- [ ] Tests, build, and the real command were run, and the output is quoted. (P19)
- [ ] Levels not verified are named explicitly. (P19)
- [ ] Every acceptance criterion is checked off or marked unverified. (P16)
- [ ] The diff contains only in-scope changes. (P17)
- [ ] New branches and failure paths have logs; new behavior has a test. (P21)
- [ ] The affected doc is updated, or the omission is explained. (P21, P23)
- [ ] Nothing was attempted more than twice without stopping to report. (P20)

## Before you commit or push

Chapter: [5](05-execute-and-verify.md#the-tension-commit-push-and-publish) · [AGENTS.md](AGENTS.md#sanitization-mandatory)

- [ ] `git status` and `git diff` were reviewed for scope. (P17)
- [ ] No secrets, tokens, passwords, or private keys in the diff.
- [ ] No personal information and no machine-specific absolute paths in the diff.
- [ ] No temporary or backup files staged.
- [ ] The commit identity is intentional for a public repository.
- [ ] Push, release, deploy, and destructive actions happened only if asked. (P14)

## Before you hand off

Chapter: [8](08-communicate-and-collaborate.md) · [7](07-persist-and-document.md)

- [ ] Goal, state, attempts, blocked-by, and next step are written down. (P25)
- [ ] The next reader knows which file to open first. (P23)
- [ ] The decision and its reason are in a durable file. (P15)
- [ ] The tree is runnable, or every half-applied change is listed. (P17)

---

## Named failures

When an item above is violated, the review can cite the name instead of describing the
problem. Full list: [Anti-patterns](appendix/anti-patterns.md).

Success by assertion · retry loop · scope creep · ghost reference · transcript as
documentation · single-option design · silent assumption · overwrite · unrequested
publish · secret in the diff · question-shaped decision · half-migration · cosmetic
completion · orphan note.
