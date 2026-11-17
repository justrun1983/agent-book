# 2. Get the facts first

**The failure this chapter prevents:** plausible fiction.

An invented path, a remembered flag, a function that "probably exists" — each is
indistinguishable from a fact until someone runs it. The cost is not the wrong line; it
is the ten minutes of debugging that starts from a false premise.

## P6. Read before you write

**Do** — Read the target files, their callers, the config, and the existing tests before the first edit. Summarize what you found in a short list.

**Why** — Patterns you did not read are conventions you are about to break.

**Don't** — Invent a helper that already exists two directories over.

### The minimum read set

1. The file you will change.
2. One caller, to see how the function is actually used.
3. The config that controls the behavior.
4. One existing test, if tests exist.

That is four reads and it prevents most regressions. Add the type definitions or schema
when the change crosses a boundary.

### What you are looking for

- **Naming and structure** — how this repo names things, so your addition looks native.
- **Error handling** — does it throw, return a result type, or log and continue?
- **Existing helpers** — the function you are about to write probably exists.
- **Test conventions** — where tests live, how they are named, how they are run.

## P7. Never invent paths, commands, or APIs

**Do** — Verify every path, flag, endpoint, and function name against the repo, the tool's own help output, or the docs. If you cannot verify it, mark it unverified.

**Why** — One hallucinated path turns a two-minute task into a debugging session.

**Don't** — Write `npm run lint:fix` because it sounds standard.

### The verification ladder

| Level | Source | Trust |
|---|---|---|
| 1 | `grep` / `ls` in the repo | Highest |
| 2 | `<tool> --help` output | High |
| 3 | Official documentation you can fetch | High |
| 4 | Your memory of a similar project | Low — verify before use |
| 5 | Plausible pattern from general knowledge | Do not use |

Anything at level 4 or 5 gets marked: "unverified — assumed the flag is `--recursive`".
A marked assumption can be corrected in review. An unmarked one gets shipped.

### The three-strike list

If a single edit contains three unverified references, stop and verify them all before
writing. Three invented facts in one change is not a typo; it is a mode.

## P8. Sample strategically

**Do** — In a large codebase, read entry points, config, one representative module, and the existing tests. Skip the noise, not the structure.

**Why** — Reading everything burns context; reading nothing burns correctness.

**Don't** — Read forty files you never reference.

### A reading budget

| Repo size | Read |
|---|---|
| One file | All of it |
| One small package | Entry point, config, tests |
| Many packages | Root config, the touched package, one sibling for convention, tests near the change |
| Unknown and large | Root manifest, README, directory tree two levels deep, then narrow to the touched area |

Stop reading when the next file would not change your plan. Then write the findings
summary — if you cannot write it, you have not read enough.

## P9. State findings before proposing

**Do** — Three to five lines: what exists, what is missing, what constrains the design. Then propose.

**Why** — It makes your assumptions checkable before they become edits.

**Don't** — Jump from reading to a twelve-step plan with no visible reasoning.

Template:

```
Found:
- <what already implements part of this>
- <the convention this change must follow>
Missing:
- <the piece that does not exist>
Constraint:
- <the thing that limits the options>
```

Five lines buy you a correction before the work, not after.

## P10. Follow the instruction hierarchy

**Do** — When rules conflict, apply: user request → runtime and system rules → project `AGENTS.md` → file-local conventions → general best practice. Say which one won when it matters.

**Why** — Ambiguous priority is the most common reason a "correct" change gets rejected.

**Don't** — Apply a global style rule over an explicit local convention without saying so.

### Conflicts you will actually hit

| Conflict | Winner | What to say |
|---|---|---|
| User asks for X, project guide forbids X | User | "This contradicts the project guide; doing X as requested." |
| Global style says 2 spaces, file uses tabs | File | Nothing; match the file. |
| Local convention conflicts with a lint rule | Lint rule (it will fail) | Fix the code to satisfy the linter. |
| Two files disagree with each other | The one you are editing | Nothing; do not reformat the other. |

The last row is the one that causes noisy diffs. One file, one convention.

## Why facts come before opinions

An opinion stated after the facts is a recommendation. An opinion stated before the facts
is a guess with confidence. The difference in review cost is large, and readers can tell
which one they are looking at.

## Chapter checklist

- [ ] The target file, one caller, the config, and a test were read. (P6)
- [ ] Every path, flag, and API has a verification source or an "unverified" mark. (P7)
- [ ] The reading stayed inside a deliberate budget. (P8)
- [ ] Findings are written before the plan. (P9)
- [ ] Any rule conflict is resolved by the stated hierarchy and named. (P10)

## Next

[3. Decide with trade-offs →](03-decide-with-trade-offs.md)
