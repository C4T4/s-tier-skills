# S-Tier Skills

> Only the Claude skills that are actually worth installing.

There are thousands of agent skills. Most are prompts in a trench coat. Four here,
each with the before/after that shows what it actually changes. If you can't see
the difference, it doesn't belong on the list.

## Contents

- [Engineering](#engineering)
- [Security](#security)
- [Writing](#writing)
- [Accessibility](#accessibility)
- [The bar](#the-bar)
- [Install](#install)
- [Contribute](#contribute)

## Engineering

### [superpowers](https://github.com/obra/superpowers)

Spec → plan → execute, with the verification step it can't skip.

> **You:** *Add rate limiting to the API*

| Without | With |
|---|---|
| Writes a middleware. Says **"Done! ✅"**. It is untested and the limit is wrong. | Asks 6 questions → writes `spec.md` → 9-task plan → runs in a git worktree → each task test-first → **halts at task 4** because the test genuinely fails. |

The win: it can't tell you it's finished when it isn't.

## Security

### [security-audit-skill](https://github.com/cloudflare/security-audit-skill)

Every finding goes to a second agent whose only job is to disprove it.

> **You:** *Audit this repo*

| Without | With |
|---|---|
| 32 "potential vulnerabilities". You spend 3 hours finding out 28 are noise. | `findings.json`: **4 confirmed**, 9 need validation, 19 discarded — a fresh agent disproved them. You read 4. |

The win: you get a triage list, not homework.

## Writing

### [humanizer](https://github.com/blader/humanizer)

Strips the 26 tells of AI prose. Meaning unchanged.

**Before**

> It's not just a bug fix — it's a fundamental rethinking of how the auth layer
> handles session state. Let's dive into what makes this approach so powerful.

**After**

> The fix changes how the auth layer stores session state.

The win: nobody can tell. 28 words → 11.

## Accessibility

### [i-have-adhd](https://github.com/ayghri/i-have-adhd)

Stops the agent burying the answer.

**Before**

> Great question! There are a few different approaches you could take here. Your
> test suite has several moving pieces, and it's worth considering how they
> interact before making changes. One option would be to…

**After**

> Run `npm test -- auth.spec.ts`
> Fails at line 42: expected 200, got 401.
> Fix: add the `Authorization` header.

The win: the answer is the first line, every time.

## The bar

Five tests. All five, or it does not go in.

| Test | Fails when |
|---|---|
| Does one hard thing | It has an internal menu of forty things |
| Beats the base model | Claude does it just as well without the skill |
| Runs, doesn't advise | It is entirely "consider whether…" |
| Earns its context | The preamble costs more than the payload |
| Alive, or finished | Abandoned with known bugs |

## Install

```sh
npx skills add https://github.com/obra/superpowers
npx skills add https://github.com/cloudflare/security-audit-skill
npx skills add https://github.com/blader/humanizer
npx skills add https://github.com/ayghri/i-have-adhd
```

Or clone into `~/.claude/skills/` for every project, `.claude/skills/` for one.

## Contribute

Nominations welcome — [read the bar first](CONTRIBUTING.md), then
[open an issue](https://github.com/C4T4/s-tier-skills/issues/new?template=nominate.yml).

One field decides it: the before/after. No before/after, no entry.

## License

[MIT](LICENSE). Entries link to their authors' repos and keep their own licences.
