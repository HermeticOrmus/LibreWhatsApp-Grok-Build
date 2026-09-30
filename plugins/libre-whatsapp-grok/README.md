# libre-whatsapp-grok

The Grok-native layer of [LibreWhatsApp-Grok-Build](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build): three WhatsApp skills melted for Grok Build. They draft and gate; they never send on their own.

| Skill | Job |
|-------|-----|
| `draft-reply` | Draft a WhatsApp reply for human confirm; never auto-send |
| `template-scrub` | Strip urgency fakes, guilt and blast copy; rewrite toward consent |
| `consent-gate` | Preview every outbound message; GATE OPEN only on an explicit confirm phrase |

Pass order: `draft-reply`, then `template-scrub`, then `consent-gate`. A send tool may run only after the gate opens.

## Install

```bash
grok plugin marketplace add HermeticOrmus/LibreWhatsApp-Grok-Build
grok plugin install libre-whatsapp-grok@libre-whatsapp-grok
```

The same marketplace offers the LibreWhatsApp-Claude-Code plugins `pull`, `grab` and `transcribe`, pinned by commit. The pack's `push` is held out: its `--send` flag skips the preview this plugin requires.

The stubs (`chat-pull`, `thread-triage`, `quiet-hours`, `grab-snippet`, `voice-local`) and the stub orchestrator are not part of this plugin. They live in [`stubs/`](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/tree/main/stubs), and each names the pack plugin with the real depth. Honest table: [docs/DEPTH_MATRIX.md](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/docs/DEPTH_MATRIX.md).

Gold Hat: draft-only messaging, consent gates, no dark spam patterns. [GOLD_HAT.md](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build/blob/main/GOLD_HAT.md)
