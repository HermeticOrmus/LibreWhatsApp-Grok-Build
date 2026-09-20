# Contributing

## Melt, don't clone

Ports from LibreWhatsApp-Claude-Code must follow Liquid Gold:

1. Keep model-agnostic WhatsApp workflow knowledge (only-new, confirm gate, local Whisper).
2. Strip Claude-only paths, `model:` pins, Anthropic install residue, and `--send` skip-gates.
3. Ship as Grok `SKILL.md` / agents under `.grok/` conventions.
4. Teach while helping (Gold Hat).
5. **Never** add auto-send, mass-blast, or dark-pattern templates.

## Skill format

```
skills/<name>/SKILL.md
```

YAML frontmatter: `name`, `description`. Body: when to use, steps, measurable checks.

`skills/` is canonical. After editing a skill, copy it to `.grok/skills/<name>/SKILL.md` (dogfood). The two files must match.

## PR bar

- Honest depth: only count what you melt (`stub` vs `melted` in `docs/DEPTH_MATRIX.md`)
- No "Grok killer" language
- Draft-only + consent by default
- Suite footer → Reality OS + sibling packs
- Gold Hat: empower or extract?
