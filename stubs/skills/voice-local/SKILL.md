---
name: voice-local
description: "Stub cue, not installed. Transcribe WhatsApp voice notes with local Whisper: audio stays on the machine. Full depth: the transcribe plugin of LibreWhatsApp-Claude-Code."
---

# voice-local

> Stub, not installed by the plugin. The real depth is the [`transcribe`](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code/tree/main/plugins/transcribe) plugin of LibreWhatsApp-Claude-Code, which this edition's marketplace installs: `grok plugin install transcribe@libre-whatsapp-grok`.

> Status: **stub (L1–L2 cue)** — not a melted transcriber. Do not invent cloud STT or upload the audio.

Turn a voice note into text on this machine. Gold Hat: local Whisper empowers; shipping audio to a vendor extracts.

## When to use

- A pulled message is audio with no body
- The human has a local Whisper install (whisper.cpp or openai-whisper) and a file path they own

## Cue (do this much; no more)

1. Audio stays local. Refuse cloud speech-to-text "just this once".
2. If no local binary / no file path, say what is missing. Do not fetch a media URL to a third party.
3. Return text as a draft input — not a send. Mark uncertain words instead of guessing commitments.
4. Do not keep extra copies of the audio in the repo.

Hand readable text to `thread-triage` (stub) or `draft-reply` (melted). Outbound still needs `consent-gate`.

## Measurable checks

- [ ] No cloud STT
- [ ] No send
- [ ] No secrets/phones echoed from the transcript unless the human asked to see them

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/GOLD_HAT.md). Sibling packs: [README suite footer](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/README.md).
