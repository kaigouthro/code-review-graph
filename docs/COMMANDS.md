# All Available Commands

## Skills (Claude Code slash commands)

### `/code-review-graph:build-graph`
Build or update the knowledge graph.
- First time: performs a full build
- Subsequent: incremental update (only changed files)

### `/code-review-graph:review-delta`
Review only changes since last commit.
- Auto-detects changed files via git diff
- Computes blast radius (2-hop default)
- Generates structured review with guidance

### `/code-review-graph:review-pr`
Review a PR or branch diff.
- Uses main/master as base
- Full impact analysis across all PR commits
- Structured output with risk assessment

## MCP Tools

### `build_or_update_graph_tool`
```
full_rebuild: bool = False    # True for full re-parse
repo_root: str | None         # Auto-detected
base: str = "HEAD~1"          # Git diff base
```

### `get_impact_radius_tool`
```
changed_files: list[str] | None  # Auto-detected from git
max_depth: int = 2               # Hops in graph
repo_root: str | None
base: str = "HEAD~1"
```

### `query_graph_tool`
```
pattern: str    # callers_of, callees_of, imports_of, importers_of,
                # children_of, tests_for, inheritors_of, file_summary
target: str     # Node name, qualified name, or file path
repo_root: str | None
```

### `get_review_context_tool`
```
changed_files: list[str] | None
max_depth: int = 2
include_source: bool = True
max_lines_per_file: int = 200
repo_root: str | None
base: str = "HEAD~1"
```

### `semantic_search_nodes_tool`
```
query: str           # Search string
kind: str | None     # File, Class, Function, Type, Test
limit: int = 20
repo_root: str | None
```

### `embed_graph_tool`
```
repo_root: str | None
```
Requires: `pip install code-review-graph[embeddings]`

### `list_graph_stats_tool`
```
repo_root: str | None
```

### `get_docs_section_tool`
```
section_name: str    # usage, review-delta, review-pr, commands, legal, watch, embeddings, languages, troubleshooting
```

## CLI Commands

```bash
# Full build
code-review-graph build --full

# Incremental update
code-review-graph update

# Check status
code-review-graph status

# Watch mode
code-review-graph watch

# Custom base ref
code-review-graph update --base origin/main
```
