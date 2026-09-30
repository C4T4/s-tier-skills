# s-tier-skills

**Only the skills and agents that are actually worth installing.**

There are thousands of Claude skills. Most are prompts in a trench coat. This is
the short list of ones that change what the model can actually do.

No star counts below. Popularity is not the bar — [the bar](#the-bar) is.
Every entry was checked against the GitHub API on **2026-09-30**.

---

## Run this first

### [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector)

Scans a skill repo, zip or directory for 71 vulnerability patterns across 17
categories — prompt injection, data exfiltration, MCP tool poisoning, taint
tracking, YARA rules — and emits SARIF/JSON with a 0–100 risk score.

**The delta —** it answers the question nothing else does: *is this safe to
install?* Its own dataset of 31,132 published skills found 26.1% with
vulnerabilities and 5.2% that looked outright malicious. Run it on everything
else on this page, including the entries I vouch for.

---

## The list

Single-purpose skills. Each does one hard thing.

### [cloudflare/security-audit-skill](https://github.com/cloudflare/security-audit-skill)

A six-phase codebase audit: recon → coverage-led hunting → adversarial
validation → `findings.json` → independent re-verification → report.

**The delta —** it refuses to trust its own output. Every candidate finding goes
to a *fresh* verifier whose job is to disprove it, and the `confirmed` vs
`needs_validation` split is enforced by a zero-dependency validator
(`validate-findings.cjs`), not by the model's say-so. Most audit prompts hand you
a confident list of maybes.

### [anthropics/skills](https://github.com/anthropics/skills)

The 19 official skill folders, including the real `docx` / `pdf` / `pptx` /
`xlsx` implementations that power file creation on claude.ai, plus
`mcp-builder`, `skill-creator` and `webapp-testing`.

**The delta —** these are production implementations, not reconstructions. It
also ships the `spec/` and `template/` that every other skill in this list is
written against.

### [obra/superpowers](https://github.com/obra/superpowers)

Fifteen composable skills that impose a full development methodology: spec
extraction → plan → subagent-driven execution, with `systematic-debugging`,
`verification-before-completion` and `using-git-worktrees`.

**The delta —** the skills auto-trigger, so the discipline is *enforced* rather
than remembered. Agents routinely run two hours unattended without drifting off
the approved plan.

### [OthmanAdi/planning-with-files](https://github.com/OthmanAdi/planning-with-files)

Keeps `task_plan.md`, `findings.md` and `progress.md` on disk and re-injects them
through lifecycle hooks every turn, so a plan survives `/clear`, compaction and
crashes.

**The delta —** it does not ask the model to remember; a hook fires regardless.
And it publishes numbers instead of claims: 96.7% assertion pass rate, 3/3 blind
A/B wins.

### [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills)

Twenty-five lifecycle skills behind nine slash commands — `/spec`, `/plan`,
`/build`, `/test`, `/review`, `/webperf`, `/ship` — including
`doubt-driven-development` and `interview-me`.

**The delta —** quality gates are wired to phases, so `/build auto` still commits
each task test-driven and halts on failure. Automation that does not quietly
drop verification on the way.

### [blader/humanizer](https://github.com/blader/humanizer)

Rewrites AI-sounding prose against 26 patterns taken from Wikipedia's "Signs of
AI writing" — not-X-but-Y constructions, the one-line closer, the staged run-up —
without changing meaning.

**The delta —** the rule set is externally grounded rather than invented, and the
author ran a blind test (16/16 judge preference) instead of asserting "better
writing".

### [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills)

Six skills teaching agents Obsidian's actual file formats: Obsidian Flavored
Markdown, `.base` files, JSON Canvas, the Obsidian CLI, Defuddle, Knap.

**The delta —** written by Obsidian's CEO against the format specs themselves.
Format-level ground truth beats whatever the model absorbed from scraped docs.

---

## Benches

Large collections that are genuinely maintained. **Copy the one folder you need,
not the lot** — loading forty skills you never call is the exact failure mode
this list exists to prevent.

| Repo | What's in it | Take it for |
|---|---|---|
| [wshobson/agents](https://github.com/wshobson/agents) | 202 agents, 184 skills, 105 commands, generated from one Markdown source | Native artifacts per harness (Claude Code, Codex, Cursor, OpenCode, Copilot) instead of lowest-common-denominator ports |
| [trailofbits/skills-curated](https://github.com/trailofbits/skills-curated) | Plugins code-reviewed by Trail of Bits staff: `scv-scan` (36 Solidity vuln classes), `ghidra-headless`, `wooyun-legacy` (88,636 cases) | The only vetted-by-a-security-firm allowlist |
| [VoltAgent/awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) | 161 subagent `.md` files in 10 categories | Real agent definitions in a consistent taxonomy; promo PRs get rejected |
| [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | 168 research skills, 100+ scientific databases — cancer genomics, AlphaGenome, PK/PD modelling, docking, DICOM | Peer-reviewed provenance (arXiv:2609.00065) plus CI skill-tests |
| [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | 8 skills incl. `vercel-optimize` and `react-best-practices` | Pulling metrics *before* reading code — the right order, and rare |

### First-party vendor skills

Worth knowing because API surfaces are the thing model weights get wrong fastest.

- [google/skills](https://github.com/google/skills) — auth recipes, Agent Platform (deploy/tune/eval/RAG), BigQuery AI/ML, Genkit.
- [microsoft/skills](https://github.com/microsoft/skills) — 175 skills for Azure SDKs and AI Foundry. Its README explicitly warns against installing them all. Unusually honest.
- [NVIDIA/skills](https://github.com/NVIDIA/skills) — Physical AI, robotics, simulation, CUDA, RAG; signed through NVIDIA's Verified Skills pipeline.

---

## Plumbing

- **[vercel-labs/skills](https://github.com/vercel-labs/skills)** — the `npx skills` CLI. Installs any `SKILL.md` source (GitHub, GitLab, Azure, any git remote) into 79 different agents; `skills use` runs one without installing it. Most entries above document it as their install path.
- **[agentskills/agentskills](https://github.com/agentskills/agentskills)** — the Agent Skills spec itself. The `SKILL.md` format everything here targets.

---

## Cut, and why

The bar only means something if things fail it. Frequently recommended,
deliberately not listed:

| Repo | Reason |
|---|---|
| `contains-studio/agents` | No push since 2025-07-28 — ~14 months stale (test 5) |
| `iannuttall/claude-agents` | Archived. Successor is [`iannuttall/dotagents`](https://github.com/iannuttall/dotagents) |
| `travisvn/awesome-claude-skills` | Last push 2026-04-28 — five months stale |
| `simonw/claude-skills` | A genuinely interesting dump of `/mnt/skills`, but it reflects a nine-month-old environment |
| `anthropics/claude-code` | Real and active, but it is the CLI product repo, not a skills library |

**Exhaustive lists**, if breadth is what you want rather than a shortlist:
[hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) ·
[ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) ·
[VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)

---

## The bar

Five tests. All five, or it does not go in.

| # | Test | Fails when |
|---|---|---|
| 1 | **Does one hard thing** | It has an internal menu of forty things |
| 2 | **Beats the base model** | Claude does it just as well without the skill |
| 3 | **Runs, doesn't advise** | It is entirely "consider whether…" |
| 4 | **Earns its context** | The preamble costs more than the payload |
| 5 | **Alive, or finished** | Abandoned with known bugs |

Full criteria, automatic rejections, and how entries leave:
**[CONTRIBUTING.md](CONTRIBUTING.md)**.

---

## Installing

Skills are folders containing a `SKILL.md`:

```sh
# available in every project
git clone <repo> ~/.claude/skills/<skill-name>

# or scoped to one project
git clone <repo> .claude/skills/<skill-name>
```

Then describe your task — Claude loads a skill when its description matches what
you asked for. Agents are single `.md` files with YAML frontmatter in
`~/.claude/agents/`.

Or use the CLI, which handles every source and target harness:

```sh
npx skills add <github-repo-or-url>
```

---

## Nominating

Open an issue with the [nomination template](.github/ISSUE_TEMPLATE/nominate.yml).

One field decides it: **the delta** — what the skill produced that the base model
did not. Paste both outputs. Nominations without a delta are closed without
discussion. That is not rudeness; it is the only thing keeping the list short.

---

MIT — see [LICENSE](LICENSE). Entries link to their authors' repos and keep their
own licences.
