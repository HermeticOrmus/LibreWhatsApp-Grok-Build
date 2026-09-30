<p align="center">
  <img src="https://ormus.solutions/mascot/pixellab_liquid_to_caduceus.gif" alt="LibreWhatsApp Grok Build" width="128" style="image-rendering: pixelated;" />
</p>

<h1 align="center">LibreWhatsApp Grok Build</h1>

<p align="center">
  <em>WhatsApp in your Grok Build session: draft-only replies behind a consent gate, plus the LibreWhatsApp pack by pinned commit</em>
</p>

<p align="center">
  <a href="https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/stargazers"><img src="https://img.shields.io/github/stars/HermeticOrmus/LibreWhatsApp-Grok-Build?style=flat-square&color=aa8142" alt="Stars" /></a>
  <a href="https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/LICENSE"><img src="https://img.shields.io/github/license/HermeticOrmus/LibreWhatsApp-Grok-Build?style=flat-square&color=aa8142" alt="License" /></a>
  <a href="https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/commits"><img src="https://img.shields.io/github/last-commit/HermeticOrmus/LibreWhatsApp-Grok-Build?style=flat-square&color=aa8142" alt="Last Commit" /></a>
  <img src="https://img.shields.io/badge/Messaging-aa8142?style=flat-square&logo=whatsapp&logoColor=white" alt="Messaging" />
  <img src="https://img.shields.io/badge/Grok_Build-aa8142?style=flat-square&logo=x&logoColor=white" alt="Grok Build" />
</p>

---

**WhatsApp-in-session skills for [Grok Build](https://github.com/HermeticOrmus/grok-build-reality-os)** — ported and melted from [LibreWhatsApp-Claude-Code](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code), not a dumb copy.

> Status: **v1.0.0**. The three melted skills (`draft-reply`, `consent-gate`, `template-scrub`) install as the `libre-whatsapp-grok` plugin, and the pack's `pull`, `grab` and `transcribe` plugins install beside them from the same marketplace. The five stubs stay in `stubs/` and do not install. See [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) and the [kintsugi ledger](./LEDGER.md).

## Why this exists

You are in a Grok Build session and the decision lives in WhatsApp. Switching to the phone breaks flow. LibreWhatsApp melts pull / draft / confirm / local-transcribe workflows for Grok — with a **Gold Hat messaging posture**: draft-only by default, consent gates, quiet hours, and template scrub against dark spam patterns.

The value is workflow logic (only-new, confirm gate, local Whisper, alias registry). The provider is yours; Periskope is the reference MCP adapter.

This repo counts only what it has melted. Upstream Claude `/push --send` does not ship here.

## Install (<5 min)

See [QUICK_START.md](./QUICK_START.md) for the marketplace, dogfood, and copy paths.

```bash
grok plugin marketplace add HermeticOrmus/LibreWhatsApp-Grok-Build
grok plugin install libre-whatsapp-grok@libre-whatsapp-grok
# The pack's plugins, pinned by commit:
grok plugin install pull@libre-whatsapp-grok
grok plugin install grab@libre-whatsapp-grok
grok plugin install transcribe@libre-whatsapp-grok
grok plugin list
```

The pack's `push` plugin is not in this marketplace. Its `--send` flag skips the preview, and this edition refuses skip-gates ([LEDGER.md](./LEDGER.md), K-09). Draft with `draft-reply`, scrub with `template-scrub`, and send only after `consent-gate` opens.

The pack's `pull` and `grab` read `~/.claude/wa-registry.json` unless `WA_REGISTRY` is set. Point them at this edition's registry with `export WA_REGISTRY=~/.grok/wa-registry.json`.

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first.

## Depth (honest)

| Artifact | This repo now | Installed from the pack |
|----------|---------------|-------------------------|
| Skills | 3 melted, in the `libre-whatsapp-grok` plugin; 5 stubs in `stubs/skills/`, not installed | The skills inside `pull`, `grab`, `transcribe` |
| Agents | 1 stub (`whatsapp-orchestrator`) in `stubs/agents/`, not installed | None; the pack ships no agents |
| Plugins | 1 (`libre-whatsapp-grok`, v1.0.0) | 3 of 4, pinned by commit in `.grok-plugin/marketplace.json`; `push` held out |

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

The melted skills install as the `libre-whatsapp-grok` plugin. The stubs live in `stubs/skills/` and do not install; each one names the pack plugin that holds the real depth, and [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) maps them all.

Agent: `stubs/agents/whatsapp-orchestrator.md`, the stub coordinator for a full suite pass. It does not install.

## Layout (Grok Build)

```
.grok-plugin/marketplace.json        # marketplace: the Grok-native plugin, then the pack's plugins by pinned commit
plugins/libre-whatsapp-grok/         # the Grok-native plugin (manifest in .grok-plugin/plugin.json)
  skills/                            # the melted SKILL.md bodies (canonical)
stubs/skills/                        # stub cues; not installed; each names the pack plugin with the depth
stubs/agents/                        # the stub orchestrator; not installed
scripts/pin-pack.sh                  # re-pins the pack entries to the pack's main HEAD
registry.example.json                # aliases only; copy to ~/.grok/wa-registry.json
docs/                                # DEPTH_MATRIX, MELT_RULES
LEDGER.md                            # kintsugi ledger: the cracks and their seals
.grok/skills/                        # dogfood copy of the plugin skills and the stubs (CI keeps it in sync)
.grok/plugins/librewhatsapp-core/    # v0 bundle stub, kept as the dogfood copy of the stub orchestrator
```

Claude's `.claude/` maps to Grok skills + `AGENTS.md` + `.grok/`. Melt rules: [docs/MELT_RULES.md](./docs/MELT_RULES.md).

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract?

Messaging non-negotiables: draft-only, teach consent, no dark spam patterns. See [SECURITY.md](./SECURITY.md).

## Kintsugi ledger

[LEDGER.md](./LEDGER.md) lists every crack found in the v0 edition, the evidence, and the seal this release put on it. Open cracks stay open in plain sight until someone seals them.

## Feedback

Tell us what worked and what is missing: [feedback form](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/issues/new?template=feedback.yml). Grok picked the wrong skill? [Report a routing miss](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/issues/new?template=routing-miss.yml). Want a new skill or plugin? [Propose it](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/issues/new?template=plugin-proposal.yml). Ways to contribute: [CONTRIBUTING.md](./CONTRIBUTING.md).

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
