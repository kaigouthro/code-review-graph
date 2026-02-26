# Code Review Graph — User Guide

**Version:** v1.1.0 (Feb 26, 2026)

## Quick Installation (30 seconds)

```bash
git clone https://github.com/tirth8205/code-review-graph.git
cd code-review-graph
python3 -m venv .venv && source .venv/bin/activate
pip install -e .
```

Add to your project's `.mcp.json`:
```json
{
  "mcpServers": {
    "code-review-graph": {
      "command": "/path/to/code-review-graph/.venv/bin/python",
      "args": ["-m", "code_review_graph.main"],
      "cwd": "/path/to/code-review-graph"
    }
  }
}
```

Then build the graph once:
```
/code-review-graph:build-graph
```

## Core Workflow

### 1. Build the graph (first time only)
```
/code-review-graph:build-graph
```
Parses your entire codebase. Takes ~10s for 500 files.

### 2. Review changes (daily use)
```
/code-review-graph:review-delta
```
Reviews only files changed since last commit + everything impacted. 5-10x fewer tokens than a full review.

### 3. Review a PR
```
/code-review-graph:review-pr
```
Comprehensive structural review of a branch diff with blast-radius analysis.

### 4. Watch mode (optional)
```bash
code-review-graph watch
```
Auto-updates the graph on every file save. Zero manual work.

### 5. Semantic search (optional)
```bash
pip install -e ".[embeddings]"
```
Then use `embed_graph_tool` to compute vectors. `semantic_search_nodes_tool` automatically uses vector similarity.

## Token Savings

| Scenario | Without graph | With graph |
|----------|:---:|:---:|
| Review 200-file project | ~150k tokens | ~25k tokens |
| Incremental review | ~150k tokens | ~8k tokens |
| PR review | ~100k tokens | ~15k tokens |

## Supported Languages

Python, TypeScript, JavaScript, Go, Rust, Java, C#, Ruby, Kotlin, Swift, PHP, C/C++

## What Gets Indexed

- **Nodes**: Files, Classes, Functions/Methods, Types, Tests
- **Edges**: CALLS, IMPORTS_FROM, INHERITS, IMPLEMENTS, CONTAINS, TESTED_BY, DEPENDS_ON

See [schema.md](schema.md) for full details.
