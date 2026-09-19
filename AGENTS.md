# LibreWhatsApp-Grok-Build — suite agents

> Ported and melted for **Grok Build**. Not a dumb Claude clone.

**Doctrine hub:** [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md`  
**Gold filter:** Does this empower or extract? → [GOLD_HAT.md](./GOLD_HAT.md)

## Messaging posture (non-negotiable)

- **Draft-only** until a human confirm gate passes
- **No dark spam patterns** (urgency fakes, guilt, silent mass-blast)
- **Teach consent** on every outbound path
- Provider is a swappable seam (Periskope reference); logic stays in skills

## How to use this suite

1. Install skills (see [QUICK_START.md](./QUICK_START.md)).
2. Keep Reality OS as the global doctrine layer.
3. Use suite skills for WhatsApp-in-session work; use `AGENTS/whatsapp-orchestrator.md` for a full pass.

## Agents in this repo

| Agent | File | Role |
|-------|------|------|
| whatsapp-orchestrator | `AGENTS/whatsapp-orchestrator.md` | Coordinates pull, triage, draft, scrub, quiet-hours, consent |

## Liquid Gold

Recognize gold in LibreWhatsApp-Claude-Code → strip Claude residue → integrate with Grok skills / `.grok/` / Periskope MCP → dogfood.
