# Quick Start — LibreWhatsApp for Grok Build

> From zero to a consent-gated draft in under 5 minutes.

## Prerequisites

- Grok Build installed and working
- Optional: Periskope (or other) WhatsApp MCP for live pull/send — skills work as draft/triage without it
- Local Whisper only if you use `voice-local`

## Install skills (repo-local)

```bash
git clone https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build.git
cd your-project
mkdir -p .grok/skills
cp -R /path/to/LibreWhatsApp-Grok-Build/skills/* .grok/skills/
```

Or user-global:

```bash
mkdir -p ~/.grok/skills
cp -R /path/to/LibreWhatsApp-Grok-Build/skills/* ~/.grok/skills/
```

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first.

## First-run teach cue

1. **Triage** — "Run thread-triage on my open WhatsApp loops."
2. **Draft** — "Run draft-reply for this thread (do not send)."
3. **Consent** — "Run consent-gate + quiet-hours before any outbound."

## Hard rules

- Draft-only by default. Human confirm before send.
- No dark spam patterns. Teach consent.
- Never embed secrets in prompts or examples.
- Honest stubs — melt depth next.
- Gold Hat: empower or extract?

## Smoke checklist

- [ ] Skills visible to Grok
- [ ] One skill run produces a draft or triage report (not a silent send)
- [ ] Consent / quiet-hours mentioned when outbound is considered
- [ ] No secrets in output
