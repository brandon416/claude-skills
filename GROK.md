# Grok Build — C-Suite Plugin

This overlay makes the C-level, BizOps, growth, and persona packs in
[`brandon416/claude-skills`](https://github.com/brandon416/claude-skills)
installable and well-behaved on **Grok Build**, without breaking Codex,
ChatGPT, Hermes Agent, or Cursor.

Grok already reads Claude skills (`SKILL.md`, `.claude-plugin/`). This file
exists so Grok, and every other agent you paste this repo into, uses the
**same entry points** and does not depend on `~/.claude/` paths.

## What we added (Grok-native)

| Path | Purpose |
|---|---|
| `grok-skills/skills/orchestrate/SKILL.md` | `/orchestrate` — chief-of-staff router |
| `grok-skills/skills/ceo-assistant/SKILL.md` | `/ceo-assistant` — CEO seat + time leverage |
| `grok-skills/agents/*.md` | 13 C-suite voices, Claude tool lists stripped |
| `grok-skills/AGENTS.md` | Cursor / Hermes / Codex project rules |
| `.grok-plugin/plugin.json` | Root Grok plugin manifest |
| `.grok-plugin/marketplace.json` | Marketplace of the 5 packs + overlay |
| `*/.grok-plugin/plugin.json` | Per-pack Grok manifests |

Canonical depth still lives in the original packs. Do not fork those files
just to add Grok frontmatter — Claude's `CONVENTIONS.md` forbids extra YAML.

## Packs in this marketplace

1. **c-suite** (`grok-skills/`) — overlay. Install this first.
2. **c-level-skills** (`c-level-advisor/`) — 34 advisor skills (CEO, CFO, COO, …)
3. **c-level-agents** (`c-level-agents/`) — founder-mode `/cs:*` commands + agents
4. **business-operations-skills** (`business-operations/`)
5. **business-growth-skills** (`business-growth/`)
6. **personas** (`agents/personas/`) — loaded as agent voices, not a plugin

## Install on Grok Build

From a clone of this repo:

```bash
grok plugin install ./grok-skills --trust
grok plugin enable c-suite
```

Or install the marketplace, then the packs you want:

```bash
grok plugin marketplace add brandon416/claude-skills
grok plugin install c-suite --trust
grok plugin install c-level-skills --trust
grok plugin install c-level-agents --trust
grok plugin install business-operations-skills --trust
grok plugin install business-growth-skills --trust
```

User-level copy (Grok Skills UI / `~/.grok/skills/`):

```bash
cp -R grok-skills/skills/orchestrate ~/.grok/skills/
cp -R grok-skills/skills/ceo-assistant ~/.grok/skills/
```

Slash commands after install: `/orchestrate`, `/ceo-assistant`, `/cs:founder-mode`,
`/cs:boardroom`, `/cs:brief`, `/cs:decide`, `/cs:execute`.

## Install on Codex / ChatGPT

Codex already has `.codex-plugin/plugin.json` and `.codex/skills/` symlinks.
Point the session at this repo and pin these two files in the prompt:

- `grok-skills/skills/orchestrate/SKILL.md`
- `grok-skills/skills/ceo-assistant/SKILL.md`

ChatGPT: attach those two files plus any advisor `SKILL.md` the router names.
Custom GPT instructions can be the body of `grok-skills/AGENTS.md`.

## Install on Cursor

Drop `grok-skills/AGENTS.md` at the project root (or merge it). Cursor walks
`AGENTS.md` the same way Grok does. Skills stay in-repo; no extra marketplace.

## Install on Hermes Agent

Hermes already indexes via `.hermes/skills/`. Add:

```
grok-skills/skills/orchestrate
grok-skills/skills/ceo-assistant
```

to the Hermes skills path. Agent voices: `grok-skills/agents/`.

## How to use

```
/orchestrate should we raise now or cut burn?
/ceo-assistant my calendar is 12 hours of sessions and I need leverage
/cs:boardroom pricing change that hits sales, finance, and brand
```

The overlay:

- Routes instead of dumping 70 skills into context
- Writes decisions to `.grok/decisions/` (Grok), `.codex/decisions/` (Codex),
  or `decisions/` (everyone else) — never `~/.claude/`
- Uses Grok connectors (Calendar, Gmail, Drive) when the question needs
  live company data; other runtimes use the filesystem
- Speaks in forcing questions, not compliments

## Descriptions (short, for skill libraries)

| Skill | Description |
|---|---|
| **orchestrate** | Chief-of-staff router. One messy question in; the right C-suite room out. Boardroom if two or more chairs light up. |
| **ceo-assistant** | CEO seat with CoS discipline. Strategy, capital, board narrative, time leverage. Delegates everything else. |
| **c-level-advisor** | 34 executive skills: 14 C-suite chairs, orchestration, strategy, culture. |
| **c-level-agents** | 13 persona agents + 21 `/cs:*` commands (founder-mode, boardroom, office-hours, decide, execute). |
| **business-operations** | Internal BizOps: process, vendors, capacity, knowledge, procurement, change comms. |
| **business-growth** | External revenue: CS, sales engineering, RevOps, contracts. |
| **personas** | Seven operator voices (solo founder, startup CTO, PM, growth, finance, content, DevOps). |

## Do not

- Rewrite original `SKILL.md` frontmatter (Claude CI rejects extra keys)
- Assume Bash/Grep/Glob or `model: opus`
- Load the whole board for a one-domain question
