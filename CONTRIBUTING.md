# The bar

Most lists optimise for length. This one optimises for the opposite: every entry
you remove makes the remaining ones worth more.

An entry gets in only if it passes **all five** tests. One failure is a rejection.
Nominate with the [issue template](.github/ISSUE_TEMPLATE/nominate.yml).

---

### 1. It does one hard thing

Not a bundle. If the skill needs an internal menu — "for X do this, for Y do
that" — it is a collection wearing a skill's clothes. Split it or skip it.

> Passes: "audit this codebase for security vulnerabilities."
> Fails: "a suite of 40 developer productivity skills."

### 2. It beats the base model

Run the task twice: once with the skill, once without. If the outputs are
comparable, the skill is a prompt, and a prompt is not worth a repo entry.

The delta has to be visible to someone who did not write the skill.

### 3. It runs, it doesn't advise

S-tier skills ship something that executes: a script, a checklist with defined
pass/fail, a reference file with real values, a schema. A skill made entirely of
"consider whether…" and "it is important to…" is a vibe, not a tool.

> Passes: a validator you can run against your palette.
> Fails: "remember to think about accessibility."

### 4. It earns its context

Skills are loaded into a finite window. An entry must be worth more than the
tokens it costs. Bloated preamble, restated best practices, and motivational
framing all count against it.

### 5. It is alive, or finished

Pushed within ~90 days, **or** so complete that it does not need pushes. An
abandoned repo with open correctness bugs fails. A four-file skill that has been
right since the day it shipped passes.

---

## Automatic rejections

- Lists of lists. Aggregators of aggregators.
- Prompt packs renamed to skills after the fact.
- "Act as a senior engineer" with extra steps.
- Anything that can't be run, only read.
- Anything whose README is longer than its implementation.
- Self-promotion where the author is the only user.

---

## How to nominate

Open an issue with the template and answer three things concretely:

1. **What it does** — one sentence, a capability, no adjectives.
2. **The delta** — what it produced that the base model did not. Paste both if
   you can. This is the part that decides it.
3. **Which test it passes hardest** — and be honest about the weakest one.

Nominations without a delta are closed without discussion. That is not rudeness;
it is the only thing keeping the list short.

## How entries leave

Entries are re-checked periodically. An entry is removed when the repo is
archived, when it drifts past the maintenance line, or when the base model
catches up and test 2 stops passing. Removals are logged in the commit history,
not hidden.

Being removed is not a judgement on the author. The bar moves because the model
moves.
