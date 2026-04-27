# Roadmap & Ideas

Future improvements and open questions for both skills. Items are marked by status so it's easy to see what's been addressed and what's still worth doing.

## Recently Shipped (in the v2 rewrite)

These were open in the original v2-notes and are now covered:

- ✅ **Radix composition patterns** — `asChild`, `Slot`, compound component structure, `data-state` attributes for animation — now in `shadcn-component-review/SKILL.md` and `review-checklist.md`
- ✅ **Base UI as an alternative primitive** — both `--base radix` and `--base base` are now covered in the review skill
- ✅ **Keyboard navigation checklist** — per-component expectations (dialog focus trap, menu arrow nav, etc.) in `review-checklist.md`
- ✅ **Official shadcn MCP** — skill now references `npx shadcn@latest mcp init` instead of the old community server
- ✅ **Preset system** — CLI v4 preset codes covered in `theme-styles.md` and `SKILL.md`
- ✅ **Motion rename** — `motion/react` import path documented in `animation-patterns.md`
- ✅ **Registry config** — namespaced `{name}.json` URL template format with authenticated registry support in `registries.md`

---

## Open: Review Skill

### Form Integration Patterns

React Hook Form + Zod integration with shadcn `<Form />` components. The checklist covers what the form's structure should look like, but a dedicated reference with the full RHF+Zod pattern — field arrays, async validation, error handling — would be useful.

**Value:** High. Forms are one of the most common review targets and the pattern is opinionated enough to warrant a reference file.

**Effort:** Medium. Would be a new `references/form-patterns.md`.

### Loading & Empty State Patterns

Decision tree for:
- Skeleton vs spinner (and when neither)
- Inline loading states vs full-page
- Optimistic update patterns
- Empty state — icon + message + action, when to use the `empty` component vs custom

**Value:** Medium. These come up frequently but the current checklist handles the basics.

**Effort:** Low. Could be a section in `review-checklist.md` or a separate reference.

### TanStack Table Integration Depth

The `registries.md` notes that `@shadcn/table` + TanStack Table is often the better path than a pre-built grid, but the review skill doesn't give guidance on reviewing TanStack Table integrations specifically — column definitions, sorting/filtering wiring, virtual scroll.

**Value:** Medium. Only relevant when the user is actually using TanStack Table, but common enough.

**Effort:** Medium. Either a new reference or expansion of `review-checklist.md`.

### Performance Review Patterns

Currently out of scope. Could be valuable to add a "Performance" review step covering:
- `React.memo` in list contexts
- Avoiding unnecessary re-renders in heavily used components
- `useCallback` for handlers passed to primitives
- Code splitting for heavy UI (drawers, modals, rich text editors)

**Value:** Lower — overlaps with general React review, not specifically shadcn.

**Effort:** Medium.

### Testing Patterns

Also currently out of scope. Possible future section:
- `@testing-library` for shadcn/Radix components (querying by role, not data-slot)
- Accessibility testing with `jest-axe`
- Interaction testing for Radix components (open/close flows)

**Value:** Medium-high for teams, lower for solo.

**Effort:** High. Would need actual test examples, not just guidance.

---

## Open: Discovery Skill

### Registry Health Monitoring

The `registries.md` has a "Registry Health" note, but there's no proactive detection for stale/broken registries. Could surface a warning when a registry URL returns a 404 or the registry hasn't published updates in a long time.

**Value:** Low-medium. Harder to implement in a skill context vs tooling.

### Preset Code Registry

A curated list of community preset codes (not just style names, but actual ready-to-apply preset strings) that cover common aesthetics — minimal, brutalist, pastel, high-contrast. Would save users having to use the preset builder themselves.

**Value:** Medium. Goes stale as shadcn updates the theme system.

---

## Open: Both Skills

### Project Skill Override

Let users drop a `shadcn-project.md` into their project root (`.claude/shadcn-project.md` or similar) that defines project-specific conventions — spacing standards, preferred registries, naming patterns. Both skills would read this file first to override/supplement the skill defaults.

**Value:** High for teams with established conventions.

**Effort:** Medium — requires a consistent detection and merge pattern.

### Skills for Specific Frameworks

The skills are framework-agnostic right now. Vite vs Next.js App Router have real differences — RSC boundaries with `"use client"`, server-side form actions, etc. A light framework-awareness layer could surface the right guidance.

**Value:** Medium. Most differences are handled at the import/file level, not the component level.

---

## Contributing

PRs welcome on any of the above. The highest-value open items for external contributors are:

1. Form integration patterns reference (`form-patterns.md`)
2. New registry additions to `registries.md` (include the URL template and a one-line description)
3. Preset code examples (with screenshots or before/after)
