# Claude Code Plugin Marketplace

Personal collection of Claude Code plugins. For plugin and marketplace documentation, see:

- [Plugin Reference](https://code.claude.com/docs/en/plugins-reference)
- [Creating Plugins](https://code.claude.com/docs/en/plugins#plugins)

## Installing Plugins

### From this marketplace

Add this repo as a marketplace, then install individual plugins:

```bash
# Add the marketplace (Git URL)
/plugin marketplace add https://github.com/petems/petems-claude-marketplace.git

# List available plugins
/plugin marketplace list

# Install a specific plugin
/plugin install git-commit-push@petems-claude-marketplace

# Install for the whole project (adds to .claude/settings.json)
/plugin install git-commit-push@petems-claude-marketplace --scope project
```

You can also pin to a branch or tag:

```bash
/plugin marketplace add https://github.com/petems/petems-claude-marketplace.git#main
```

### From a local clone

If you've cloned the repo locally, you can add it as a local marketplace or load a single plugin directly:

```bash
# Add local directory as marketplace
/plugin marketplace add ./path/to/petems-claude-marketplace

# Or load a single plugin for one session
claude --plugin-dir ./path/to/petems-claude-marketplace/plugins/git-commit-push
```

### Managing marketplaces

```bash
# List configured marketplaces
/plugin marketplace list

# Update plugin listings
/plugin marketplace update petems-claude-marketplace

# Remove marketplace (also uninstalls its plugins)
/plugin marketplace remove petems-claude-marketplace
```

## Development Quick Start

```bash
# Install dependencies
pnpm install

# Build MCP servers and sync marketplace
pnpm run build:all
```

## Plugin Structure

```
plugins/{name}/
├── .claude-plugin/
│   └── plugin.json          # Required manifest (only this goes in .claude-plugin/)
├── .mcp.json                # Optional: MCP server config
├── commands/                # Optional: slash commands
├── agents/                  # Optional: agent definitions
├── skills/                  # Optional: skills
├── hooks/                   # Optional: event handlers
├── output-styles/           # Optional: custom output styles
└── mcp-server/              # Optional: custom MCP server
    └── dist/                # Bundled output
```

Use kebab-case for all directory and file names. All component directories must be at the plugin root, not nested inside `.claude-plugin/`.

Validate a plugin manifest with: `claude plugin validate`

## Adding a Plugin

1. **Create plugin directory:**

   ```bash
   mkdir -p plugins/my-plugin/.claude-plugin
   ```

2. **Create `plugin.json`:**

   ```json
   {
     "name": "my-plugin",
     "version": "0.1.0",
     "description": "Plugin description",
     "author": {
       "name": "Peter Souter",
       "email": "1064715+petems@users.noreply.github.com"
     },
     "repository": "https://github.com/petems/petems-claude-marketplace",
     "license": "MIT",
     "keywords": ["optional", "search", "terms"]
   }
   ```

   Optional path overrides (defaults to standard directory names):

   ```json
   {
     "commands": ["./custom/commands/special.md"],
     "agents": "./custom/agents/",
     "skills": "./custom/skills/",
     "hooks": "./config/hooks.json",
     "mcpServers": "./mcp-config.json",
     "outputStyles": "./styles/",
     "lspServers": "./.lsp.json"
   }
   ```

3. **Add components** (commands, agents, skills, hooks, MCP servers, output styles, or LSP servers)

4. **Sync marketplace:**
   ```bash
   pnpm run sync
   ```

The sync script auto-discovers plugins and generates `marketplace.json`.

## MCP Servers

### Custom MCP Server

Use `${CLAUDE_PLUGIN_ROOT}` for paths:

```json
{
  "mcpServers": {
    "my-server": {
      "command": "node",
      "args": ["${CLAUDE_PLUGIN_ROOT}/mcp-server/dist/index.js"],
      "env": {
        "API_KEY": "${API_KEY}"
      }
    }
  }
}
```

Build: `pnpm run build` (bundles to `dist/`)

### External MCP Server

```json
{
  "mcpServers": {
    "external": {
      "command": "npx",
      "args": ["-y", "@org/mcp-server"]
    }
  }
}
```

No build needed - runs published package.
