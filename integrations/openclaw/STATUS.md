# OpenClaw integration status

This directory was imported from the standalone `openclaw-mempalace` repository and is now maintained inside the canonical `mempalace_openclaw` repository.

## What this directory is

This is the OpenClaw integration surface for MemPalace.

It currently contains:
- the OpenClaw plugin package
- the session-save hook
- install and verification docs
- operations and backend-abstraction notes

## What this directory is not

It is not the MemPalace core implementation.

Core behavior should live in the main repository code when possible.
If functionality already exists in the main MemPalace codebase, the long-term goal is to call into that cleanly instead of duplicating logic here.

## Current migration state

### Kept here for now
- OpenClaw-specific packaging
- OpenClaw-specific hooks
- OpenClaw-specific install and operations docs
- temporary adapter/backend abstraction work

### To reconcile with main repo later
- direct Python bridge logic
- duplicated backend logic that should eventually route through canonical MemPalace interfaces
- legacy OpenClaw integration experiments

## Long-term target

The desired end state is:
- MemPalace core remains canonical at repository root
- OpenClaw integration remains canonical under `integrations/openclaw/`
- duplicated transport logic is removed in favor of one clean backend path
