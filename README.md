# Awesome S-Tier Skills [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Only the Claude skills that are actually worth installing.

There are thousands of agent skills. Most are prompts in a trench coat. This list
stays short on purpose — an entry is added only when it clears [the bar](#the-bar),
and removed the moment it stops.

## Contents

- [Engineering](#engineering)
- [Security](#security)
- [Writing](#writing)
- [Accessibility](#accessibility)
- [The bar](#the-bar)
- [Install](#install)
- [Contribute](#contribute)

## Engineering

- [superpowers](https://github.com/obra/superpowers) - Composable skills that impose a full development methodology: spec → plan → subagent execution, with systematic debugging and verification-before-completion. They auto-trigger, so the discipline is enforced rather than remembered.

## Security

- [security-audit-skill](https://github.com/cloudflare/security-audit-skill) - Six-phase codebase audit that sends every candidate finding to a fresh verifier whose job is to disprove it. Confirmed vs. unverified is machine-checked, not asserted.

## Writing

- [humanizer](https://github.com/blader/humanizer) - Removes the 26 tells of AI-generated prose — not-X-but-Y, the one-line closer, the staged run-up — without changing meaning. Rules drawn from Wikipedia's "Signs of AI writing", not invented.

## Accessibility

- [i-have-adhd](https://github.com/ayghri/i-have-adhd) - Stops the agent burying the answer. Leads with the next action, numbers the steps, cuts the preamble and the closing pleasantries.

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
npx skills add <repo-url>
```

Or clone into `~/.claude/skills/` for every project, `.claude/skills/` for one.

## Contribute

Nominations welcome — [read the bar first](CONTRIBUTING.md), then
[open an issue](https://github.com/C4T4/s-tier-skills/issues/new?template=nominate.yml).

One field decides it: what the skill produced that the base model did not.

## License

[MIT](LICENSE). Entries link to their authors' repos and keep their own licences.
