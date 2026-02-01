# shadcn-skills

Skills for building better [shadcn/ui](https://ui.shadcn.com) applications with AI coding agents.

## Skills Included

### 1. shadcn-component-discovery

**Stop reinventing the wheel.** Search 1,500+ existing shadcn components before building custom.

- **Proactively searches** before building any UI component
- **Presents top matches** with descriptions and install commands
- **Covers 30+ registries**: @shadcn, @blocks, @reui, @animate-ui, @diceui, Magic UI, Cult UI, and more
- **Works with or without** the shadcn MCP (MCP recommended for full experience)

```
You: "Add a data table to show user accounts"

Agent: Before building a custom data table, I found existing options:
       1. @reui/data-grid-table - Full-featured grid with sorting, filtering
       2. @blocks/table-05 - Pre-styled data table block
       → Install one of these, or build custom?
```

### 2. shadcn-component-review

**Build like the shadcn team.** Review components against shadcn design patterns and theme styles.

- **Supports all 5 themes**: Vega, Nova, Maia, Lyra, Mira
- **Checks spacing patterns**: gap-* vs space-y-*, theme-appropriate values
- **Validates structure**: data-slot attributes, composition patterns
- **Enforces design tokens**: semantic colors only, no hardcoded values
- **Includes**: CVA patterns, cn() utility, animation best practices

```
You: "Review this component against shadcn patterns"

Agent: ## Component Review

       ✅ Structure: Proper data-slot attributes
       ⚠️ Spacing: Using space-y-4 instead of gap-4
       ❌ Colors: Hardcoded text-neutral-500 (use text-muted-foreground)

       Fixes: [provides specific corrections]
```

## Installation

### npx skills (Recommended)

```bash
# Install both skills to any supported agent
npx skills add mattbx/shadcn-skills

# Or list available skills first
npx skills add mattbx/shadcn-skills --list

# Install to specific agents
npx skills add mattbx/shadcn-skills -a claude-code -a cursor
```

### Claude Code Plugin

```bash
# Add the marketplace
/plugin marketplace add mattbx/shadcn-skills

# Install both skills
/plugin install shadcn-component-discovery
/plugin install shadcn-component-review
```

### Manual Installation

Copy the skill folders from `skills/` to:
- `~/.claude/skills/` (personal - all projects)
- `.claude/skills/` (project-specific)

### Supported Tools

These skills follow the [Agent Skills](https://agentskills.io) open standard and work with:
- Claude Code
- Cursor
- OpenAI Codex CLI
- Windsurf
- Gemini CLI
- GitHub Copilot
- And other compatible tools

## Workflow: Discovery → Build → Review

These skills work great together:

```
1. DISCOVER: "Add an animated accordion"
   → Agent searches registries, finds @animate-ui/components-base-accordion
   → User chooses to install or build custom

2. BUILD: User customizes or builds the component

3. REVIEW: "Review this component"
   → Agent checks spacing, structure, tokens, theme alignment
   → Provides specific fixes if needed
```

## Best Experience: Configure shadcn MCP

The discovery skill works without MCP (provides registry links), but for **instant search with code examples**:

```bash
# Add shadcn MCP to your AI coding tool
# See: https://github.com/nicholasoxford/shadcn-mcp
```

## Registries Covered (Discovery)

### Core Registries

| Registry | Items | Focus |
|----------|-------|-------|
| @shadcn | 440+ | Core UI primitives |
| @blocks | 100+ | Pre-built page sections |
| @reui | 700+ | Advanced components & apps |
| @animate-ui | 200+ | Animated components |
| @diceui | 100+ | Accessible components |

### Community Registries (30+)

Magic UI, Cult UI, AI Elements, ElevenLabs UI, Tailark, JollyUI, Intent UI, Kibo UI, and many more.

See `skills/shadcn-component-discovery/references/registries.md` for the full catalog.

## Theme Styles Covered (Review)

| Theme | Spacing | Shape | Best For |
|-------|---------|-------|----------|
| **Vega** | Standard | Classic | Default shadcn look |
| **Nova** | Compact | Standard | Dense UIs, data-heavy apps |
| **Maia** | Generous | Soft/Rounded | Consumer apps, friendly interfaces |
| **Lyra** | Standard | Boxy/Sharp | Technical tools, mono fonts |
| **Mira** | Dense | Compact | Admin dashboards, power users |

See `skills/shadcn-component-review/references/theme-styles.md` for detailed patterns.

## Contributing

PRs welcome! Ideas:
- UX suggestions
- New registry additions
- Additional theme patterns
- Improved search mappings
- Better response templates

## License

MIT

---

Built with the [Agent Skills](https://agentskills.io) open standard.
