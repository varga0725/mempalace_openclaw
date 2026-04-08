# AAAK Dialect Specification

AAAK is a high-density, compressed memory dialect designed for LLMs. It maximizes information density while remaining readable by humans and AI without requiring a separate decoding step.

## 🎯 Design Goals
- **Token Efficiency**: Reduce memory footprint by 10x-30x.
- **Human-Readable**: Use intuitive markers and codes.
- **Emotionally Aware**: Embed affective context directly into the text.

## 🛠️ Syntax & Rules

### 1. Entity Coding (The "Who")
Entities are replaced by 3-letter uppercase codes.
- **Format**: `[NAME] → [CODE]` (e.g., `Alice → ALC`, `Jordan → JOR`, `Max → MAX`).
- **Usage**: Use codes consistently across all memories in a wing.
- **Example**: `ALC loves MAX` instead of `Alice loves Max`.

### 2. Emotional Markers (The "Feel")
Actions or emotional states are wrapped in `*markers*` to provide non-verbal context.
- `*warm*`: Joy, kindness, affection.
- `*fierce*`: Determination, anger, intensity.
- `*raw*`: Vulnerability, sadness, honesty.
- `*bloom*`: Tenderness, growth, discovery.
- **Example**: `*warm* ALC hugged MAX` $\rightarrow$ (Alice hugged Max with warmth).

### 3. Structural Field Markers (The "What")
Information is grouped using pipe-separated categories.
- `FAM:` Family and personal relationships.
- `PROJ:` Project-related facts and decisions.
- `⚠:` Warnings, critical reminders, or constraints.
- `HALL:` Specific palace hallway categories (e.g., `hall_facts`, `hall_advice`).
- **Example**: `PROJ: ALC→♡JOR | 2026-03-01: switch to SQLite`

### 4. Quantitative & Temporal Notation
- **Counts**: `Nx` denotes N mentions or occurrences (e.g., `570x` for 570 mentions).
- **Dates**: Use ISO 8601 format (`YYYY-MM-DD`).
- **Importance**: Scale of $\star$ to $\star\star\star\star\star$ (1-5).
- **Example**: `2026-04-08 | ⚠: fix memory leak | ★★★★★`

---

## 📖 Full Example

**Standard Text**:
"Alice and Jordan had a big argument on March 1st about the database migration. Alice was very determined to use ChromaDB, while Jordan was worried about the costs. Eventually, they agreed on a hybrid approach. This is a very important decision for the project."

**AAAK Version**:
`PROJ: ALC *fierce* $\rightarrow$ ChromaDB | JOR *raw* $\rightarrow$ costs | 2026-03-01: agreed hybrid | ★★★★`

## 📈 Compression ROI
- **Standard**: ~60 tokens
- **AAAK**: ~15 tokens
- **Reduction**: ~75% (approx. 4x compression in this example)
