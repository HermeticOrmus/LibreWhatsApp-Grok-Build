# Changelog

## [1.0.0] - 2026-09-30

The Grok edition: one marketplace add brings the Grok-native skills plus the LibreWhatsApp pack, pinned by commit. Draft-only and consent-first everywhere. Every crack this release found and sealed is in [LEDGER.md](./LEDGER.md).

### Added

- `plugins/libre-whatsapp-grok/`: the three melted skills (`draft-reply`, `consent-gate`, `template-scrub`) as an installable Grok plugin with `.grok-plugin/plugin.json` (version 1.0.0).
- `.grok-plugin/marketplace.json` (`libre-whatsapp-grok`): the Grok-native plugin, then the LibreWhatsApp-Claude-Code plugins `pull`, `grab` and `transcribe` as remote entries pinned to commit `4e9dcc1`. The pack's `push` is held out: its `--send` flag skips the preview (LEDGER K-09).
- `scripts/pin-pack.sh`: moves every pack entry to the pack's current main HEAD, adds new pack plugins, drops removed ones, and prints the diff. `--check` fails when the pack's plugin set changed.
- `.github/workflows/validate.yml`: validates the plugin, checks the dogfood copies, checks every pinned commit is reachable, checks the pack plugin names, and installs every entry in a clean `GROK_HOME`.
- Issue forms for feedback, routing misses and plugin proposals, with the `feedback`, `routing-miss` and `plugin-proposal` labels.
- `LEDGER.md`, the kintsugi ledger: 10 cracks sealed, 4 open.

### Changed

- The melted skills moved from `skills/` to `plugins/libre-whatsapp-grok/skills/`. The stubs moved to `stubs/skills/` and the orchestrator from `AGENTS/` to `stubs/agents/`; none of them install. Each stub names the pack plugin that holds the real depth, and its description starts "Stub cue".
- Install is `grok plugin marketplace add HermeticOrmus/LibreWhatsApp-Grok-Build`, then `grok plugin install <plugin>@libre-whatsapp-grok`. README, QUICK_START, AGENTS, CONTRIBUTING, DEPTH_MATRIX and MELT_RULES follow the new layout.
- README header follows the Ormus GitHub standard; the Depth table counts what installs.
- `.grok/skills/` stays as the dogfood copy of the plugin skills and the stubs, and `.grok/plugins/librewhatsapp-core/` stays as the dogfood copy of the stub orchestrator. CI keeps both in sync.
- What a 0.1.0 user must change: delete the skill folders you copied from `skills/` (the stubs among them are cues, not skills), then install through the marketplace. If you installed the repo root directly, uninstall that plugin; the root holds no skills now. For the pack's `pull` and `grab`, set `WA_REGISTRY=~/.grok/wa-registry.json`.

### Fixed

- 17 relative links in the dogfood copies that resolved inside `.grok/` now point at the real files (LEDGER K-07).

## [0.1.0] — 2026-09-20

### Melted (toward L3–L4)

- `draft-reply` — playbook, consent line, refuse `--send`, handoff to scrub + gate.
- `consent-gate` — preview block, confirm phrases, failure modes; no skip-gate.
- `template-scrub` — dark-pattern catalog, rewrite table, worked example.

### Fixed

- `QUICK_START.md` — clone then `cd` this repo or an explicit project path; dogfood / project / global; `test -f` checks.

### Docs

- Honest `DEPTH_MATRIX` (3 melted, 5 stub skills, 1 stub agent). No Claude totals.
- Suite footer on README, QUICK_START, depth matrix, skills, Gold Hat.
- Gold Hat messaging filter for this suite (empower vs extract table).
- Remaining skills kept as skill-specific stubs (not identical templates).
- `registry.example.json` for `~/.grok/wa-registry.json` (placeholders only).

## [0.0.1] — 2026-09-19

### Added

- Public scaffold for LibreWhatsApp-Grok-Build (v0 stubs).
- Stub SKILL.md for 8 first skills + whatsapp-orchestrator agent.
- README, LICENSE (MIT), GOLD_HAT, QUICK_START, CONTRIBUTING, SECURITY.
- Depth matrix + melt rules docs.
- Gold Hat messaging posture: draft-only, consent-gate, quiet-hours, template-scrub.

### Notes

- Honest stubs — not fake upstream depth counts. Melt next.
