# AGENTS.md

Repository guide for agents working on this book.

## What this repo is

A process reference for AI coding agents: `PRINCIPLES.md` (25 rules), `CHECKLIST.md`
(the same rules as checkpoints), `README.md` (human entry point), and this file (machine
entry point).

It contains no code, no build step, and no tests. The only artifact is Markdown.

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
| Explain a rule to someone | `PRINCIPLES.md` | The matching row in `CHECKLIST.md` |
| Review agent output and name the failure | `CHECKLIST.md` → Anti-patterns | The cited `P#` in `PRINCIPLES.md` |
| Add or rewrite a principle | `PRINCIPLES.md` | Style rules below |
| Add a checkpoint | `CHECKLIST.md` | Confirm it cites an existing `P#` |
| Improve onboarding | `README.md` | `AGENTS.md` (this file) |

## Writing style

- One idea per rule. If a rule needs "and also", it is two rules.
- **Do** under 60 words. **Why** one sentence tied to a failure cost. **Don't** one concrete counter-example.
- No filler: no "it is worth noting", "as mentioned", "of course", "simply".
- Prefer a command, a path, or an observation over an adjective.
- Keep numbering stable. Renumbering breaks every citation in `CHECKLIST.md`.

### Rule template

```markdown
### P<n>. Short imperative title

**Do** — the action.

**Why** — the failure it prevents.

**Don't** — a concrete way to get it wrong.

<!-- provenance: capability name, not a file path -->
```

## Sanitization (mandatory)

This repository is public. Never commit the following.

1. Machine paths: real home directories, drive letters, internal mount points.
2. Personal data: real names, emails, usernames, hostnames, internal domains.
3. Credentials: API keys, tokens, passwords, private keys, `.env` contents, backup files.
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
2. Every `P#` reference resolves to an existing rule.
3. The change is limited to the files the task names.
4. The greps below return no unexpected hits.

## Pre-commit checks

```bash
# Machine paths
grep -rnE '/(home|Users)/[A-Za-z0-9._-]+|[~]/[A-Za-z0-9._-]+' --include='*.md' .

# Credential shapes
grep -rnE '(sk-[A-Za-z0-9]{10,}|ghp_[A-Za-z0-9]{10,}|BEGIN [A-Z ]*PRIVATE KEY|password[[:space:]]*[:=])' --include='*.md' .

# Hostnames and IPs (example.com is fine, anything else is not)
grep -rnE '([a-z0-9-]+\.){2,}[a-z]{2,}|([0-9]{1,3}\.){3}[0-9]{1,3}' --include='*.md' .
```

The first two must return nothing. The third may match `example.com` placeholders only.

## Session hygiene

- Do not commit, push, or rewrite history unless asked.
- Review `git status` and `git diff` before staging.
- Leave unrelated files alone, including files you did not create.
