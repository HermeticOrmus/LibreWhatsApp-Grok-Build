---
name: consent-gate
description: Preview-and-confirm gate before any outbound WhatsApp message. Use whenever send is considered — draft-only until an explicit human confirm phrase.
---

# consent-gate

The send does not happen until a human says so, in words this skill accepts. Gold Hat: preview-and-confirm empowers; skip-gates and silent blast extract.

> Status: **melted (L3–L4)** — governed gate. Upstream Claude `/push --send` is residue: it does not ship here.

## When to use

- Any path that might touch a provider send tool
- After `draft-reply` + `template-scrub` produce a body
- The human said "send", "just ship it", "blast them", or pasted a number

If nobody is trying to send, do not run this skill as theater. If they *are* trying to send, this skill is mandatory — including when they ask to skip it.

## Hard rules

- **Draft-only until GATE OPEN.** Default is GATE CLOSED.
- **No skip flag.** There is no `--send`, `--send-trust`, or `PUSH_PREVIEW_MODE=false`. Asking for those is a closed gate plus a teach line.
- **Confirm is a phrase, not a vibe.** Conversational suggestion ("you should tell them") is not confirm. A thumbs-up emoji is not confirm. "Looks good" is not confirm.
- **One target per open gate** unless the human named every alias and accepted the mass-blast warning.
- **No secrets in the preview.** Aliases only. Registry and credentials stay on the operator machine.
- **Provider is a seam.** After GATE OPEN, the operator (or a later skill) may call the configured send. This skill does not hide that call and does not auto-loop.

## Confirm phrases (GATE OPEN)

Accept only an explicit line from the human in this session, aimed at this preview:

- `send`
- `confirm send`
- `confirm send to <alias>`

`<alias>` must match the preview's target. If they type `send` after you showed two drafts, ask which alias — do not pick.

Everything else keeps GATE CLOSED: `edit`, `cancel`, a replacement body, `later`, `queue`, silence.

`cancel` discards the preview. A replacement body is a new draft — re-run `template-scrub`, then this gate again.

## Operating steps

1. **Refuse a missing packet.** You need: audience alias, DM vs group, body, who/why/stop from `draft-reply`. If scrub has not run, run `template-scrub` first.
2. **Render the preview.** Use the block below. Do not call send.
3. **Scan the body** for `(?i)(api[_-]?key|secret|password|token|bearer)\s*[:=]\s*\S+`. On match: GATE CLOSED, ask whether they meant to expose it.
4. **Flag risk.**
   - Unverified / first-seen-this-session target → warning; still need a confirm phrase.
   - Multiple aliases → mass-blast warning; require `confirm send to <alias>` per target or an explicit "send to these N aliases: …".
   - Group chat → remind that every participant sees it.
5. **Quiet-hours (stub).** If the human stated a quiet window and now is inside it, GATE CLOSED and queue-or-refuse in words. If they did not state a window, say `quiet-hours` is still a stub — ask "is now an allowed window?" Do not invent timezone math.
6. **Wait.** Print GATE CLOSED and the confirm phrases. Stop.
7. **On a valid confirm phrase only:** print GATE OPEN, the exact body, the alias, and "send tool may run now". Then — and only then — a send tool is allowed. Log metadata only (alias, char count, timestamp). Never log the body or raw ids in repo files.

## Preview block

```text
CONSENT PREVIEW — not sent
To:       <alias>  (dm|group)
Channel:  wa
Length:   <N chars>
Scrub:    pass | rewritten
Quiet:    allowed | closed (human-stated) | stub-ask
Secrets:  none flagged | REFUSE
---
<body, WhatsApp-formatted>
---
Who sees this: <alias / group>
Why it would go: <job>
How to stop: do not confirm; or cancel
Confirm: send | confirm send | confirm send to <alias>
Edit:    reply with replacement body
Cancel:  cancel
```

## Failure modes

| Failure | Gate | Teach |
|---------|------|-------|
| Human said "just send" / `--send` | CLOSED | Skip-gates are extract. Confirm phrase or cancel. |
| "Looks good" / "ok" / 👍 | CLOSED | Need `send` or `confirm send to <alias>`. |
| Unresolved raw phone in the prompt | CLOSED | Map to a local alias in `~/.grok/wa-registry.json`. Do not echo the number. |
| Fan-out without naming aliases | CLOSED | Mass-blast is a dark pattern unless each target is consented. |
| Secret-shaped token | CLOSED | Strip or human re-confirms exposure. |
| Quiet window (human-stated) | CLOSED | Queue the draft; do not "just this once". |
| Provider send called before GATE OPEN | **incident** | Stop. Say the gate was bypassed. Do not retry send. |

## Worked example

Draft is ready for `teammate`. Human: "looks good, ship it."

```markdown
## Gate
CLOSED

## Why closed
"ship it" / "looks good" is not a confirm phrase.

## Preview
[CONSENT PREVIEW block]

## Teach
A confirm is the word `send` (or `confirm send to teammate`) after you have seen the body. That is the autonomy line — not friction for its own sake.

## Next
Reply `send` to open the gate, or paste an edit, or `cancel`.
```

Only if they then reply `confirm send to teammate`:

```markdown
## Gate
OPEN

## Target
teammate (dm)

## Body
[exact draft]

## Next
Send tool allowed for this one alias and this exact body. Do not add recipients.
```

## Output shape

```markdown
## Gate
OPEN | CLOSED

## Why
[phrase accepted / which rule held]

## Preview
[block above, always shown when CLOSED; shown again when OPEN]

## Risks
- [unverified target / group / fan-out / secrets / quiet-hours]

## Teach
[one sentence on why the gate exists]

## Next
[wait for phrase | send tool allowed | cancel]
```

## Measurable checks

- [ ] Preview shown before any send tool
- [ ] GATE OPEN only after an accepted confirm phrase
- [ ] No `--send` path, no default-open
- [ ] Fan-out did not silently loop
- [ ] No real phone, chat id, or token in the preview
- [ ] Quiet-hours either honored from a human-stated window or marked stub-ask
- [ ] Teach sentence present (why this gate)

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](../../README.md).
