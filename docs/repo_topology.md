# Repository topology

This repository is the canonical source of truth for ByteWolf's MemPalace work.

## What lives here

### Core MemPalace
- Python package and main product code remain at the repository root.
- Existing MCP/server code remains part of the main MemPalace codebase.

### Imported OpenClaw integration
- `integrations/openclaw/`
- This directory is imported from the standalone `openclaw-mempalace` repository.
- It contains the OpenClaw plugin package, session-save hook, install docs, verification docs, operations notes, and backend abstraction work.

### Imported reference material from the private fork
- `docs/`
- `docs/reference/private-fork/`
- These files were brought over from the more advanced private `mempalace-openclaw` fork so the canonical repo keeps the relevant architecture and MCP/OpenClaw notes in one place.

## Intent

This layout avoids multiple competing source-of-truth repositories.

- `mempalace_openclaw` = canonical repo
- `integrations/openclaw/` = OpenClaw integration surface
- private fork content = mined and imported here as docs/reference or targeted code

## Next merge direction

Future work should happen here first.

Recommended follow-up:
1. reconcile `integrations/openclaw/` with the MCP/server path already present in the main MemPalace codebase
2. remove duplicated bridge/backend logic where the main MemPalace repo already provides a better interface
3. decide whether the standalone `openclaw-mempalace` repo becomes deprecated or mirrored from this directory
