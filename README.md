<div align="center">

# claude-plugins

**Claude Code plugins by [bntvllnt](https://bntvllnt.com) — MCP servers for AI-assisted development.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

</div>

---

## Plugins

| Plugin | Description | Version |
|--------|-------------|---------|
| [codebase-visualizer](plugins/codebase-visualizer/) | 15 MCP tools for TypeScript codebase intelligence | 1.1.0 |

## Install

### Marketplace (recommended)

```bash
# Add the marketplace (once)
/plugin marketplace add bntvllnt/claude-plugins

# Install a plugin
/plugin install codebase-visualizer@bntvllnt-claude-plugins
```

Update to latest:

```bash
/plugin marketplace update bntvllnt-claude-plugins
```

### One-liner (no marketplace)

```bash
claude mcp add -s user -t stdio codebase-visualizer -- npx -y codebase-visualizer@latest . --mcp
```

### Manual (.mcp.json)

Add to your project's `.mcp.json`:

```json
{
  "mcpServers": {
    "codebase-visualizer": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "codebase-visualizer@latest", ".", "--mcp"],
      "env": {}
    }
  }
}
```

Replace `.` with your source directory (e.g., `./src`, `./packages`).

## Available MCP Tools

codebase-visualizer provides 15 tools for code intelligence:

| Tool | Purpose |
|------|---------|
| `codebase_overview` | High-level architecture: modules, entry points, key metrics |
| `file_context` | Full file details: exports, imports, dependents, metrics |
| `get_dependents` | Blast radius: what breaks if you change this file |
| `find_hotspots` | Ranked files by coupling, churn, complexity, etc. |
| `get_module_structure` | Module map with cross-deps and cohesion |
| `analyze_forces` | Tension files, bridges, extraction candidates |
| `find_dead_exports` | Unused exports safe to remove |
| `get_groups` | Top-level directory groups with aggregate metrics |
| `symbol_context` | Callers, callees, importance for any function or class |
| `search` | BM25 keyword search across files and symbols |
| `detect_changes` | Git diff with risk metrics per changed file |
| `impact_analysis` | Symbol-level blast radius with risk labels |
| `rename_symbol` | Find all references for rename planning |
| `get_processes` | Trace execution flows from entry points |
| `get_clusters` | Community-detected clusters of related files |

## Adding a Plugin

```
plugins/
  your-plugin/
    .claude-plugin/
      plugin.json       <- manifest (name, description, version)
    .mcp.json           <- MCP server config
```

See [plugins/codebase-visualizer/](plugins/codebase-visualizer/) for a working example.

## License

[MIT](LICENSE)
