# Project Index: MemPalace

Generated: 2026-04-08

## 📁 Project Structure

- `mempalace/` - Core logic and source code
    - `__main__.py`, `cli.py` - CLI Entry points
    - `mcp_server.py` - MCP Server for Claude Code integration
    - `knowledge_graph.py` - Temporal Entity-Relationship Graph (SQLite)
    - `searcher.py` - Semantic search implementation (ChromaDB)
    - `miner.py`, `convo_miner.py` - Ingestion engines for files and conversations
    - `dialect.py` - AAAK compressed memory dialect
    - `layers.py` - Memory hierarchy (L0, L1, etc.)
    - `palace_graph.py` - Structural connectivity (wings, rooms, tunnels)
    - `config.py` - Configuration management
- `tests/` - Test suite
- `docs/` - (Not explicitly present, but READMEs and examples are used)
- `benchmarks/` - Performance benchmarks
- `examples/` - Setup guides and tutorials
- `hooks/` - Custom hooks for the environment

## 🚀 Entry Points

- CLI: `mempalace/cli.py` - Primary interface for mining, searching, and managing memories.
- MCP: `mempalace/mcp_server.py` - Provides `mempalace_*` tools for AI agents.
- Tests: `tests/` - Python test suite.

## 📦 Core Modules

### Module: KnowledgeGraph
- Path: `mempalace/knowledge_graph.py`
- Exports: `KnowledgeGraph` class
- Purpose: Manages a temporal graph of entities and relationships using SQLite.

### Module: Searcher
- Path: `mempalace/searcher.py`
- Exports: `search_memories` function
- Purpose: Implements semantic search over "drawers" using ChromaDB.

### Module: Miner
- Path: `mempalace/miner.py` & `mempalace/convo_miner.py`
- Exports: `mine`, `mine_convos`
- Purpose: Processes source directories to extract and file memories into the palace.

### Module: Dialect
- Path: `mempalace/dialect.py`
- Exports: `Dialect` class
- Purpose: Implements the AAAK compression format for efficient memory storage.

### Module: PalaceGraph
- Path: `mempalace/palace_graph.py`
- Exports: `traverse`, `find_tunnels`, `graph_stats`
- Purpose: Manages the connectivity between memory rooms and wings.

## 🔧 Configuration

- `pyproject.toml`: Project dependencies and metadata.
- `mempalace/config.py`: Application settings and path management.

## 📚 Documentation

- `README.md`: General project overview.
- `mempalace/README.md`: Core library documentation.
- `CONTRIBUTING.md`: Contribution guidelines.
- `examples/`: Setup and usage tutorials.

## 🧪 Test Coverage

- Unit tests: ~11 files in `tests/`
- Integration tests: Included in the test suite.

## 🔗 Key Dependencies

- `chromadb`: Vector database for semantic search.
- `sqlite3`: Local storage for the knowledge graph.
- `argparse`: CLI argument parsing.

## 📝 Quick Start

1. `mempalace init <dir>` - Initialize a project wing.
2. `mempalace mine <dir>` - Ingest data into the palace.
3. `mempalace search "query"` - Retrieve relevant memories.
