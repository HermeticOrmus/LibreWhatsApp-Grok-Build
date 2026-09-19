---
name: voice-local
description: Transcribe voice notes with local Whisper — audio stays local.
---

# voice-local

> Status: **v0 stub** — melt body next. Gold Hat: draft-only messaging, teach consent, no dark spam patterns.

## When to use

Transcribe voice notes with local Whisper — audio stays local.

## Hard rules (always)

- **Draft-only by default.** Never send without an explicit human confirm gate.
- **No dark spam patterns:** urgency fakes, fake scarcity, guilt loops, silent mass-blast, hidden opt-outs.
- **Teach consent:** every outbound path explains who sees it, why, and how to stop.
- **No secrets** in prompts, registry examples, or logs (phones, tokens, chat ids stay local).
- Provider is swappable (Periskope reference MCP); skills own workflow logic, not vendor lock-in.

## Steps (stub)

1. Restate intent and audience.
2. Apply this skill's checklist.
3. Produce draft / triage output with measurable checks.
4. Hand off to `consent-gate` before any send.

## Measurable checks

- [ ] Output is a draft or report, not a silent send
- [ ] Quiet-hours / consent considered
- [ ] No spam-template residue
- [ ] No real phone numbers or API keys in output
