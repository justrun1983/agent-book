# 0. The mental model

Agent failures are usually not knowledge failures. The model knew how to write the
function; it did not know what the function was for. It knew the command; it did not run
it. It knew the file; it edited a different one.

Those are process failures, and they happen in a predictable order. That order is the
structure of this book.

## The loop

```
Align → Read → Decide → Contract → Execute → Verify → Persist
```

| Step | The question it answers | Skipped, it costs | Chapter |
|---|---|---|---|
| Align | What outcome does the user actually want? | A completed task nobody needed | [1](01-align-on-the-goal.md) |
| Read | What already exists here? | A change that breaks the local convention | [2](02-get-the-facts-first.md) |
| Decide | Which path, and why not the other? | A single-option plan that hides the cost | [3](03-decide-with-trade-offs.md) |
| Contract | What does "done" mean, and where are the edges? | An open-ended edit that keeps growing | [4](04-contract-and-scope.md) |
| Execute | What is the smallest change that satisfies the contract? | Noise in the diff, risk in the review | [5](05-execute-and-verify.md) |
| Verify | What evidence proves it works? | A claim the reviewer has to test for you | [5](05-execute-and-verify.md) |
| Persist | What must survive this session? | The next agent starts from zero | [7](07-persist-and-document.md) |

Failures that stop the loop are covered in [6](06-fail-and-block.md). How to report and
hand off is covered in [8](08-communicate-and-collaborate.md).

## Cost moves downstream

A mistake costs more the later it is discovered. A wrong goal caught in the first message
costs one sentence. The same goal caught after implementation costs the implementation,
the review, the tests, and the trust.

This is why the early steps are cheap to do and expensive to skip. Restating the goal
takes ten seconds. Finding out in review that you solved the wrong problem takes a day.

## One scenario, two runs

Request: "Add a timeout to the HTTP client."

**Run A — no align, no read.**

The agent adds `timeout: 30` to the constructor, runs the tests, reports success. The
timeout applies to the whole request including retries, so a retried call can now take
90 seconds. The existing retry wrapper already had a deadline. Three days later a
production alert appears.

**Run B — align, read, then edit.**

The agent reads the client file, the retry wrapper, and the config. It finds a global
deadline and a per-attempt timeout that are separate concepts. It asks one question:
should the timeout apply per attempt or to the whole call? It comments on the diff that
the two are distinct, adds a per-attempt value, and notes the existing deadline as
unchanged.

Same model, same request. The difference was five minutes of process.

## Three ways to use this book

1. **Ten-minute skim.** Read this page, then `PRINCIPLES.md`. You will have the vocabulary.
2. **Task-time lookup.** Start at `CHECKLIST.md`, find the section matching where you are, follow the `P#` to its chapter.
3. **Review.** Read `appendix/anti-patterns.md` and name what happened. A named failure is easier to fix than a vague one.

## What this book is not

- Not a prompt library. There are no copy-paste prompts, because the useful part is the decision, not the phrasing.
- Not a tool manual. Commands appear as examples; your tool's own docs win.
- Not a coding standard. Formatting and naming are local conventions and belong in the repo.

## Next

[1. Align on the goal →](01-align-on-the-goal.md)
