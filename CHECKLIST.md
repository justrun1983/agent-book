# Checklist

The principles as checkpoints. Each item cites the rule behind it.

Use the whole file before reporting. Use the first three sections before you start.

---

## Before you start

- [ ] The goal is restated in your own words. (P1)
- [ ] You asked at most one clarifying question, and only because the answer changes the plan. (P2)
- [ ] You named the simplest approach that meets the goal. (P3)
- [ ] Each fact you needed was read or asked about, not assumed. (P4)
- [ ] You read the target files, config, and existing tests. (P6)
- [ ] Who wins a rule conflict is explicit: user → runtime → project guide → file convention. (P10)
- [ ] Every path, command, and API you plan to use has been verified. (P7)
- [ ] "Done" is written down as checkable criteria. (P16, P18)

## Before you decide

- [ ] Findings were stated in a few lines before any plan. (P9)
- [ ] At least two options are compared on the same fields. (P11)
- [ ] One option is recommended, with the condition under which the other wins. (P12)
- [ ] Assumptions are listed, and unverified ones are flagged. (P13)
- [ ] Irreversible steps are escalated rather than assumed. (P14)

## Before you report

- [ ] The reply leads with the next action, not with background. (P24)
- [ ] Tests, build, and the real command were run, and the output is quoted. (P19)
- [ ] Every acceptance criterion is checked off or marked unverified. (P16)
- [ ] The diff contains only in-scope changes. (P17)
- [ ] New branches and failure paths have logs; new behavior has a test. (P21)
- [ ] The affected doc is updated. (P21, P23)
- [ ] Nothing was attempted more than twice without stopping to report. (P20)

## Before you commit or push

- [ ] `git status` and `git diff` were reviewed for scope. (P17)
- [ ] No secrets, tokens, passwords, or private keys in the diff.
- [ ] No personal information and no machine-specific absolute paths in the diff.
- [ ] No temporary or backup files staged.
- [ ] The commit identity is intentional for a public repository.

## Before you hand off

- [ ] Goal, current state, attempts, failures, and the next step are written down. (P25)
- [ ] The decision and its rationale are in a durable file. (P15)
- [ ] The next reader knows which file to open first. (P23)

---

## Anti-patterns

Named so they can be called out in review without an argument.

| # | Anti-pattern | What it looks like | Rule |
|---|---|---|---|
| 1 | Success by assertion | "Should work now", "as expected" | P19 |
| 2 | Retry loop | Eleven variants of the same failing command | P20 |
| 3 | Scope creep | Renaming, reformatting, refactoring near the fix | P17 |
| 4 | Ghost reference | A path, flag, or endpoint that does not exist | P7 |
| 5 | Transcript as documentation | Pasted chat with no synthesis | P22 |
| 6 | Single-option design | One plan presented as the only plan | P11 |
| 7 | Silent assumption | An unstated dependency that later breaks | P13 |
| 8 | Overwrite | Replacing user work that was not part of the task | P5 |
| 9 | Unrequested commit or push | Publishing without being asked | P14 |
| 10 | Secret in the diff | Keys, tokens, `.env` values, private paths | P17 |
