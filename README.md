# Bulk Text Index Agents

A pattern to handle massive text collections in tools like M365 Copilot (multi-day transcripts, logs, interview dumps, documentation) efficiently without bloating the context window, hit token limit or losing accuracy.

**Use cases:** Q&A agents, backlog creation, timeline reconstruction, report generation.

```text
 ┌──────────────────────────────────┐
 │         Raw text files           │
 └──────────────┬────────────┬──────┘
                │            │
                │            │ Pass raw text files
                ▼            │
 ┌────────────────────────┐  │
 │ Agent 1 Indexer        │  │
 │ (Run for each file)    │  │
 └──────────────┬─────────┘  │
                │            │
                │ Pass index │
                │ files      │
                ▼            │
 ┌────────────────────────┐  │
 │ Agent 2 Consolidator   │  │
 └──────────────┬─────────┘  │
                │            │
                │ Pass master│
                │ index file │
                ▼            ▼
 ┌──────────────────────────────────┐
 │ Agent 3 (Your use case)          │
 └──────────────────────────────────┘
```

> [!TIP]
> **Getting Started:** Clone the repo or download this `README.md` and the prompt files from the [`prompts/`](prompts/) directory to plug them directly into your agent workspace.

## How to Use These Prompts

1. **Step 1 — Index individual files**  
   Run [Agent 1 (Indexer)](prompts/agent-1-indexer.md) separately on each raw text file. It extracts verbatim anchor phrases, decisions, and local topic segments without summarizing the whole file.

2. **Step 2 — Consolidate into a Master Index**  
   Feed all generated index files into [Agent 2 (Consolidator)](prompts/agent-2-consolidator.md). It generates a unified Topic Map, a Reversal Log (tracking position changes over time), and an Open Items list.

3. **Step 3 — Execute your use case**  
   Feed the Master Index and the raw files to [Agent 3 (Query Agent)](prompts/agent-3-query.md) (or customize it for backlog extraction). The agent uses the index as a map to locate exact verbatim anchors in the raw files and produces fast, grounded answers with zero hallucinations.
