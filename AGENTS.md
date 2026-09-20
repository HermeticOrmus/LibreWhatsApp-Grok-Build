# LibreWhatsApp-Grok-Build — suite agents

> Ported and melted for **Grok Build**. Not a dumb Claude clone.

**Doctrine hub:** [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md`
**Gold filter:** Does this empower or extract? → [GOLD_HAT.md](./GOLD_HAT.md)

## Messaging posture (non-negotiable)

- **Draft-only** until a human confirm gate passes
- **No dark spam patterns** (urgency fakes, guilt, silent mass-blast)
- **Teach consent** on every outbound path
- Provider is a swappable seam (Periskope reference); logic stays in skills

## Melted vs stub (honest)

Melted toward L3–L4: `draft-reply`, `consent-gate`, `template-scrub`.
Still stubs: `chat-pull`, `thread-triage`, `quiet-hours`, `grab-snippet`, `voice-local`, `whatsapp-orchestrator`.
Counts: [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## How to use this suite

1. Install skills (see [QUICK_START.md](./QUICK_START.md)).
2. Keep Reality OS as the global doctrine layer.
3. Use melted skills for draft / scrub / gate; use `AGENTS/whatsapp-orchestrator.md` for a full pass (stub coordinator).

## Agents in this repo

| Agent | File | Role |
|-------|------|------|
| whatsapp-orchestrator | `AGENTS/whatsapp-orchestrator.md` | Coordinates pull, triage, draft, scrub, quiet-hours, consent |

## Liquid Gold

Recognize gold in LibreWhatsApp-Claude-Code → strip Claude residue (`--send`, `~/.claude/`) → integrate with Grok skills / `.grok/` / Periskope MCP → dogfood.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Sibling Libre*-Grok-Build packs: [README suite footer](./README.md). Systems map: https://ormus.solutions/systems
