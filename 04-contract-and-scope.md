# 4. Contract and scope

**The failure this chapter prevents:** "done" that quietly becomes "out of time".

Without a written definition, the finish line moves to wherever the agent stopped. The
work is not wrong; it is unfinished in a way nobody can see.

## P16. Define "done" before the first edit

**Do** — Write the acceptance criteria as checks you can run or observe, and use them as the checklist at the end.

**Why** — Without a definition, "done" quietly becomes "out of time".

**Don't** — Report success because the diff looks right.

### Three criteria is usually enough

```markdown
Done when:
1. A double submit creates one record. (covered by a new test)
2. The existing suite passes.
3. The button is disabled after the first click. (observed in the browser)
```

Rules:

- Every criterion is a check, not a hope.
- At least one criterion covers the original reason the user asked.
- If you cannot check a criterion yourself, mark who can.

### Criteria you cannot verify are not criteria

"Looks right" and "feels fast" are not done. If the user's reason is subjective, convert
it: "no layout shift on load" instead of "feels smooth".

## P17. Scope is a boundary, not a suggestion

**Do** — Change what the task requires, and only that. Anything adjacent becomes a named follow-up.

**Why** — Every out-of-scope line raises review cost and regression surface.

**Don't** — Rename variables and reorder imports while fixing a bug.

### Write both lists

```markdown
In scope:  the submit handler, its test, the button state
Out of scope: retry logic, form validation, the API client
Follow-ups: validation is client-only (tracked as an issue)
```

The out-of-scope list is the one that protects you. When you notice something else that
is broken, it goes there — not into the diff.

### What "adjacent" is allowed to mean

| Change | In scope? | Why |
|---|---|---|
| A one-line fix required for the acceptance criterion | Yes | The criterion fails without it |
| A comment explaining a non-obvious new branch | Yes | It is part of the change |
| Reformatting the file you touched | No | Noise; the diff should show intent |
| A bug you found on the way | No | Separate task, separate review |
| A test for the new behavior | Yes | Required, not adjacent |

The test is not scope creep. Skipping it is.

## P18. Make acceptance criteria testable

**Do** — Replace adjectives with observations: exit code, test name, output, visible behavior.

**Why** — "Works correctly" cannot be checked by the next person, or by you.

**Don't** — Write "the feature should be stable" as a done criterion.

| Adjective | Testable replacement |
|---|---|
| Fast | p95 under 200 ms on the existing benchmark |
| Robust | Handles null and empty input without throwing |
| Clean | No new lint warnings; file matches neighbors |
| Backward compatible | Old clients still pass the contract test |
| Stable | 100 sequential runs with no failure |

If a criterion needs a tool to check, name the tool. If it needs a human, name the human.

## The contract block

One block at the top of the work keeps everything aligned. Keep it short.

```markdown
Goal: one sentence
Done when: 2-3 checkable criteria
In scope: files or modules
Out of scope: what you will not touch
Open question: the one thing you cannot decide alone
```

For a small task this lives in your reply. For a large task it lives in a file, because
the context will not survive the session.

## The tension: fix the neighbor or leave it

The neighbor problem is real: the adjacent bug makes your fix look broken.

| Situation | Action |
|---|---|
| The acceptance criterion fails without the neighbor fix | Include it, say why in one line |
| The neighbor bug is unrelated but obvious | Leave it, name it as a follow-up |
| The neighbor fix is one line and zero-risk | Leave it anyway; the habit matters more than the line |
| The neighbor is broken and the user will hit it immediately | Ask, once, then follow the answer |

Default to leaving it. The default is not about that one line; it is about the behavior it
trains.

## Chapter checklist

- [ ] Acceptance criteria are written and checkable. (P16)
- [ ] In-scope and out-of-scope lists exist. (P17)
- [ ] No criterion relies on an adjective. (P18)
- [ ] Every adjacent issue found is a named follow-up, not a diff line. (P17)

## Next

[5. Execute and verify →](05-execute-and-verify.md)
