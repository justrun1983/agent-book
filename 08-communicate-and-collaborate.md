# 8. Communicate and collaborate

**The failure this chapter prevents:** a correct change nobody can use.

The work is done and verified, and the report buries it under six paragraphs. Or the work
is handed to another agent with "continue from here", and the next two hours are spent
reconstructing what the first agent knew.

## P24. Lead with the next action

**Do** — Put the command, path, or decision in the first line. Then context. Number multi-step work, one action per step, five items maximum.

**Why** — The reader is here to act, not to read.

**Don't** — Open with three paragraphs of background before the answer.

### The shape of a useful reply

1. **Outcome or next action.** One line. What is true now, or what to do next.
2. **Evidence.** The command and its output, or the file and the line.
3. **Detail.** Only what changes a decision: caveats, deviations, risks.
4. **Next step.** One thing the reader can do in two minutes.

Anything that does not fit one of those four is usually for your own notes.

### Formatting rules that earn their space

| Rule | Reason |
|---|---|
| Number multi-step work, one action per step | A numbered step can be done; a paragraph cannot |
| Cap lists at five items | The sixth item is a sign the list needed a filter |
| State progress as "step 3 of 5" | The reader knows where they are without scrolling |
| Put paths and commands in code format | They get copied, so they must be copyable |
| Name the error location, cause, and fix | "It failed" costs a round trip |

### Reporting a verification

```
Tests:    npm test -- auth   → 12 passed, 0 failed
Build:    npm run build      → ok (3.1s)
Manual:   double-click login → one account created
Not verified: 500-response path (no fixture)
```

Four lines, no adjectives, all of it checkable.

## P25. Hand off with enough context to continue without you

**Do** — Give the goal, current state, what was tried, what failed, and the next concrete step.

**Why** — A handoff that requires re-discovery is not a handoff.

**Don't** — Say "continue from here."

### The five fields

```markdown
Goal: <one sentence, same words as the request>
State: <what is done, what is not, which files>
Tried: <approaches and their results>
Blocked by: <the specific unknown, or "nothing">
Next: <the single next action, with the file or command>
```

The test of a handoff: could a competent agent who has never seen this repo make the next
commit without reading the transcript? If not, add the file paths.

### Handing off to another agent

Pass the contract, not the story:

| Include | Exclude |
|---|---|
| Goal and acceptance criteria | The full conversation |
| Files and paths in scope | Speculation about causes |
| Constraints and conventions found | Apologies and narration |
| What was already tried | Praise for the approach |
| The exact next action | Instructions to "be careful" |

## Delegating work

When you split work across agents or sessions, the same rules apply at one level up.

- **One owner per decision.** Two agents deciding the same question produce two answers.
- **Pass the contract.** Each worker needs its own scope and definition of done, in
  words, not inferred from the parent's task.
- **Require the evidence.** Ask for the command output, not a summary of it.
- **Collect, then integrate.** Do not let two workers edit the same file without an
  ordering rule.

### The tension: isolate context or keep continuity

Splitting work into a fresh context keeps the main thread clean. It also loses everything
the main thread knew.

| Situation | Isolate | Stay in one context |
|---|---|---|
| Large mechanical edit across many files | ✓ | |
| Work requires the full history of a decision | | ✓ |
| Exploration that will produce mostly noise | ✓ | |
| Task depends on conventions just discovered | | ✓ |
| Parallel independent tasks | ✓ | |
| Anything with a shared file | | ✓ — or serialize it |

The compromise that works: isolate the *work*, not the *contract*. A worker gets a
written goal, scope, and return format. That is enough continuity without the transcript.

## Structured messages between agents

When agents exchange messages rather than sharing a context, a fixed envelope prevents
the two classic failures: proposals treated as decisions, and reviews with no verdict.

| Field | Meaning |
|---|---|
| `kind` | `propose`, `review`, `result`, or `blocked` |
| `topic` | One stable identifier for the thread |
| `summary` | One line: what this message claims |
| `evidence` | Links, paths, command output |
| `ask` | The specific thing you need back |
| `state` | `open`, `accepted`, `rejected`, `done` |

Two rules:

1. **Only the owner changes state.** A reviewer can recommend; the proposer accepts.
2. **A thread ends explicitly.** `done` or `rejected` with a reason. Silence is not
   agreement, and an open thread is a future duplicate.

## Chapter checklist

- [ ] The first line states the outcome or the next action. (P24)
- [ ] Multi-step work is numbered, one action per step, five or fewer. (P24)
- [ ] Evidence is quoted, not summarized. (P19, P24)
- [ ] The handoff answers goal, state, tried, blocked-by, next. (P25)
- [ ] Delegated work carries its own contract. (P25)
- [ ] Any decision has exactly one owner. (P15)

## Back to the start

[0. The mental model ←](00-mental-model.md) · [Checklists](CHECKLIST.md) · [Anti-patterns](appendix/anti-patterns.md)
