# LibreWhatsApp-Grok-Build

**WhatsApp-in-session skills for Grok Build** — ported and melted from [LibreWhatsApp-Claude-Code](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code), not a dumb copy.

> Status: **v0 public scaffold** — honest stubs. Melt depth next.

## Why this exists

You are in a Grok Build session and the decision lives in WhatsApp. Switching to the phone breaks flow. LibreWhatsApp melts pull / draft / confirm / local-transcribe workflows for Grok — with a **Gold Hat messaging posture**: draft-only by default, consent gates, quiet hours, and template scrub against dark spam patterns.

The value is workflow logic (only-new, confirm gate, local Whisper, alias registry). The provider is yours; Periskope is the reference MCP adapter.

## Install (<5 min)

See [QUICK_START.md](./QUICK_START.md).

```bash
mkdir -p .grok/skills
cp -R skills/* .grok/skills/
```

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first.

## Depth matrix (honest)

| Artifact | v0 scaffold | Upstream Claude (proof) |
|----------|-------------|-------------------------|
| Skills (melted bodies) | 8 stubs → fill next | pull / push / grab / transcribe plugins |
| Agents | 1 (`whatsapp-orchestrator`) | upstream plugin orchestration |

Counts on the right are **upstream proof**, not this repo's claim until melted.

## First skills

| Skill | Job |
|-------|-----|
| draft-reply | Draft replies for human confirm — never auto-send |
| thread-triage | Open loops / priority without nagging |
| quiet-hours | Queue or refuse outbound outside allowed windows |
| consent-gate | Preview-and-confirm before any send |
| template-scrub | Strip spam / dark-pattern templates; teach consent copy |
| chat-pull | Fetch chat; show only-what-is-new |
| grab-snippet | Grab latest URL, command, or code block |
| voice-local | Local Whisper transcription — audio stays on machine |

Agent: `AGENTS/whatsapp-orchestrator.md` — full suite pass.

## Layout (Grok Build)

```
skills/                 # install into .grok/skills or ~/.grok/skills
AGENTS/                 # suite agents
.grok/plugins/          # optional plugin bundle
docs/                   # DEPTH_MATRIX, MELT_RULES
```

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract?

Messaging non-negotiables: draft-only, teach consent, no dark spam patterns. See [SECURITY.md](./SECURITY.md).

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- Jev hub: [ormus-jev](https://github.com/HermeticOrmus/ormus-jev)
- Siblings: [LibreUIUX-Grok-Build](https://github.com/HermeticOrmus/LibreUIUX-Grok-Build) · [LibreSessionFlow-Grok-Build](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [LibreCopy-Grok-Build](https://github.com/HermeticOrmus/LibreCopy-Grok-Build)
- Skills packs: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof: [LibreWhatsApp-Claude-Code](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code)
- Systems map: https://ormus.solutions/systems
- https://ormus.solutions

## License

MIT — see [LICENSE](./LICENSE).
