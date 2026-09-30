# Contributing

## Ways to contribute

- **Seal a crack.** [LEDGER.md](./LEDGER.md) lists the open cracks with their evidence. Pick one, write the seal (a check that fails first, then the fix, then the doc line that now tells the truth), and open a pull request that names the crack ID.
- **Melt a pack skill into a Grok-native one.** The stubs in `stubs/skills/` each name the LibreWhatsApp-Claude-Code plugin that holds the depth. Melt one into a real Grok skill under `plugins/libre-whatsapp-grok/skills/` by the rules below, and keep draft-only and consent-first.
- **Report a routing miss.** When Grok picks the wrong skill, or none, the description is what needs fixing: [routing miss form](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/issues/new?template=routing-miss.yml).
- **Propose a plugin.** A job people do in WhatsApp that nothing here covers: [plugin proposal form](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/issues/new?template=plugin-proposal.yml). General feedback goes in the [feedback form](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/issues/new?template=feedback.yml).

## Melt, don't clone

Ports from LibreWhatsApp-Claude-Code must follow Liquid Gold:

1. Keep model-agnostic WhatsApp workflow knowledge (only-new, confirm gate, local Whisper).
2. Strip Claude-only paths, `model:` pins, Anthropic install residue, and `--send` skip-gates.
3. Ship as Grok `SKILL.md` in the `plugins/libre-whatsapp-grok/` plugin (Grok reads `.grok-plugin/plugin.json`).
4. Teach while helping (Gold Hat).
5. **Never** add auto-send, mass-blast, or dark-pattern templates.

## Skill format

```
plugins/libre-whatsapp-grok/skills/<name>/SKILL.md   # melted skills (installed)
stubs/skills/<name>/SKILL.md                         # stub cues (not installed)
```

YAML frontmatter: `name`, `description` (quote it if it contains `: `). The description is the routing line: say what the skill does and when to use it. Body: when to use, steps, measurable checks.

The files above are canonical. After editing one, copy it to `.grok/skills/<name>/SKILL.md` (dogfood). The two files must match; CI checks it. Links that leave the skill's folder are absolute GitHub URLs, so they still work after install.

When a stub melts: `git mv stubs/skills/<name> plugins/libre-whatsapp-grok/skills/<name>`, remove its "Stub, not installed" line and the "Stub cue" prefix, and update [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

The pack entries in `.grok-plugin/marketplace.json` are generated. Run `scripts/pin-pack.sh` to move them to the pack's current commit; do not edit them by hand.

## PR bar

- Honest depth: only count what you melt (`stub` vs `melted` in `docs/DEPTH_MATRIX.md`)
- No "Grok killer" language
- Draft-only + consent by default
- Suite footer → Reality OS + sibling packs
- Gold Hat: empower or extract?
