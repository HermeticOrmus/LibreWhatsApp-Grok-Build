# Quick Start — LibreWhatsApp for Grok Build

> From a clean machine to a consent-gated draft in under 5 minutes.

Doctrine first: put [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine (global Grok doctrine). This pack does not replace it.

## Prerequisites

- `git`
- Grok Build installed and able to see skills under `.grok/skills/` or `~/.grok/skills/`
- Optional: Periskope (or other) WhatsApp MCP for live pull — melted skills work as draft / scrub / gate without it
- Local Whisper only if you later use `voice-local` (still a stub)
- Optional local registry: copy `registry.example.json` to `~/.grok/wa-registry.json` and fill **your** aliases. Never commit that file.

## Layout this file assumes

Verified against this repository (do not invent extra folders):

```
skills/<name>/SKILL.md                 # canonical skill bodies (copy these)
AGENTS/whatsapp-orchestrator.md
registry.example.json
docs/DEPTH_MATRIX.md
docs/MELT_RULES.md
.grok/skills/<name>/SKILL.md           # dogfood copy; must match skills/
.grok/plugins/librewhatsapp-core/      # plugin stub; not required for first run
```

Melted (usable now): `skills/draft-reply/SKILL.md`, `skills/consent-gate/SKILL.md`, `skills/template-scrub/SKILL.md`.
Still stubs: `chat-pull`, `thread-triage`, `quiet-hours`, `grab-snippet`, `voice-local`, plus the orchestrator. Honest table: [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Install (pick one)

### A. Dogfood this repo (fastest)

```bash
git clone https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build.git
cd LibreWhatsApp-Grok-Build
# Skills are already at .grok/skills/ — open this folder in Grok Build.
```

### B. Install into your project

```bash
git clone https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build.git ~/LibreWhatsApp-Grok-Build
cd /path/to/your-project
mkdir -p .grok/skills
cp -R ~/LibreWhatsApp-Grok-Build/skills/* .grok/skills/
```

Confirm the copy landed:

```bash
test -f .grok/skills/draft-reply/SKILL.md
test -f .grok/skills/consent-gate/SKILL.md
test -f .grok/skills/template-scrub/SKILL.md
ls .grok/skills
```

You should see eight skill directories, matching `skills/` in this repo.

### C. User-global

```bash
git clone https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build.git ~/LibreWhatsApp-Grok-Build
mkdir -p ~/.grok/skills
cp -R ~/LibreWhatsApp-Grok-Build/skills/* ~/.grok/skills/
```

Same three `test -f` checks as B, under `~/.grok/skills/`.

Optional registry (machine-local, never the repo):

```bash
cp ~/LibreWhatsApp-Grok-Build/registry.example.json ~/.grok/wa-registry.json
# Edit aliases only. No real numbers belong in git.
```

Copy `AGENTS/whatsapp-orchestrator.md` only when you want a full-suite pass. It is still a stub coordinator.

## First-run teach cue

In Grok Build, on a thread you own (paste context if you have no MCP):

1. **Draft** — "Run draft-reply for this thread. Do not send. Name who / why / how to stop."
2. **Scrub** — "Run template-scrub on that draft. Strip urgency, guilt, or blast language."
3. **Gate** — "Run consent-gate. Preview only. Treat 'looks good' as CLOSED."

You used melted LibreWhatsApp depth on Grok — not a Claude `/push --send` paste, not a silent blast.

If you later pull live chat, `chat-pull` is still a stub: aliases, only-new, no send. Outbound still dies at this gate.

## Hard rules

- Draft-only by default. Human confirm phrase before send (`send` / `confirm send to <alias>`).
- No dark spam patterns. Teach consent.
- Never embed secrets, phones, or chat ids in prompts or examples.
- Honest stubs — do not invent pull/whisper/quiet-hours engines.
- Gold Hat: empower or extract?

## Smoke checklist

- [ ] `draft-reply`, `consent-gate`, and `template-scrub` files exist at the install path you chose
- [ ] Grok can see those three skills
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
