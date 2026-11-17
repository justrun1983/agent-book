# Anti-patterns

Named failures. The value of a name is that it can be used in one sentence in review
without an argument.

| # | Anti-pattern | Looks like | Rule |
|---|---|---|---|
| 1 | Success by assertion | "Should work now", "as expected" | P19 |
| 2 | Retry loop | Eleven variants of the same failing command | P20 |
| 3 | Scope creep | Renaming and reformatting near the fix | P17 |
| 4 | Ghost reference | A path, flag, or endpoint that does not exist | P7 |
| 5 | Transcript as documentation | Pasted chat with no synthesis | P22 |
| 6 | Single-option design | One plan presented as the plan | P11 |
| 7 | Silent assumption | An unstated dependency that later breaks | P13 |
| 8 | Overwrite | Replacing work that was outside the task | P5 |
| 9 | Unrequested publish | Commit, push, release, or deploy without being asked | P14 |
| 10 | Secret in the diff | Keys, tokens, env values, private paths | P17 |
| 11 | Question-shaped decision | "Should I use A?" followed by an edit that assumes A | P2 |
| 12 | Half-migration | Some call sites updated; tests green because they miss the rest | P17 |
| 13 | Cosmetic completion | The visible part done; the verified part skipped | P19 |
| 14 | Orphan note | A doc nobody is routed to | P23 |

---

## 1. Success by assertion

**Symptom** — A summary that claims the work without any command output.

**Why it happens** — Running the test is a separate, less interesting step than writing
the code, and the model is fluent enough to describe a plausible result.

**Fix** — Paste the command and its output. Where verification is impossible, name the
gap. See [P19](../05-execute-and-verify.md#p19-verify-your-own-work-before-reporting).

## 2. Retry loop

**Symptom** — A sequence of near-identical commands with small variations, then a summary.

**Why it happens** — Each failure looks like a detail; nobody admits the model is wrong.

**Fix** — Two attempts, then stop and name the doubtful assumption. See
[P20](../05-execute-and-verify.md#p20-stop-after-two-failed-attempts-on-the-same-approach).

## 3. Scope creep

**Symptom** — A diff that touches files the task never mentioned.

**Why it happens** — Adjacent ugliness is visible, and fixing it feels free.

**Fix** — In/out lists before the first edit; adjacent issues become named follow-ups.
See [P17](../04-contract-and-scope.md#p17-scope-is-a-boundary-not-a-suggestion).

## 4. Ghost reference

**Symptom** — A command, path, or function that fails on first use.

**Why it happens** — Plausible patterns from other projects are indistinguishable from
memory of this one.

**Fix** — Verification ladder: repo grep, then `--help`, then docs, then mark unverified.
See [P7](../02-get-the-facts-first.md#p7-never-invent-paths-commands-or-apis).

## 5. Transcript as documentation

**Symptom** — A doc that reads like chat, with the decision buried in the middle.

**Why it happens** — Copying is faster than synthesizing, and it feels complete.

**Fix** — Three filters: still true next month, is it a rule or a record, can a reader
act on it alone. See [P22](../07-persist-and-document.md#p22-distill-dont-transcribe).

## 6. Single-option design

**Symptom** — "The plan is ..." with no alternative and no trade-off.

**Why it happens** — One option feels obviously right, so the comparison feels like
padding.

**Fix** — Two columns, same fields, plus the condition under which the other wins. See
[P11](../03-decide-with-trade-offs.md#p11-two-options-one-table).

## 7. Silent assumption

**Symptom** — The design depends on a fact nobody stated, and it is false.

**Why it happens** — Most assumptions are true most of the time, so they never surface.

**Fix** — Assumption table with a "if false" column; mark unverified. See
[P13](../03-decide-with-trade-offs.md#p13-name-the-assumptions-that-could-break-it).

## 8. Overwrite

**Symptom** — User work disappears inside a "cleanup".

**Why it happens** — The agent's version looks tidier, and the diff hides the deletion.

**Fix** — Read before write; never delete what the task did not mention. See
[P5](../01-align-on-the-goal.md#p5-separate-what-the-user-wants-from-what-you-would-build).

## 9. Unrequested publish

**Symptom** — A push, release, or deploy that the user discovers afterwards.

**Why it happens** — The task said "finish", and publishing looks like finishing.

**Fix** — Publish is a one-way door. Default to local; escalate explicitly. See
[P14](../03-decide-with-trade-offs.md#p14-prefer-reversible-decisions).

## 10. Secret in the diff

**Symptom** — A key, token, or env value in a tracked file, sometimes in history.

**Why it happens** — Debugging with real credentials is faster than with fixtures.

**Fix** — Grep before staging; use placeholders; never commit a backup file. See
[P17](../04-contract-and-scope.md#p17-scope-is-a-boundary-not-a-suggestion).

## 11. Question-shaped decision

**Symptom** — A question in the report, and an implementation that already assumed the
answer.

**Why it happens** — The agent wants to keep momentum and cover itself at the same time.

**Fix** — Either ask before acting, or act and state the default. Not both. See
[P2](../01-align-on-the-goal.md#p2-ask-one-question-not-five).

## 12. Half-migration

**Symptom** — New and old code paths both alive, tests passing because they only cover one.

**Why it happens** — The mechanical part is long and the tests do not complain.

**Fix** — One step per commit; finish or revert; list every half-applied file. See
[P17](../04-contract-and-scope.md#p17-scope-is-a-boundary-not-a-suggestion).

## 13. Cosmetic completion

**Symptom** — The UI or the happy path is done; the error path and the test are not.

**Why it happens** — The visible part produces the reward.

**Fix** — Acceptance criteria include at least one failure path. See
[P19](../05-execute-and-verify.md#p19-verify-your-own-work-before-reporting).

## 14. Orphan note

**Symptom** — Good documentation in a file nobody opens.

**Why it happens** — Writing feels like progress; routing feels like overhead.

**Fix** — Register new docs in the index or agent guide that readers actually follow.
See [P23](../07-persist-and-document.md#p23-write-for-two-audiences).
