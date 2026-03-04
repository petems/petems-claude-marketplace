# Claude Plugins

@petems personal collection of Claude Code plugins.

## Concepts

- **CLAUDE.md** — Always-loaded project context. Instructions here are included at the start of every conversation. Best for conventions, stack info, and patterns. Can be per-project (`./CLAUDE.md`) or global (`~/.claude/CLAUDE.md`).
- **Skills** — Structured instruction sets that Claude auto-invokes when relevant, or the user triggers manually (e.g., `/my-skill`). Only loaded when needed, so more token-efficient than CLAUDE.md.
- **Slash Commands** — User-invoked shortcuts (e.g., `/review`, `/commit`). Similar to skills but designed primarily for the user to trigger at their own pace. Claude can also invoke them.
- **Plugins** — A packaging format that bundles skills, slash commands, agents, hooks, and MCP servers together. A plugin can be as simple as a single skill.
- **Marketplace** — A git repository containing one or more plugins. Users add a marketplace, then install individual plugins from it.

## Using this marketplace

Add this marketplace to Claude Code:

```bash
/plugin marketplace add petems/petems-claude-marketplace
```

Then install plugins:

```bash
/plugin install content@petems
```

## Plugins

- [content](plugins/content/README.md) - Tools for bootstrapping content creation
- [git-commit-push](plugins/git-commit-push/skills/git-commit-push/SKILL.md) - Git add, commit with Conventional Commits, and push in one step

## Development

This is a pnpm workspace with TypeScript project references.

```bash
# Install dependencies
pnpm install

# Type check everything
pnpm run typecheck

# Build all MCP servers
pnpm run build

# Build and sync marketplace metadata
pnpm run build:all
```

### Adding a new plugin

1. Create `plugins/your-plugin/.claude-plugin/plugin.json` with metadata
2. Add components: agents, commands, skills, or MCP servers
3. If adding an MCP server, update `pnpm-workspace.yaml` and root `tsconfig.json`
4. Run `pnpm run sync` to auto-discover and add to marketplace

The sync script scans `plugins/` and automatically discovers all plugins with valid `plugin.json` files. Add a plugin directory and it shows up. Remove one and it disappears.

## License

MIT
