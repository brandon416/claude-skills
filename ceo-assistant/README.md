# CEO Assistant Portable Skill Pack

CEO Assistant is a host-neutral executive decision and orchestration pack built from the strongest reusable ideas in Brandon's `claude-skills` repository.

It combines five requested source areas:

1. `c-level-advisor`
2. `c-level-agents`
3. `business-operations`
4. `agents/personas`
5. `business-growth`

## What it does

Use CEO Assistant when a founder, executive, or small-business owner needs a decision, operating plan, growth plan, or cross-functional review. It frames the decision, selects only the executive lenses that add value, compares tradeoffs, and returns one prioritized recommendation with risks, assumptions, ownership, and a next action.

The pack is intentionally portable across Grok, ChatGPT and Codex, Hermes Agent, Cursor, and Claude-compatible hosts. The canonical logic lives in `skills/`. Host-specific files are thin adapters only.

## Design principles

- One canonical skill pack, not separate prompt forks for every model.
- Use the minimum useful number of executive lenses.
- Scale recommendations to the real company size and resources.
- Prefer a small number of high-leverage actions over sprawling plans.
- Never claim parallel agents ran unless the host exposes isolated workers and observable routing evidence.
- Keep external or irreversible actions behind explicit approval.
- Do not expose private reasoning. Return conclusions, evidence, assumptions, tradeoffs, and verification instead.

## Main entry points

- `skills/ceo-assistant/SKILL.md`: primary executive assistant skill.
- `skills/executive-orchestrator/SKILL.md`: capability-aware orchestration router.
- `skills/c-level-advisor/SKILL.md`: executive decision framing and tradeoffs.
- `skills/c-level-agents/SKILL.md`: selective C-suite lenses.
- `skills/business-operations/SKILL.md`: lightweight operating systems.
- `skills/business-growth/SKILL.md`: focused growth strategy and experiments.
- `skills/executive-personas/SKILL.md`: practical persona lenses without role-play theater.

## Orchestration modes

The default mode is Orbit, a sequential set of focused passes. Constellation is allowed only when the host can prove it is using isolated workers. Eclipse adds a skeptical review pass. Morph is the implementation phase after a plan is approved.

See `references/orchestration-contract.md` for the exact contract.

## Host notes

See `references/host-compatibility.md` for Grok, Codex and ChatGPT, Hermes Agent, Cursor, and Claude-compatible usage.

## Source policy

This package does not replace or destructively rewrite the requested source folders. It is an umbrella compatibility layer. `SOURCE_MAP.md` explains what was reused, normalized, and intentionally changed.
