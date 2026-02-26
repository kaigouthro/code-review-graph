# Features

## v1.1.0 (Current)
- **Watch mode**: `code-review-graph watch` — auto-rebuilds graph on file changes
- **Vector embeddings**: Optional `pip install .[embeddings]` for semantic code search
- **Go, Rust, Java verified**: 12+ languages with dedicated test coverage
- **47 tests passing**, 7 MCP tools registered
- README badges and cleaner install flow

## v1.0.0 (Foundation)
- **Persistent SQLite knowledge graph** — zero external dependencies
- **Tree-sitter multi-language parsing** — classes, functions, imports, calls, inheritance
- **Incremental updates** via `git diff` + automatic dependency cascade
- **Impact-radius / blast-radius analysis** — BFS through call/import/inheritance graph
- **6 MCP tools** for full graph interaction
- **3 review-first skills**: build-graph, review-delta, review-pr
- **PostEdit/PostGit hooks** for automatic background updates
- **FastMCP 3.0 compatible** stdio MCP server

## Privacy & Data
- All data stays 100% local
- Graph stored in `.code-review-graph.db` (SQLite)
- No telemetry, no network calls
- Respects `.gitignore` and `.code-review-graphignore`
