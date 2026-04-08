# OpenClaw integration TODO

## Priority now

- [ ] Repoint backend work toward canonical MemPalace interfaces in this repository
- [ ] Implement a real `mcp` backend using `mempalace.mcp_server`
- [ ] De-emphasize legacy inline Python bridge code
- [ ] Review whether direct ChromaDB writes in the integration layer can be removed

## Keep in integration layer

- [ ] plugin manifest and config schema
- [ ] hook definitions
- [ ] OpenClaw install and verification docs
- [ ] OpenClaw operations guidance

## Remove over time

- [ ] duplicated backend/storage logic that belongs in the canonical repo
- [ ] legacy standalone plugin assumptions from before the merge
