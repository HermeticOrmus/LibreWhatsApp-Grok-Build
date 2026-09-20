# Security

Report vulnerabilities privately to the HermeticOrmus maintainers (see org profile / funding contacts).

Do not file public issues with exploit details.

This suite is documentation and prompts for WhatsApp-in-session workflows — not a network service. Still:

- Never embed secrets, phone numbers, chat ids, or provider tokens in skills, templates, or examples.
- Registry and credentials stay on the operator's machine (`~/.grok/wa-registry.json`, not this repo).
- Default posture is **draft-only** with a consent gate; do not ship auto-blast, `--send` skip-gates, or dark spam patterns.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](./GOLD_HAT.md). Systems map: https://ormus.solutions/systems
