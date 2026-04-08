# Backend selection

## Purpose

The adapter layer is now prepared for multiple backend implementations.

## Supported backend ids

Current config/backend ids:
- `python-bridge`
- `http`
- `mcp`

## Current status

### `python-bridge`
Implemented.
This is the current working backend.

### `http`
Selection path exists, but backend is still unimplemented.
Intended for a local or remote MemPalace HTTP service.

### `mcp`
Selection path exists, but backend is still unimplemented.
Intended for a MemPalace MCP server or another OpenClaw-compatible tool boundary.

## Why backend selection matters

This is the path away from a hardcoded unsafe runtime model.

Instead of baking one transport into the whole plugin, we can now evolve toward:
- a safer backend
- an officially accepted runtime boundary
- better packaging for the OpenClaw ecosystem

## Recommended future direction

Inside the canonical `mempalace_openclaw` repository, `mcp` is now the preferred future backend direction because the repository already contains an MCP/server path in the main MemPalace codebase.

`http` can still exist as an option later, but it should no longer be treated as the default next target ahead of the repository's own MCP surface.
