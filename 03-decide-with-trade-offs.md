# 3. Decide with trade-offs

**The failure this chapter prevents:** a decision presented as a fact.

One option, no assumptions listed, no note about what would change the answer. The user
cannot disagree with the reasoning, only with the result — which means the decision gets
made twice.

## P11. Two options, one table

**Do** — Present at least two viable approaches with the same fields: approach, complexity, risk, best when.

**Why** — A single option is a decision already made for the user.

**Don't** — Present one plan as "the plan".

```markdown
| | Patch the handler | Extract a shared client |
|---|---|---|
| Approach | Add the check inline | Move retry logic into one module |
| Complexity | Low | Medium |
| Risk | Duplicated logic later | Touches three call sites |
| Best when | This is the only caller | Two more callers are coming |
```

Three rules for the table:

1. **Same fields in both columns.** A comparison with different criteria is two
   arguments, not one comparison.
2. **Honest cost.** If the option you dislike is cheaper, say so.
3. **No straw man.** The alternative must be something you would actually accept.

## P12. Recommend one and say why not the other

**Do** — Pick one, give the reason in a sentence, and name the condition under which the other wins.

**Why** — A comparison without a recommendation hands the decision back instead of resolving it.

**Don't** — End with "both are viable, your call."

The losing-condition sentence is the useful part:

> "I recommend the patch: there is one caller and the retry logic is unlikely to spread.
> If you expect a second caller this quarter, take the extraction instead."

Now the user can disagree with a specific belief, not a general vibe.

## P13. Name the assumptions that could break it

**Do** — List the conditions the design depends on, and flag the ones you did not verify.

**Why** — Unstated assumptions fail silently and get blamed on the code.

**Don't** — Assume an endpoint is idempotent and never say it.

Format each assumption so it can be tested:

| Assumption | Verified? | If false |
|---|---|---|
| The endpoint is idempotent | No | Retries duplicate records |
| Only one writer touches the table | Yes — schema comment | Need a lock |
| Payloads stay under 1 MB | No | Need streaming |

"If false" is the column that makes it useful. An assumption without a consequence is
decoration.

## P14. Prefer reversible decisions

**Do** — Choose the option you can undo cheaply. Escalate the ones you cannot: data deletion, public API changes, published releases.

**Why** — Reversibility turns a decision into an experiment.

**Don't** — Treat a destructive migration like a code style choice.

### Two-way and one-way doors

| Door | Examples | How to decide |
|---|---|---|
| Two-way | Naming, internal structure, logging, a new flag | Decide yourself, move on |
| One-way | Dropping a column, changing a public response shape, deleting a branch, publishing | Stop, state the cost, get explicit approval |

The common mistake is treating a one-way door as a two-way one because it is one line of
code. Length of the diff is not the measure; recoverability is.

## P15. Write the decision where the next agent will find it

**Do** — Record goal, options, choice, and reason in a durable file, not in chat.

**Why** — Chat dies with the session; the next agent starts from zero.

**Don't** — Leave the rationale only in a commit message or your reply.

A commit message says what changed. It cannot hold why the other option lost. That
context belongs in a decision note next to the code or in the project's docs, whichever
the repo already uses. If the repo has no convention, put it where a reader looking at
the changed file would look.

Minimum viable record:

```markdown
## Decision: per-attempt timeout
Options: per-attempt (chosen) vs whole-call.
Why: retries are counted separately; a whole-call timeout hides which attempt failed.
Revisit if: retries are removed.
```

Four lines. Enough to stop the next agent from re-litigating.

## The tension: minimal change or best design

Both instincts are correct in different situations, and agents usually pick one as a
religion. Pick per task.

| Signal | Minimal change | Best design |
|---|---|---|
| The code is legacy or being replaced | ✓ | |
| The same problem appears in 3+ places | | ✓ |
| Deadline is real and the workaround is honest | ✓ | |
| The area is under active development | | ✓ |
| The fix would need a comment explaining why it is ugly | | ✓ |
| The refactor would touch unrelated files | ✓ | |

Two guardrails:

- **Never do both silently.** "Fix plus refactor" hides the refactor inside the fix.
- **Write down the deferred one.** A workaround without a follow-up note becomes the design.

When the honest answer is "the right fix is bigger than the task", say that in one
paragraph and let the user choose. That is not a failure to decide; it is the decision.

## Chapter checklist

- [ ] At least two options are compared on the same fields. (P11)
- [ ] One is recommended, with the condition under which the other wins. (P12)
- [ ] Assumptions are listed with "if false" consequences. (P13)
- [ ] One-way doors were escalated, not assumed. (P14)
- [ ] The decision and its reason are in a durable file. (P15)

## Next

[4. Contract and scope →](04-contract-and-scope.md)
