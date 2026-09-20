---
name: chat-pull
description: Pull a WhatsApp chat and show only-what-is-new via local registry aliases.
---

# chat-pull

> Status: **stub (L1–L2 cue)** — not a melted pull protocol. Do not invent Claude `/pull` depth, state-file schemas, or slash-command theater.

Fetch a chat. Show what is new since last look. Gold Hat: aliases live on the operator machine; the repo never ships real numbers.

## When to use

- "What is new in `team` / `teammate`"
- Before `draft-reply` when you need thread context
- After wiring a provider (Periskope is the reference MCP)

## Cue (do this much; no more)

1. Resolve the alias from `~/.grok/wa-registry.json` (copy `registry.example.json`). If the registry is missing, stop and say so.
2. Call the provider **list-messages** seam only. Do not send.
3. Prefer only-what-is-new. Quote bodies verbatim. Do not paraphrase.
4. Sender gotcha (Periskope-shaped): the wrong account number yields an empty slice with **no error**. Ask the human to check `provider.default_sender_phone` on their machine — do not print the number.
5. Voice notes have no text — point at `voice-local` (still a stub).

Hand off leftovers to `thread-triage` (stub) and `draft-reply` (melted). Never embed chat ids or tokens in output.

## Measurable checks

- [ ] No send
- [ ] Aliases, not raw ids, in what you print
- [ ] Empty result named as possible sender mismatch, not "chat is quiet" unless you know that

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling packs: [README suite footer](../../README.md).
