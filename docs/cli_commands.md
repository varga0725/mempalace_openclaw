# CLI Commands Reference

Quick reference for the `mempalace` command-line interface.

| Command | Description | Key Flags |
| :--- | :--- | :--- |
| `init <dir>` | Initializes a wing and detects rooms. | `--yes` (Auto-accept) |
| `mine <dir>` | Ingests files into the palace. | `--mode convos`, `--wing`, `--no-gitignore` |
| `search <query>` | Semantic search for memories. | `--wing`, `--room`, `--results` |
| `compress` | Compresses drawers using AAAK. | `--wing`, `--dry-run`, `--config` |
| `wake-up` | Generates L0+L1 context. | `--wing` |
| `split <dir>` | Splits mega-files into sessions. | `--output-dir`, `--min-sessions` |
| `repair` | Rebuilds vector index from SQLite. | N/A |
| `status` | Shows palace stats. | N/A |
