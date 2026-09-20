---
name: quiet-hours
description: Queue or refuse outbound WhatsApp during quiet-hours windows.
---

# quiet-hours

> Status: **stub (L1–L2 cue)** — no timezone engine. Do not invent windows the human did not state.

Respect rest. Gold Hat: a late ping that "just this once" ships is extract.

## When to use

- `consent-gate` is about to consider GATE OPEN
- The human named a quiet window (or asked "is it too late to send?")

## Cue (do this much; no more)

1. If the human stated a window (e.g. "no outbound after 21:00 America/Panama"), treat inside-window as **refuse or queue** the draft. Keep GATE CLOSED.
2. If they did not state a window, say this skill is a stub and ask: "Is now an allowed window?" Do not guess their timezone.
3. Queued means: keep the draft, do not send, remind them later in-session. No silent delay-send.
4. Never override quiet hours to "hit the metric".

Then return to `consent-gate` (melted).

## Measurable checks

- [ ] No send during a human-stated quiet window
- [ ] No invented timezone math
- [ ] Draft preserved; not discarded as punishment

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling packs: [README suite footer](../../README.md).
