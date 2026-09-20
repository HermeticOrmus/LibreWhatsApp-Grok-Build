# LibreWhatsApp-Grok-Build

**WhatsApp-in-session skills for [Grok Build](https://github.com/HermeticOrmus/grok-build-reality-os)** — ported and melted from [LibreWhatsApp-Claude-Code](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code), not a dumb copy.

> Status: **public v0** — three skills melted toward L3–L4 (`draft-reply`, `consent-gate`, `template-scrub`); the rest are honest stubs. See [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Why this exists

You are in a Grok Build session and the decision lives in WhatsApp. Switching to the phone breaks flow. LibreWhatsApp melts pull / draft / confirm / local-transcribe workflows for Grok — with a **Gold Hat messaging posture**: draft-only by default, consent gates, quiet hours, and template scrub against dark spam patterns.

The value is workflow logic (only-new, confirm gate, local Whisper, alias registry). The provider is yours; Periskope is the reference MCP adapter.

This repo counts only what it has melted. Upstream Claude `/push --send` does not ship here.

## Install (<5 min)

See [QUICK_START.md](./QUICK_START.md) for clone, dogfood, project-local, and user-global paths.

```bash
git clone https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build.git
cd LibreWhatsApp-Grok-Build
# Dogfood: .grok/skills/ already has the skill bodies.
# Other project: cp -R skills/* /path/to/your-project/.grok/skills/
```

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first.

## Depth (honest)

| Artifact | This repo now | Upstream Claude |
|----------|---------------|-----------------|
| Skills | 3 melted + 5 stubs | Proof the job exists; not our inventory |
| Agents | 1 stub (`whatsapp-orchestrator`) | Proof the job exists; not our inventory |
| Plugins | 1 core bundle stub | Proof the job exists; not our inventory |

Do not paste Claude plugin/command totals here. Update [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) when something melts.

## Skills

| Skill | Status | Job |
|-------|--------|-----|
| draft-reply | melted | Draft replies for human confirm — never auto-send |
| consent-gate | melted | Preview-and-confirm before any send |
| template-scrub | melted | Strip spam / dark-pattern templates; teach consent copy |
| chat-pull | stub | Fetch chat; show only-what-is-new |
| thread-triage | stub | Open loops / priority without nagging |
| quiet-hours | stub | Queue or refuse outbound outside allowed windows |
| grab-snippet | stub | Grab latest URL, command, or code block |
| voice-local | stub | Local Whisper transcription — audio stays on machine |

Agent: `AGENTS/whatsapp-orchestrator.md` — stub coordinator for a full suite pass.

## Layout (Grok Build)

```
skills/                 # canonical SKILL.md bodies
AGENTS/                 # suite agents
registry.example.json   # aliases only; copy to ~/.grok/wa-registry.json
docs/                   # DEPTH_MATRIX, MELT_RULES
.grok/skills/           # dogfood copy of skills/ (keep in sync)
.grok/plugins/          # optional plugin bundle stub
```

Claude's `.claude/` maps to Grok skills + `AGENTS.md` + `.grok/`. Melt rules: [docs/MELT_RULES.md](./docs/MELT_RULES.md).

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract?

Messaging non-negotiables: draft-only, teach consent, no dark spam patterns. See [SECURITY.md](./SECURITY.md).

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- This pack: [LibreWhatsApp-Grok-Build](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build)
- Sibling Libre*-Grok-Build packs: [Arch](https://github.com/HermeticOrmus/LibreArch-Grok-Build) · [Copy](https://github.com/HermeticOrmus/LibreCopy-Grok-Build) · [DevOps](https://github.com/HermeticOrmus/LibreDevOps-Grok-Build) · [Embed](https://github.com/HermeticOrmus/LibreEmbed-Grok-Build) · [FinTech](https://github.com/HermeticOrmus/LibreFinTech-Grok-Build) · [GameDev](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build) · [GEO](https://github.com/HermeticOrmus/LibreGEO-Grok-Build) · [MLOps](https://github.com/HermeticOrmus/LibreMLOps-Grok-Build) · [MobileDev](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build) · [SecOps](https://github.com/HermeticOrmus/LibreSecOps-Grok-Build) · [SessionFlow](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [UIUX](https://github.com/HermeticOrmus/LibreUIUX-Grok-Build)
- Skills collections: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof: [LibreWhatsApp-Claude-Code](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code)
- Systems map: https://ormus.solutions/systems
- https://ormus.solutions

## License

MIT — see [LICENSE](./LICENSE).
