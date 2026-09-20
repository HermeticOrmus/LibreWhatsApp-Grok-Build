# Depth matrix

Update this table when melting. Status words mean what they say:

| Status | Meaning |
|--------|---------|
| stub | Thin cue only (about L1–L2). Usable as a reminder, not a playbook. |
| melted | Real Grok skill toward L3–L4: when-to-use, steps, measurable checks, example, output shape, governed handoffs. |

Depth labels used in this pack:

| Level | Meaning |
|-------|---------|
| L1 | Name / cue only |
| L2 | When-to-use + hard rules |
| L3 | Systematic playbook: steps, pass/fail checks, output shape |
| L4 | Governed: examples, failure modes, consent/quiet-hours handoff, no skip-gate |

This repo is **not** L3–L4 suite-wide. Three messaging skills are melted toward L3–L4. The rest are honest stubs. Never copy Claude plugin / command totals into this inventory. Upstream [LibreWhatsApp-Claude-Code](https://github.com/HermeticOrmus/LibreWhatsApp-Claude-Code) is proof that the *job* exists, not a count this repo has earned.

| ID | Kind | Status | Source (Claude, for melt) | Notes |
|----|------|--------|---------------------------|-------|
| draft-reply | skill | melted | plugins/push (compose + format; **no** `--send`) | L3–L4 playbook. Draft-only; handoff to scrub + gate. |
| consent-gate | skill | melted | plugins/push (preview/confirm + safety) | L3–L4 governed gate. `--send` residue stripped. |
| template-scrub | skill | melted | Gold Hat new (anti-spam) | L3–L4 catalog + rewrite. Never send. |
| chat-pull | skill | stub | plugins/pull (only-new, registry, sender gotcha) | Cue only. No invented state protocol. |
| thread-triage | skill | stub | session patterns | Cue only. No nag scores. |
| quiet-hours | skill | stub | Gold Hat new (Grok-native) | Cue only. No timezone engine. |
| grab-snippet | skill | stub | plugins/grab | Cue only. |
| voice-local | skill | stub | plugins/transcribe | Cue only. Local Whisper; no cloud STT. |
| whatsapp-orchestrator | agent | stub | upstream plugin orchestration | Coordinates; not a melted specialist. |

This repo now: **3 melted skills**, **5 stub skills**, **1 stub agent**.

Dogfood copies of every skill live at `.grok/skills/<name>/SKILL.md` and must match `skills/<name>/SKILL.md`.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](../README.md). Systems map: https://ormus.solutions/systems
