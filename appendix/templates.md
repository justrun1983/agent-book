# Templates

Copy-paste starting points. Keep them short; a template longer than the work it describes
will not be used.

- [Task contract](#task-contract)
- [Decision note](#decision-note)
- [Execution spec](#execution-spec)
- [Blocker report](#blocker-report)
- [Change report](#change-report)
- [Handoff](#handoff)
- [Agent message envelope](#agent-message-envelope)

---

## Task contract

Use for anything longer than one file, or anything with a real chance of scope drift.

```markdown
Goal: <one sentence>
Done when:
1. <checkable criterion>
2. <checkable criterion>
In scope: <files, modules, endpoints>
Out of scope: <what you will not touch>
Assumptions: <unverified, with the consequence if false>
Open question: <the one thing you cannot decide alone, or "none">
```

---

## Decision note

Lives next to the code or in the project's decision log.

```markdown
## Decision: <short name>
Date: <YYYY-MM-DD>
Options: <A> (chosen) vs <B>
Why: <the reason, tied to a constraint>
Assumption: <what would make this wrong>
Revisit if: <the trigger>
```

Four to six lines. If it needs more, the decision is not one decision.

---

## Execution spec

Use when work will be done by someone who did not participate in the discussion.

```markdown
# Execution: <topic>

## Goal
<one paragraph, written for someone who has not seen the conversation>

## Scope
In:  <paths or modules>
Out: <explicit exclusions>

## Steps
1. <action> — done when <observable result>
2. <action> — done when <observable result>

## Definition of done
- [ ] <criterion, checkable by command or observation>
- [ ] <criterion>
- [ ] Tests added or updated: <path>
- [ ] Doc updated: <path, or "none required because ...">

## Commands
Build: <command or N/A>
Test:  <command or N/A>
Lint:  <command or N/A>

## Risks
<what could go wrong, and the mitigation>

## If blocked
Stop. Report: what failed, exact error, what is needed.
```

---

## Blocker report

```markdown
Blocked: <what cannot proceed, one line>

Tried:
1. <action> → <exact error>
2. <action> → <exact error>

Cause: <specific cause, or "unknown">

Need: <decision, credential, file, or answer>

Suggested next: <pick one option; name the alternative>
```

---

## Change report

```markdown
## What changed
<files and behavior, not a narrative>

## Why
<the goal it serves>

## How it was verified
- Tests: <command> → <result>
- Build: <command> → <result>
- Manual: <what you did and saw>
- Not verified: <what you could not check>

## Deviations
<anything that differs from the request or plan, and why>

## Follow-ups
<named, not implied>
```

---

## Handoff

```markdown
Goal: <one sentence>
State: <done / not done / files>
Tried: <approaches and results>
Blocked by: <the specific unknown, or "nothing">
Next: <single next action, with path or command>
Read first: <the one file that matters most>
```

---

## Agent message envelope

For agent-to-agent messages outside a shared context.

```yaml
kind: propose | review | result | blocked
topic: <stable thread id>
summary: <one line claim>
evidence:
  - <path or command output>
ask: <the specific thing you need back>
state: open | accepted | rejected | done
```

Only the owner of a topic changes `state`. A thread ends with `done` or `rejected` plus
a reason.
