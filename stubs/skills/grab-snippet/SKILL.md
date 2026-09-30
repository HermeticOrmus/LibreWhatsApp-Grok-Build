---
name: grab-snippet
description: "Stub cue, not installed. Grab the latest URL, command, or code block from a WhatsApp chat. Full depth: the grab plugin of LibreWhatsApp-Claude-Code."
---

# grab-snippet

> Stub, not installed by the plugin. The real depth is the [`grab`](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code/tree/main/plugins/grab) plugin of LibreWhatsApp-Claude-Code, which this edition's marketplace installs: `grok plugin install grab@LibreWhatsApp-Grok-Build`.

> Status: **stub (L1–L2 cue)** — not a melted clipboard pipeline. Do not invent `/grab` slash-command theater.

Lift the useful fragment. Gold Hat: copy the snippet, not the contact graph.

## When to use

- "Get the URL / command / code they just sent"
- After `chat-pull` when the human wants one artifact, not a draft

## Cue (do this much; no more)

1. Prefer the latest matching block in the current pull or pasted thread.
2. Quote verbatim. Do not "clean up" a command into something else.
3. Strip secrets if the snippet contains tokens or phones — show a redacted form and say you redacted.
4. Clipboard helpers (`wl-copy`, `xclip`, `pbcopy`) are optional and local. Do not upload the snippet.

This skill does not send. If they want a reply about the snippet, use `draft-reply`.

## Measurable checks

- [ ] One snippet, verbatim or honestly redacted
- [ ] No send
- [ ] No raw secrets in the output

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/GOLD_HAT.md). Sibling packs: [README suite footer](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/README.md).
