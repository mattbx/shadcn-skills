# shadcn Registry Catalog

Comprehensive catalog of shadcn-compatible registries organized by specialty.

## Core Registries (Recommended First)

These registries are well-maintained and cover most use cases.

### @shadcn (Official)
- **Items:** 440+
- **Focus:** Core UI primitives
- **Quality:** Reference implementation
- **URL:** https://ui.shadcn.com
- **Best for:** Base components (Button, Input, Card, Dialog, etc.)

### @blocks (Official)
- **Items:** 100+
- **Focus:** Pre-built page sections
- **Quality:** Production-ready
- **URL:** https://ui.shadcn.com/blocks
- **Best for:** Dashboards, authentication pages, settings layouts, sidebars

### @reui
- **Items:** 700+
- **Focus:** Advanced components and full apps
- **Quality:** Production-ready
- **URL:** https://reui.dev
- **Best for:** Data grids, complex forms, full page templates, admin panels

### @animate-ui
- **Items:** 200+
- **Focus:** Animated components with Motion
- **Quality:** High polish
- **URL:** https://animate-ui.com
- **Best for:** Animated backgrounds, transitions, micro-interactions, polished UI

### @diceui
- **Items:** 100+
- **Focus:** Accessible components
- **Quality:** WCAG compliant
- **URL:** https://diceui.com
- **Best for:** Accessibility-first projects, enterprise apps

---

## Specialty Registries

### AI & Chat Components

| Registry | Focus | URL |
|----------|-------|-----|
| **AI Elements** | AI chat, messages, conversations | https://aielements.dev |
| **Manifest UI** | ChatGPT-style apps | https://manifest-ui.com |
| **assistant-ui** | AI assistant interfaces | https://assistant-ui.com |

**Search terms:** `chat`, `message`, `conversation`, `ai`, `assistant`, `streaming`

### Animation & Motion

| Registry | Focus | URL |
|----------|-------|-----|
| **Magic UI** | 150+ animated components | https://magicui.design |
| **Cult UI** | Design engineer animations | https://cult-ui.com |
| **Shadix UI** | Production-ready animations | https://shadix-ui.com |
| **Motion Primitives** | Motion building blocks | https://motion-primitives.com |

**Search terms:** `animate`, `motion`, `transition`, `hover`, `entrance`

### Voice & Audio

| Registry | Focus | URL |
|----------|-------|-----|
| **ElevenLabs UI** | Voice agents, audio players, waveforms | https://elevenlabs.io |

**Search terms:** `audio`, `voice`, `waveform`, `player`, `orb`

### Marketing & Landing Pages

| Registry | Focus | URL |
|----------|-------|-----|
| **Tailark** | Marketing blocks | https://tailark.com |
| **Eldora UI** | Landing page components | https://eldoraui.com |
| **HextaUI** | Extended blocks | https://hextaui.com |

**Search terms:** `hero`, `cta`, `pricing`, `features`, `testimonial`, `landing`

### Data & Tables

| Registry | Focus | URL |
|----------|-------|-----|
| **@reui** | Advanced data grids | https://reui.dev |
| **TanCN** | TanStack Table integration | - |

**Search terms:** `table`, `data-grid`, `column`, `sort`, `filter`, `pagination`

### Forms & Validation

| Registry | Focus | URL |
|----------|-------|-----|
| **Shadcn Form Builder** | Form generation | https://shadcn-form-builder.vercel.app |
| **FormCN** | Form components | - |

**Search terms:** `form`, `input`, `validation`, `field`, `submit`

### Icons (Animated)

| Registry | Focus | URL |
|----------|-------|-----|
| **pqoqubbw/icons** | Animated Lucide icons | https://icons.pqoqubbw.dev |
| **heroicons-animated** | 316 animated heroicons | - |

**Search terms:** `icon`, `animated-icon`

### Style Variants

| Registry | Style | URL |
|----------|-------|-----|
| **8bitcn** | Retro 8-bit pixel style | https://8bitcn.com |
| **RetroUI** | Neobrutalism | https://retroui.dev |
| **Neobrutalism UI** | Bold, brutalist | - |
| **shadcn-glass-ui** | Glassmorphism (55 components) | - |

**Search terms:** `retro`, `brutalist`, `glass`, `pixel`, `8bit`

### Accessibility-First

| Registry | Focus | URL |
|----------|-------|-----|
| **JollyUI** | React Aria based | https://jollyui.dev |
| **Intent UI** | Accessible, customizable | https://intent-ui.com |
| **Kibo UI** | Composable, accessible | https://kibo-ui.com |

**Search terms:** `accessible`, `aria`, `a11y`

---

## Registry Search Strategy

### By Component Type

| Looking for... | Search these registries first |
|----------------|-------------------------------|
| Basic UI | @shadcn |
| Page layouts | @blocks, @reui |
| Data tables | @reui, @shadcn |
| Animations | @animate-ui, Magic UI, Cult UI |
| AI/Chat | AI Elements, Manifest UI, assistant-ui |
| Forms | @shadcn, Shadcn Form Builder |
| Auth pages | @blocks |
| Dashboards | @blocks, @reui |
| Marketing | Tailark, Eldora UI |
| Audio/Voice | ElevenLabs UI |

### By Project Type

| Building... | Recommended registries |
|-------------|------------------------|
| SaaS dashboard | @blocks, @reui, @shadcn |
| Marketing site | Tailark, Eldora UI, Magic UI |
| AI application | AI Elements, assistant-ui, @animate-ui |
| Admin panel | @reui, @blocks, @diceui |
| E-commerce | @shadcn, @reui, @blocks |
| Portfolio | Magic UI, @animate-ui, Cult UI |
| Enterprise app | @diceui, JollyUI, @shadcn |

---

## Adding Registries to Your Project

### Via components.json

```json
{
  "registries": {
    "animate-ui": "https://animate-ui.com/r",
    "magic-ui": "https://magicui.design/r",
    "reui": "https://reui.dev/r"
  }
}
```

### Via CLI

```bash
# View available items in a registry
npx shadcn@latest view @registry-name

# Add from a registry
npx shadcn@latest add @registry-name/component-name
```

---

## Quick Reference: Popular Components

### Most Searched

| Need | Component | Registry |
|------|-----------|----------|
| Animated tabs | components-animate-tabs | @animate-ui |
| Data table | data-grid-table | @reui |
| File upload | file-upload | @reui |
| Date picker | calendar, date-picker | @shadcn |
| Command palette | command | @shadcn |
| Sidebar | sidebar | @shadcn, @blocks |
| Toast notifications | sonner, toast | @shadcn |
| Charts | chart | @shadcn |
| Carousel | carousel | @shadcn, @animate-ui |
| Modal/Dialog | dialog, alert-dialog | @shadcn, @animate-ui |

### Hidden Gems

| Component | What it does | Registry |
|-----------|--------------|----------|
| preview-link-card | Link preview on hover | @animate-ui |
| components-backgrounds-* | Animated backgrounds | @animate-ui |
| data-grid-table-dnd | Drag-drop table rows | @reui |
| components-animate-cursor | Custom cursor effects | @animate-ui |
| gravity-stars | Animated star background | @animate-ui |

---

## Browsing Registries Manually

If shadcn MCP is not available, browse these discovery sites:

- **[registry.directory](https://registry.directory)** - Aggregated registry browser
- **[shadcnregistry.com](https://shadcnregistry.com)** - Searchable component index
- **[shadcn.io/awesome](https://www.shadcn.io/awesome)** - Curated resource list
- **[ui.shadcn.com/blocks](https://ui.shadcn.com/blocks)** - Official blocks

---

*Last updated: February 2025*
