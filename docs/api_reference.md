# API Reference

Detailed technical specification of the MemPalace core components.

## 🥞 MemoryStack
The primary interface for interacting with the 4-layer memory system.

### `MemoryStack(palace_path=None, identity_path=None)`
- **`wake_up(wing=None) -> str`**: Generates L0 (Identity) and L1 (Essential Story) text.
- **`recall(wing=None, room=None, n_results=10) -> str`**: Performs L2 on-demand retrieval.
- **`search(query, wing=None, room=None, n_results=5) -> str`**: Performs L3 deep semantic search.
- **`status() -> dict`**: Returns health and token stats for all layers.

---

## 🕸️ KnowledgeGraph
A temporal entity-relationship graph implemented via SQLite.

### `KnowledgeGraph(db_path=None)`
- **`add_entity(name, entity_type="unknown", properties=None) -> str`**: Adds or updates a node in the graph.
- **`add_triple(subject, predicate, obj, valid_from=None, valid_to=None, confidence=1.0, source_closet=None, source_file=None) -> str`**: Creates a relationship between two entities.
- **`invalidate(subject, predicate, obj, ended=None)`**: Sets the `valid_to` date for a fact, marking it as no longer true.
- **`query_entity(name, as_of=None, direction="both") -> list`**: Retrieves all facts about an entity, optionally filtered by date.
- **`query_relationship(predicate, as_of=None) -> list`**: Finds all triples of a specific relationship type.
- **`timeline(entity_name=None) -> list`**: Returns a chronological list of facts.
- **`stats() -> dict`**: Returns graph metrics (entity count, triple count, etc.).

---

## 🔍 Searcher
Handles semantic retrieval using ChromaDB.

### `search_memories(query, palace_path, wing=None, room=None, n_results=5) -> list`
Performs a vector search against the `mempalace_drawers` collection. Returns a list of hits including:
- `text`: The verbatim content.
- `wing`/`room`: The spatial location.
- `similarity`: The distance-based score.

---

## 🔠 Dialect
Implements the AAAK compressed memory format.

### `Dialect(config_path=None)`
- **`compress(text, metadata=None) -> str`**: Transforms standard text into AAAK format using entity codes and markers.
- **`decompress(aaak_text) -> str`**: (Internal) Expands AAAK back to readable text.
- **`compression_stats(original, compressed) -> dict`**: Calculates token reduction and compression ratio.
- **`count_tokens(text) -> int`**: Estimates token count.
