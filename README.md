# shadcn-skills

Two agent skills for working with [shadcn/ui](https://ui.shadcn.com): one for discovering existing components across the ecosystem before building, one for reviewing custom components against shadcn design patterns.

Both follow the [Agent Skills](https://agentskills.io) open standard and work with Claude Code, Cursor, Windsurf, OpenAI Codex CLI, Gemini CLI, GitHub Copilot, and other compatible tools.

---

## Skills

### shadcn-component-discovery

Searches the shadcn component ecosystem before building any custom UI. Activates proactively before Claude writes a table, form, modal, animation, or other common UI pattern — and explicitly when prompted to search registries.

**What it covers:**
- Live search via the official shadcn MCP (`npx shadcn@latest mcp init`) or CLI fallback (`npx shadcn@latest search`)
- Awareness of 30+ community registries beyond the user's configured `components.json`, organized by specialty (animations, AI interfaces, data grids, accessibility-first, etc.)
- Response format: top 2–3 matches with registry-qualified name, description, and ready-to-run install command
- Graceful handling when no match exists — recommends closest adjacencies and offers to build custom

**How it complements the official shadcn skill:** The official shadcn skill (shipped with CLI v4) searches registries already declared in `components.json`. This skill's scope is upstream — surfacing registries the user hasn't configured yet, and providing ecosystem-wide awareness when choosing which registries to add.

**Example:**

```text
User: "Add a data table to show user accounts"

Agent: Before building custom, I found existing options:

       1. @reui/data-grid-table — Full-featured grid with sorting, filtering, pagination
       2. @shadcn/table — Unstyled primitives (pair with TanStack Table for sorting)

       @reui/data-grid-table looks like the fit — install it?
```

---

### shadcn-component-review

Reviews custom components against shadcn design patterns. Activates proactively after writing or modifying a component, and explicitly when asked to review or audit.

**What it checks:**
- **Structure**: `data-slot` attributes, composition vs forking, Radix vs Base UI primitive patterns
- **Spacing**: `gap-*` in flex/grid (not `space-y-*`), Tailwind scale values, `size-*` for equal dimensions
- **Design tokens**: semantic colors only (`text-muted-foreground`, `bg-card`, etc.) — flags any Tailwind color scale values
- **Composability**: `className` via `cn()`, CVA variant patterns, prop typing
- **Responsive/a11y**: mobile-first, touch targets, `min-w-0`, focus-visible states, motion preferences

**How it complements the official shadcn skill:** The official skill enforces rules at generation time. This skill is for post-hoc audit — reviewing components that already exist, especially ones built before the project standardized on a style, or written by contributors without shadcn context.

**Visual styles supported:** Vega, Nova, Maia, Lyra, Mira — per-style spacing, radius, and density expectations are applied based on the project's `components.json` or `npx shadcn@latest info --json`.

**Example:**

```text
User: "Review this component"

Agent: ## Review: <PageHeader />

       Structure  ✅ data-slot present, composition clean
       Spacing    ⚠️ Uses space-y-4 in flex container (line 8) — swap to gap-4
       Tokens     ❌ text-neutral-500 on line 12 — use text-muted-foreground
       a11y       ⚠️ Missing min-w-0 on flex child (line 18)

       Want me to apply these fixes?
```

---

## Installation

### npx skills (recommended)

```bash
npx skills add mattbx/shadcn-skills
```

Install individual skills:

```bash
npx skills add mattbx/shadcn-skills --list   # preview available
npx skills add mattbx/shadcn-skills -s shadcn-component-discovery
npx skills add mattbx/shadcn-skills -s shadcn-component-review
```

Target specific agents:

```bash
npx skills add mattbx/shadcn-skills -a claude-code -a cursor
```

### Manual installation

Copy the skill folders from `skills/` to:
- `~/.claude/skills/` — applies to all projects for the current user
- `.claude/skills/` — project-scoped

The same paths work for Cursor, Windsurf, and other compatible tools. Check your agent's documentation for skill directory locations.

---

## Recommended Setup

Both skills work without any additional configuration, but work best with the official shadcn MCP:

```bash
# Adds the official shadcn MCP to your agent
npx shadcn@latest mcp init
```

The MCP enables real-time search of your configured registries with code examples and correct install commands. Without it, the skills fall back to CLI commands and manual registry links.

---

## File Structure

```
skills/
├── shadcn-component-discovery/
│   ├── SKILL.md                    # Main skill — workflow, search paths, response format
│   └── references/
│       └── registries.md           # Registry catalog with configuration examples
│
└── shadcn-component-review/
    ├── SKILL.md                    # Main skill — review workflow, patterns, output format
    └── references/
        ├── theme-styles.md         # Per-style spacing, density, radius tables
        ├── review-checklist.md     # Expanded audit checklist by category
        └── animation-patterns.md  # CSS and Motion animation conventions

docs/
└── ROADMAP.md                      # Open ideas and contribution opportunities
```

---

## Contributing

PRs welcome. The highest-value open areas are in `docs/ROADMAP.md`. For registry additions, include the registry name, URL template (`https://example.com/r/{name}.json`), and a one-line description of what it covers.

## License

MIT
