# AGENTS.md

Repository guide for agents working on this book.

## What this repo is

A process reference for AI coding agents. Markdown only: no code, no build step, no
tests.

```
00-mental-model.md      the loop and why the order matters
01..08-*.md             chapters, one per stage or behavior
PRINCIPLES.md           index: 25 rules, one line each, linked
CHECKLIST.md            the rules as checkpoints, by phase
appendix/               templates, anti-patterns, provenance
```

Rule numbers `P1`–`P25` are stable identifiers. Chapter 6 is procedure and adds no rules.

## Instruction priority

When instructions conflict:

1. The user's request.
2. Runtime and system instructions.
3. This file.
4. Conventions already present in the file being edited.
5. General writing practice.

## Routing: task → where to look

| Task | Read first | Then |
|---|---|---|
| Add a new rule | The chapter that owns its stage | `PRINCIPLES.md` row, `CHECKLIST.md` checkpoint |
| Rewrite an existing rule | Its chapter | Confirm nothing else cites its number |
| Add a decision table | The relevant chapter's "tension" section | Keep it to two columns of conditions |
| Add an anti-pattern | `appendix/anti-patterns.md` | Link it to a `P#` |
| Add or change a template | `appendix/templates.md` | Keep it copy-pasteable |
| Review agent output | `CHECKLIST.md` | `appendix/anti-patterns.md` |
| Improve onboarding | `README.md` | This file |

## Adding a rule

A rule is added only after a real failure traced to it. Then:

1. Pick the chapter that owns the stage. Chapters map to the loop: align, read, decide,
   contract, execute, fail, persist, communicate.
2. Write the heading `### P<n>. Short imperative title`, reusing the next free number.
3. Fill **Do** (under 60 words), **Why** (one sentence, tied to a cost), **Don't** (one
   concrete counter-example).
4. Add a row to `PRINCIPLES.md` with a working anchor link.
5. Add at least one checkpoint to `CHECKLIST.md`.
6. Add a provenance row to `appendix/provenance.md`, in capability terms.

Never renumber. A retired rule leaves a gap, because every checklist citation depends on
the number.

### Rule template

```markdown
### P<n>. Short imperative title

**Do** — the action.

**Why** — the failure it prevents.

**Don't** — a concrete way to get it wrong.
```

## Writing style

- One idea per rule. If it needs "and also", it is two rules.
- Prefer a command, a path, or an observation over an adjective.
- No filler: no "it is worth noting", "as mentioned", "of course", "simply".
- Two-column comparison tables use the same fields on both sides.
- 60-em dash (`—`) in rule bodies, no smart quotes in headings (they break anchors).

### Anchors matter

GitHub anchors come from the heading text: lowercase, punctuation dropped, spaces to
hyphens. `### P7. Never invent paths, commands, or APIs` becomes
`#p7-never-invent-paths-commands-or-apis`. If a heading changes, every link to it must
change in the same commit.

## Sanitization (mandatory)

This repository is public. Never commit the following.

1. Machine paths: real home directories, drive letters, internal mount points.
2. Personal data: real names, emails, usernames, hostnames, internal domains.
3. Credentials: API keys, tokens, passwords, private keys, `.env` contents, backups.
4. Internal services: private hostnames, IP addresses, ports, organization names, provider IDs.
5. Session artifacts: temporary files, tool logs, local config dumps.

Allowed substitutes:

| Instead of | Write |
|---|---|
| A real absolute path | `/path/to/repo`, `<project-root>` |
| A real address | `user@example.com` |
| A real key | `<your-api-key>`, `sk-REDACTED` |
| A real host | `https://example.com` |

## Definition of done for an edit here

1. The rule states an action, a reason, and a counter-example.
2. Every `P#` reference resolves, and every anchor link points at a real heading.
3. `PRINCIPLES.md`, `CHECKLIST.md`, and the owning chapter agree on the same number.
4. The change is limited to the files the task names.
5. The greps below return no unexpected hits.

## Pre-commit checks

```bash
# Machine paths
grep -rnE '/(home|Users)/[A-Za-z0-9._-]+|[~]/[A-Za-z0-9._-]+' --include='*.md' .

# Credential shapes
grep -rnE '(sk-[A-Za-z0-9]{10,}|ghp_[A-Za-z0-9]{10,}|BEGIN [A-Z ]*PRIVATE KEY|password[[:space:]]*[:=])' --include='*.md' .

# Hostnames and IPs (example.com placeholders are fine, nothing else)
grep -rnE '([a-z0-9-]+\.){2,}[a-z]{2,}|([0-9]{1,3}\.){3}[0-9]{1,3}' --include='*.md' .

# Broken relative links (paths only; anchors need the heading check)
grep -rhoE '\]\([^)#]+\.md' --include='*.md' . | sed 's/^](//' | sort -u
```

The first two must return nothing. The third may match `example.com` only. For the fourth,
confirm each path exists relative to the file that links it.

## Session hygiene

- Do not commit, push, or rewrite history unless asked.
- Review `git status` and `git diff` before staging.
- Leave unrelated files alone, including files you did not create.
- One concern per commit. Mixed commits cannot be reverted selectively.
