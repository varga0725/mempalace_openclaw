# Merge plan

## Canonical repository

`mempalace_openclaw` is the source of truth.

## Imported sources

### 1. `openclaw-mempalace`
Imported under:
- `integrations/openclaw/`

Purpose:
- provide the dedicated OpenClaw plugin, hook, install docs, verification docs, operations model, and backend abstraction work

### 2. `mempalace-openclaw` (private fork)
Imported selectively into:
- `docs/`
- `docs/reference/private-fork/`
- `integrations/openclaw/legacy/`

Purpose:
- preserve useful MCP/OpenClaw architecture and experimentation notes
- keep advanced private-fork discoveries visible while converging on one repo

## Merge principles

1. Core MemPalace logic belongs in the main repository, not in duplicated plugin glue.
2. OpenClaw-specific packaging and hooks belong under `integrations/openclaw/`.
3. Private-fork imports should be treated as references until reconciled.
4. New work should happen in this repository first, not in competing side repos.

## Next cleanup steps

### Cleanup wave 1
- make directory roles explicit in docs
- mark imported legacy files clearly
- define what is authoritative vs reference-only

### Cleanup wave 2
- compare `integrations/openclaw/` bridge/backend logic with canonical MemPalace interfaces
- replace duplicated paths with calls into canonical interfaces where possible
- prioritize the repository's own MCP/server surface as the preferred non-legacy backend target

### Cleanup wave 3
- decide whether standalone `openclaw-mempalace` becomes deprecated or a mirror
- decide whether private fork stays private reference-only or is archived after reconciliation
