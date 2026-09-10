# Host Compatibility

The canonical skill format is `SKILL.md` with YAML frontmatter. Keep business logic there. Host adapters should stay thin.

## Grok

Grok can discover skills from plugin `skills/` directories and from configured skill paths. The `.grok-plugin/plugin.json` file describes this package. Grok-specific behavior should not override the canonical business workflow.

If Grok exposes isolated subagents, Constellation may be used. Otherwise use Orbit.

## ChatGPT and Codex

Use the skill bundle as a reusable skill package or provide the relevant `SKILL.md` and reference files as context. Keep `AGENTS.md` available when the work happens inside a repository.

Do not assume API credentials or a specific model. Use the tools and permissions actually available in the current ChatGPT or Codex surface.

## Cursor

Cursor supports Agent Skills built around `SKILL.md`. The included `.cursor/rules/ceo-assistant.mdc` is only a routing hint. The canonical instructions remain under `skills/`.

If Cursor exposes separate subagent contexts, Constellation is allowed only when route evidence is observable.

## Hermes Agent

Hermes supports `SKILL.md` skills and can scan external skill directories. The descriptions in this pack are intentionally short and host-neutral. Copy or expose the desired skill directories to Hermes, or point Hermes at a shared skills directory.

Do not hard-code Hermes tools into the canonical skills. Hermes may use its native tools when available.

## Claude-compatible hosts

`CLAUDE.md` points back to the canonical skill and `AGENTS.md`. Avoid maintaining a separate Claude-specific reasoning workflow.

## Portability rule

When a host lacks a named feature, preserve the intent rather than inventing an equivalent. For example, if there are no subagents, run independent lens passes sequentially instead of pretending to delegate.
