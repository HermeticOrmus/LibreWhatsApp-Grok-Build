# Quick Start — LibreWhatsApp for Grok Build

> From a clean machine to a consent-gated draft in under 5 minutes.

Doctrine first: put [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine (global Grok doctrine). This pack does not replace it.

## Prerequisites

- Grok Build installed: `curl -fsSL https://x.ai/cli/install.sh | bash`, then `grok --version`. Plugin commands need no login.
- `git` (only for the dogfood and copy paths)
- Optional: Periskope (or other) WhatsApp MCP for live pull. The melted skills work as draft, scrub and gate without it
- Local Whisper only if you use the pack's `transcribe` plugin (`voice-local` here is still a stub)
- Optional local registry: copy `registry.example.json` to `~/.grok/wa-registry.json` and fill **your** aliases. Never commit that file. The pack's `pull` and `grab` read `~/.claude/wa-registry.json` unless you `export WA_REGISTRY=~/.grok/wa-registry.json`.

## Layout this file assumes

Verified against this repository (do not invent extra folders):

```
.grok-plugin/marketplace.json                     # the marketplace: libre-whatsapp-grok, then the pack's plugins by pinned commit
plugins/libre-whatsapp-grok/.grok-plugin/plugin.json
plugins/libre-whatsapp-grok/skills/<name>/SKILL.md  # the melted skills (canonical)
stubs/skills/<name>/SKILL.md                      # stub cues; not installed
stubs/agents/whatsapp-orchestrator.md             # stub coordinator; not installed
registry.example.json
docs/DEPTH_MATRIX.md
docs/MELT_RULES.md
.grok/skills/<name>/SKILL.md                      # dogfood copy; must match its source above
.grok/plugins/librewhatsapp-core/                 # v0 bundle stub; dogfood copy of the stub orchestrator
```

Melted (usable now): `plugins/libre-whatsapp-grok/skills/draft-reply/SKILL.md`, `plugins/libre-whatsapp-grok/skills/consent-gate/SKILL.md`, `plugins/libre-whatsapp-grok/skills/template-scrub/SKILL.md`.
Still stubs, in `stubs/`: `chat-pull`, `thread-triage`, `quiet-hours`, `grab-snippet`, `voice-local`, plus the orchestrator. Each stub names the pack plugin with the real depth. Honest table: [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Install (pick one)

### A. Marketplace (recommended)

One marketplace brings the Grok-native plugin and the pack's plugins, each pinned to a commit:

```bash
grok plugin marketplace add HermeticOrmus/LibreWhatsApp-Grok-Build
grok plugin install libre-whatsapp-grok@LibreWhatsApp-Grok-Build
grok plugin install pull@LibreWhatsApp-Grok-Build
grok plugin install grab@LibreWhatsApp-Grok-Build
grok plugin install transcribe@LibreWhatsApp-Grok-Build
```

Grok registers a marketplace added from GitHub under the repo's name, so the part after `@` is `LibreWhatsApp-Grok-Build`, not the manifest name `libre-whatsapp-grok`. A bare plugin name also works when no other marketplace you added has a plugin by that name.

Confirm what landed:

```bash
grok plugin list
grok plugin details libre-whatsapp-grok
```

You should see `libre-whatsapp-grok` (three skills: `draft-reply`, `consent-gate`, `template-scrub`) plus `pull`, `grab` and `transcribe`. The pack's `push` is not offered: its `--send` flag skips the preview, and this edition refuses skip-gates ([LEDGER.md](./LEDGER.md), K-09).

Only the Grok-native plugin, without the marketplace:

```bash
grok plugin install HermeticOrmus/LibreWhatsApp-Grok-Build#plugins/libre-whatsapp-grok
```

Do not install the repo root itself (`grok plugin install HermeticOrmus/LibreWhatsApp-Grok-Build`): since v1.0.0 the root holds no skills, so Grok installs an empty plugin.

### B. Dogfood this repo

```bash
git clone https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build.git
cd LibreWhatsApp-Grok-Build
# Dogfood copies of the melted skills and the stubs are at .grok/skills/; open this folder in Grok Build.
```

### C. Copy into your project (no plugin manager)

```bash
git clone https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build.git ~/LibreWhatsApp-Grok-Build
cd /path/to/your-project
mkdir -p .grok/skills
cp -R ~/LibreWhatsApp-Grok-Build/plugins/libre-whatsapp-grok/skills/* .grok/skills/
```

Confirm the copy landed:

```bash
test -f .grok/skills/draft-reply/SKILL.md
test -f .grok/skills/consent-gate/SKILL.md
test -f .grok/skills/template-scrub/SKILL.md
ls .grok/skills
```

You should see three skill directories, matching `plugins/libre-whatsapp-grok/skills/` in this repo. The stubs are not copied: they are cues, not skills.

### D. User-global copy

```bash
git clone https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build.git ~/LibreWhatsApp-Grok-Build
mkdir -p ~/.grok/skills
cp -R ~/LibreWhatsApp-Grok-Build/plugins/libre-whatsapp-grok/skills/* ~/.grok/skills/
```

Same three `test -f` checks as C, under `~/.grok/skills/`.

Optional registry (machine-local, never the repo):

```bash
cp ~/LibreWhatsApp-Grok-Build/registry.example.json ~/.grok/wa-registry.json
# Edit aliases only. No real numbers belong in git.
```

Copy `stubs/agents/whatsapp-orchestrator.md` only when you want a full-suite pass. It is still a stub coordinator, and no install path ships it.

## First-run teach cue

In Grok Build, on a thread you own (paste context if you have no MCP):

1. **Draft** — "Run draft-reply for this thread. Do not send. Name who / why / how to stop."
2. **Scrub** — "Run template-scrub on that draft. Strip urgency, guilt, or blast language."
3. **Gate** — "Run consent-gate. Preview only. Treat 'looks good' as CLOSED."

You used melted LibreWhatsApp depth on Grok — not a Claude `/push --send` paste, not a silent blast.

If you later pull live chat, `chat-pull` is still a stub; the pack's `pull` plugin holds the real depth (aliases, only-new, no send). Outbound still dies at this gate.

## Hard rules

- Draft-only by default. Human confirm phrase before send (`send` / `confirm send to <alias>`).
- No dark spam patterns. Teach consent.
- Never embed secrets, phones, or chat ids in prompts or examples.
- Honest stubs — do not invent pull/whisper/quiet-hours engines.
- Gold Hat: empower or extract?

## Smoke checklist

- [ ] `grok plugin list` shows `libre-whatsapp-grok` (or the three skill files exist at the copy path you chose)
- [ ] Grok can see `draft-reply`, `consent-gate`, and `template-scrub`
- [ ] One skill run produces a draft or scrub report (not a silent send)
- [ ] Consent preview shown; gate stays CLOSED without a confirm phrase
- [ ] Quiet-hours mentioned as stub-ask or a human-stated window
- [ ] No secrets in output

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- This pack: [LibreWhatsApp-Grok-Build](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build)
- Sibling Libre*-Grok-Build packs: [Arch](https://github.com/HermeticOrmus/LibreArch-Grok-Build) · [Copy](https://github.com/HermeticOrmus/LibreCopy-Grok-Build) · [DevOps](https://github.com/HermeticOrmus/LibreDevOps-Grok-Build) · [Embed](https://github.com/HermeticOrmus/LibreEmbed-Grok-Build) · [FinTech](https://github.com/HermeticOrmus/LibreFinTech-Grok-Build) · [GameDev](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build) · [GEO](https://github.com/HermeticOrmus/LibreGEO-Grok-Build) · [MLOps](https://github.com/HermeticOrmus/LibreMLOps-Grok-Build) · [MobileDev](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build) · [SecOps](https://github.com/HermeticOrmus/LibreSecOps-Grok-Build) · [SessionFlow](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [UIUX](https://github.com/HermeticOrmus/LibreUIUX-Grok-Build)
- Skills collections: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof (upstream, not this inventory): [LibreWhatsApp-Claude-Code](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code)
- Systems map: https://ormus.solutions/systems
- https://ormus.solutions
