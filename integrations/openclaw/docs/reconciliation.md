# Reconciliation with canonical MemPalace interfaces

## Problem

The imported OpenClaw integration currently duplicates backend behavior that already exists in the canonical MemPalace repository.

Duplicated or overlapping areas include:
- semantic recall logic
- direct ChromaDB write logic
- transport/backend abstraction around those paths

## Canonical interfaces already present in this repository

The main MemPalace codebase already exposes the real source-of-truth building blocks:
- `mempalace.searcher.search_memories`
- `mempalace.convo_miner`
- `mempalace.mcp_server`
- other repository-level CLI and storage paths around the same palace data

## Current OpenClaw integration status

The OpenClaw integration still contains temporary glue under:
- `integrations/openclaw/lib/runtime-bridge.ts`
- `integrations/openclaw/lib/mempalace-adapter.ts`
- `integrations/openclaw/lib/mempalace-backends.ts`

That code was useful during standalone plugin development, but it is no longer the desired long-term source for backend behavior now that this integration lives inside the canonical MemPalace repository.

## Canonical direction

### What should stay in `integrations/openclaw/`
- OpenClaw plugin packaging
- OpenClaw hook definitions
- OpenClaw-specific install and operations docs
- OpenClaw-specific configuration/schema glue

### What should move toward canonical repository interfaces
- recall implementation
- memory write implementation
- backend transport decisions

## Preferred technical path

### Step 1
Keep the adapter abstraction, but treat it as OpenClaw-facing glue only.

### Step 2
Replace duplicated backend internals with calls to canonical repository interfaces.

Preferred order:
1. use canonical Python package interfaces instead of bespoke inline scripts
2. prefer the repository's MCP/server path where appropriate
3. shrink or remove duplicated direct ChromaDB logic from `integrations/openclaw/`

## Immediate cleanup target

The first concrete cleanup goal is:
- mark `python-bridge` as a temporary legacy backend in OpenClaw docs
- make `mcp` the preferred future backend path because this repository already ships `mempalace/mcp_server.py`
- avoid expanding duplicated storage logic further inside the OpenClaw integration subtree
