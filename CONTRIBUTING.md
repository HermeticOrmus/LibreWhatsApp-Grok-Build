# Contributing

## Melt, don't clone

Ports from LibreWhatsApp-Claude-Code must follow Liquid Gold:

1. Keep model-agnostic WhatsApp workflow knowledge (only-new, confirm gate, local Whisper).
2. Strip Claude-only paths, `model:` pins, Anthropic install residue.
3. Ship as Grok `SKILL.md` / agents under `.grok/` conventions.
4. Teach while helping (Gold Hat).
5. **Never** add auto-send, mass-blast, or dark-pattern templates.

## Skill format

```
skills/<name>/SKILL.md
```

YAML frontmatter: `name`, `description`. Body: when to use, steps, measurable checks.

## PR bar

- Honest depth: only count what you melt
- No "Grok killer" language
- Draft-only + consent by default
- Link Reality OS in suite footers
