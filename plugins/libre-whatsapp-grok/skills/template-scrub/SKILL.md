---
name: template-scrub
description: Scrub spam and dark-pattern WhatsApp templates; rewrite toward consent copy. Use before consent-gate on any outbound draft.
---

# template-scrub

Strip extractive copy. Teach the consent rewrite. Gold Hat: if the honest job is "make them click", it does not ship.

> Status: **melted (L3–L4)** — pattern catalog + rewrite table. This skill never sends.

## When to use

- After `draft-reply` (or any human-supplied outbound body)
- Before `consent-gate`
- When the human pastes a "high-converting" blast, countdown, or guilt follow-up
- When orchestrator says "scrub this template"

Do not use this skill to raise conversion, add urgency, or A/B a darker variant. If they ask for that, refuse the tactic and offer a consent rewrite.

## Hard rules

- **No dark spam patterns:** urgency fakes, fake scarcity, guilt loops, silent mass-blast, hidden opt-outs, disguised identity.
- **Teach consent:** the recipient can see who is writing, why, and how to stop or ignore without punishment framing.
- **Draft-only.** Scrub is a rewrite. Send is `consent-gate`'s job, and only after a confirm phrase.
- **No secrets** in examples or output. Aliases, not phones.

## Operating steps

1. **Name the real job.** What does the recipient need to know or decide? If the job is only "get a reply / click / FOMO", say extract and stop until the human names a real job.
2. **Walk the catalog.** Record each hit: pattern, excerpt, why it extracts.
3. **Rewrite once.** Keep facts. Drop pressure. Add a stop/ignore path if the message asks for action.
4. **Show the delta.** Extract line → empower line. One teach sentence the human can reuse on the next template.
5. **Hand off.** Clean body goes to `consent-gate`. Do not send.

## Pattern catalog

| Pattern | Looks like | Pass | Fail |
|---------|------------|------|------|
| Urgency fake | "URGENT", "NOW", countdown, red sirens when no real deadline exists | A dated, true deadline the human verified | Invented window, "last chance", emoji panic |
| Fake scarcity | "Only 2 spots", "closing tonight" with no inventory | Real capacity the human owns and stated | Borrowed SaaS-scarcity theater |
| Guilt loop | "Don't leave us hanging", "disappointed", shame follow-ups | Neutral status + optional ask | Moral debt to force a reply |
| Silent mass-blast | Same body, many chats, no per-target confirm | One alias, or named list each gated | Hidden BCC-style fan-out |
| Hidden opt-out | No way to decline; "reply STOP" buried or missing on a campaign ask | Clear ignore/stop; no punishment | Unsubscribe maze, or "only losers skip" |
| Fake identity | AI footer, pretend-human intimacy, spoofed sender | Operator's real number/name via provider | "Generated with…", fake personalization at scale |
| Engagement bait | "If I don't hear back I'll assume X" | Wait or ask once, no trap default | Manufactured consent from silence |
| Dark CTA | Misleading button-words, packed links | One honest ask, link purpose named | Link-shortener pile, "tap to claim" |

If a deadline is real, keep the date and drop the theater: "Review due Tuesday if you can; otherwise say you are out."

## Rewrite table

| Extract | Empower |
|---------|---------|
| `URGENT!!! Need this NOW or we miss everything` | `Need a look at <thing> when you can. Real due: <date or none>.` |
| `Last chance — only 3 spots left` | `We have room for <N> if that is still true. No hold either way.` |
| `Don't leave the team hanging` | `Still blocked on this. Tell me if you want it reassigned.` |
| `I'll assume yes if no reply` | `No reply means I will wait. Reply yes/no when you know.` |
| `Blast this to the whole list` | Split per alias; each draft through `consent-gate`. |
| `Reply STOP to unsubscribe` buried under guilt | First or last line: `Ignore this if it is not useful. Reply stop and I will not follow up.` |

## Worked example

Inbound template (fail):

```text
🔥 FINAL NOTICE 🔥
You still haven't confirmed. Don't let everyone down.
Tap https://example.invalid/claim — spots vanish at midnight.
```

Scrub result (pass):

```text
Checking whether you still want in on <event>.
Details: <one sentence + the same URL named as "event page">.
Ignore this if it is not relevant. Reply "stop" and I will not follow up.
```

```markdown
## Job
Ask whether they still want in. Optional.

## Hits
1. Urgency fake — "FINAL NOTICE" / midnight vanish — no verified deadline
2. Guilt loop — "Don't let everyone down"
3. Dark CTA — "Tap … claim" hides the job

## Rewrite
[body above]

## Teach
A true deadline is a date. A countdown without a date is a dark pattern.

## Gate
Handoff to `consent-gate`. Not sent.
```

## Output shape

```markdown
## Job
[real recipient job, or EXTRACT — stopped]

## Hits
1. [pattern] — [excerpt] — [why]
2. …

## Rewrite
[WhatsApp-formatted body, or "no change"]

## Teach
[one reusable sentence]

## Gate
Not sent. Next: `consent-gate`.
```

Empty hits are allowed. Invented hits are not. If the body is already clean, say `no change` and pass it through.

## Measurable checks

- [ ] Real job named, or EXTRACT stop
- [ ] Every catalog hit has an excerpt
- [ ] Rewrite has no urgency/guilt/scarcity theater unless a human-verified fact remains
- [ ] Campaign-style asks include an ignore/stop path
- [ ] Output is a rewrite, not a send
- [ ] No real phones, tokens, or "just blast it" leftover

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/README.md).
