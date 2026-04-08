# MemPalace Architecture Guide

MemPalace is a local-first memory system designed to provide AI agents with a structured, scalable, and temporal memory without relying on expensive cloud-based knowledge graphs.

## 🏛️ The Palace Concept

The system uses a spatial metaphor to organize information, mirroring the "Method of Loci" (Memory Palace technique).

### 🚩 Wings (Domains)
A **Wing** represents a high-level domain of knowledge, typically corresponding to a specific project, a person, or a category of information (e.g., `wing_code`, `wing_user`, `wing_my_app`).

### 🚪 Rooms (Ideas)
Within each wing, information is organized into **Rooms**. A room represents a specific named idea, a task, or a topic (e.g., `chromadb-setup`, `pricing-discussion`). 

### 🗄️ Drawers (Memories)
The smallest unit of storage is a **Drawer**. A drawer contains a verbatim snippet of information, its metadata (wing, room, source), and a timestamp.

### 🚇 Tunnels (Cross-links)
A **Tunnel** occurs when the same **Room** name appears in multiple **Wings**. This creates a natural bridge between different domains, allowing the agent to traverse the palace graph and find connected ideas across disparate projects.

---

## 📚 The 4-Layer Memory Stack

To optimize context window usage, MemPalace employs a tiered retrieval strategy.

| Layer | Name | Size (Approx) | Trigger | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **L0** | **Identity** | ~100 tokens | Always Loaded | Defines "Who am I?" and core traits. |
| **L1** | **Essential Story** | 600-900 tokens | Always Loaded | A compact summary of the most important/recent memories. |
| **L2** | **On-Demand** | 200-500 tokens | Topic Trigger | Loaded when a specific wing or room is mentioned. |
| **L3** | **Deep Search** | Unlimited | Explicit Query | Full semantic search via ChromaDB. |

### Layer Workflow
1. **Wake-up**: The agent starts with L0 + L1, providing immediate context of identity and the "big picture".
2. **Recall**: If the conversation shifts to "Project X", the agent triggers an L2 retrieval for `wing_project_x`.
3. **Investigation**: If a specific fact is missing, the agent performs an L3 semantic search.

---

## 🕸️ The Temporal Knowledge Graph

Beyond semantic search, MemPalace maintains a **Temporal Knowledge Graph** implemented in SQLite.

- **Nodes**: Entities (People, Projects, Tools, Concepts).
- **Edges**: Typed relationships (e.g., `works_on`, `child_of`, `loves`).
- **Temporal Validity**: Every fact has a `valid_from` and `valid_to` date. This allows the AI to query the state of the world "as of" a specific date, handling evolving facts (e.g., a person changing jobs).

## ⚙️ Data Flow

`Source Files` $\rightarrow$ `Miner` $\rightarrow$ `ChromaDB (Drawers)` $\rightarrow$ `KnowledgeGraph (Triples)` $\rightarrow$ `MemoryStack` $\rightarrow$ `AI Agent`
