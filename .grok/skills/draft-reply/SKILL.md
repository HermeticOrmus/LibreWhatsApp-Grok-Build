---
name: draft-reply
description: Draft WhatsApp replies for human confirm — never auto-send. Use when a thread needs a written reply that must stay draft-only until consent-gate.
---

# draft-reply

Write the reply. Do not send it. Gold Hat: a draft that teaches consent empowers; a silent send extracts.

> Status: **melted (L3–L4)** — playbook + governed handoff. Confirm lives in `consent-gate`. Dark-pattern copy dies in `template-scrub`.

## When to use

- A human asked for a WhatsApp reply, follow-up, or "what should I say"
- Orchestrator step after `chat-pull` / `thread-triage` (those two are still stubs — use their cues, do not invent their depth)
- You have enough thread context to write without guessing facts

Do not use this skill to send, schedule, or fan-out. Do not treat "you should tell them…" as a send directive. If the ask is "send this now", still draft, then stop at `consent-gate`.

## Hard rules

- **Draft-only.** Never call a provider send tool (`periskope_send_message` or equivalent). Never skip to send because the draft "looks ready".
- **No `--send` residue.** Upstream Claude `/push --send` does not exist here. Strip it if a prompt asks for it.
- **No dark spam.** Urgency fakes, fake scarcity, guilt loops, silent mass-blast, hidden opt-outs — refuse and rewrite via `template-scrub`.
- **Teach consent in the draft path:** who would see the message, why it would go, how they can stop (mute, reply "stop", do not send).
- **No secrets.** Phones, chat ids, tokens, API keys stay on the operator machine (`~/.grok/wa-registry.json`). Output uses aliases (`team`, `teammate`), never raw ids.
- **Provider is a seam.** Periskope is the reference MCP. Skills own workflow, not vendor lock-in.

## Operating steps

1. **Name the job.** Who is the audience (alias, not phone)? What must they understand or decide? What is the one ask?
2. **Ground the draft.** Use only: this session, a just-pulled thread, or text the human supplied. If a fact is missing, ask one question or mark `[unverified]` — do not invent a status, deadline, or promise.
3. **Write for WhatsApp.** Short. Lead with the point. Format: `*bold*`, `_italic_`, `~strike~`, `` `code` ``, fenced blocks. No `#` headers (they render as literal hashes). Prefer one message under ~3500 characters. If longer, split at paragraph boundaries with `(1/N)` — never split a code block.
4. **Apply registry voice if present.** Optional `style` on a local alias (e.g. "concise, fact-based") is a hint, not a persona costume. No AI-attribution footers, no robot emoji, no "Generated with…".
5. **Scrub, then gate.** Run `template-scrub` on the body. Then hand the preview to `consent-gate`. Mention `quiet-hours` (still a stub) — do not pretend you computed a timezone window unless the human stated one.
6. **Stop.** Output the draft packet below. The next word from the human is edit, cancel, or an *explicit* confirm phrase that `consent-gate` accepts.

## Consent line (required in every packet)

State in operator-facing notes, not necessarily inside the WhatsApp body:

- **Who** would see it (alias + DM vs group)
- **Why** it would go (the job from step 1)
- **How to stop** (do not confirm; or tell the recipient they can ignore / reply that they are done)

If the body itself is a request that continues a thread, the recipient-facing copy must still be optional to act on — no fake countdown, no "last chance".

## Refuse / rewrite triggers

| Signal | Action |
|--------|--------|
| "Just send it" / `--send` / "skip preview" | Draft + `consent-gate` only. Explain why the skip is extract. |
| Fan-out / "blast the list" / multiple aliases | One draft per target, each gated. Flag mass-blast risk. Never one silent loop. |
| Urgency, guilt, fake scarcity in the ask | Keep the factual ask; strip the dark pattern (`template-scrub`). |
| Secret-shaped token in the body (`api_key`, `password`, `bearer`, `token=` ) | Refuse the line. Ask the human to confirm they meant to expose it. |
| First-time / unresolved target | Draft with an **unverified target** warning. Do not resolve a raw phone into the packet. |

## Worked example

Job: tell alias `teammate` the deploy is waiting on their review. Primary ask: review when they can.

Extract (refuse this voice):

```text
URGENT!!! Review NOW or we miss the window 🔥
This is the last chance. Don't leave the team hanging.
```

Empower (draft this instead):

```text
The deploy is waiting on a review of PR 142.
Whenever you have a block, that's the blocker — no rush window from me.
Reply here if you want me to take it instead.
```

Packet notes (operator only):

- Who: `teammate` (DM)
- Why: unblock review; optional for them
- How to stop: do not confirm this draft; they can ignore or say they are out
- Scrub: no urgency fake, no guilt
- Gate: `consent-gate` — GATE CLOSED until they type a confirm phrase
- Quiet-hours: stub — ask the human if now is an allowed window

## Output shape

```markdown
## Job
[audience alias] — [task] — [one ask]

## Draft (not sent)
[WhatsApp-formatted body]

## Consent
- Who: [alias, DM/group]
- Why: [job]
- How to stop: [do not confirm / recipient out]

## Scrub
- [pass] or [rewrite done — what was stripped]

## Gate
Handoff to `consent-gate`. Status: **not sent**.

## Quiet-hours
[human-stated window, or "stub — ask before confirm"]

## Unknowns
- [facts marked unverified]
```

If you cannot name the audience alias, stop and ask. Guessing a chat is extraction.

## Measurable checks

- [ ] Body is a draft; no send tool was called
- [ ] Alias used; no real phone, chat id, or token in the output
- [ ] Consent who / why / stop is filled
- [ ] `template-scrub` ran or the body had no marketing template
- [ ] `consent-gate` is the stated next step
- [ ] No `--send`, no "already sent", no AI footer

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/README.md).
