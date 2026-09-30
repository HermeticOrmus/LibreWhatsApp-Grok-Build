# librewhatsapp-core (v0 plugin stub, kept as a dogfood copy)

This was the v0 plugin bundle. It had no manifest and no skills, so it bundled nothing: Grok saw it only as a project plugin with one agent, the stub orchestrator. It stays as the dogfood copy of `stubs/agents/whatsapp-orchestrator.md` (the two files must match; CI checks it).

The installable plugin is now [`plugins/libre-whatsapp-grok/`](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/tree/main/plugins/libre-whatsapp-grok), with its own manifest. Install it with `grok plugin marketplace add HermeticOrmus/LibreWhatsApp-Grok-Build` and `grok plugin install libre-whatsapp-grok@LibreWhatsApp-Grok-Build`.

The melted skills now live in that plugin's `skills/`; the stubs live in `stubs/skills/`. Dogfood copies of both: `.grok/skills/`.

Melted toward L3–L4: `draft-reply`, `consent-gate`, `template-scrub`.
Still stubs (in `stubs/skills/`, not installed): `chat-pull`, `thread-triage`, `quiet-hours`, `grab-snippet`, `voice-local`.

Gold Hat: draft-only messaging, consent gates, no dark spam patterns.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Sibling packs: [README suite footer](../../../README.md).
