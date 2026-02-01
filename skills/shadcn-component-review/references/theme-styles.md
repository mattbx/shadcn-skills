# shadcn Theme Styles Reference

Reference guide for the 5 official shadcn visual styles and their design characteristics.

## The 5 Visual Styles

| Style | Spacing | Shape | Best For |
|-------|---------|-------|----------|
| **Vega** | Standard | Classic | Default shadcn look, most projects |
| **Nova** | Compact | Standard | Dense UIs, data-heavy apps |
| **Maia** | Generous | Soft/Rounded | Consumer apps, friendly interfaces |
| **Lyra** | Standard | Boxy/Sharp | Technical tools, pairs with mono fonts |
| **Mira** | Dense | Compact | Admin dashboards, power user interfaces |

## Vega (Classic)

The default shadcn/ui aesthetic. Balanced spacing and standard border radius.

**Characteristics:**
- Standard spacing: `gap-4` sections, `gap-2` internal
- Medium border radius: `rounded-md` to `rounded-lg`
- Clean, professional appearance

**Spacing patterns:**
```tsx
<Card className="gap-4">
  <CardHeader className="gap-2">
  <CardContent>
</Card>

<Button className="h-9 px-4">  // Standard sizing
```

## Nova (Compact)

Reduced padding and margins for compact layouts without feeling cramped.

**Characteristics:**
- Tighter spacing: `gap-2` to `gap-3` sections
- Smaller padding on components
- Efficient use of screen real estate

**Spacing patterns:**
```tsx
<Card className="gap-2 p-4">  // Reduced padding
  <CardHeader className="gap-1.5">
  <CardContent>
</Card>

<Button size="sm" className="h-8 px-3">  // Compact buttons
```

**Best for:** Data tables, sidebars, toolbars, mobile-first designs

## Maia (Soft & Rounded)

Soft, friendly aesthetic with generous spacing and pill-shaped elements.

**Characteristics:**
- Generous spacing: `gap-6` sections, `gap-2` to `gap-4` internal
- Large border radius: `rounded-xl` to `rounded-full` for buttons/inputs
- Comfortable, approachable feel

**Spacing patterns:**
```tsx
<Card className="gap-6 p-6">  // Generous padding
  <CardHeader className="gap-2">
  <CardContent>
</Card>

<Button className="h-10 px-6 rounded-full">  // Pill-shaped
<Input className="rounded-full">
```

**Responsive spacing:**
```tsx
// Maia uses larger responsive jumps
<div className="gap-4 md:gap-6">  // 16px → 24px
<div className="gap-6 md:gap-8">  // 24px → 32px
```

**Best for:** Consumer apps, onboarding flows, marketing sites

## Lyra (Boxy & Sharp)

Sharp, technical aesthetic with minimal border radius.

**Characteristics:**
- Standard spacing (similar to Vega)
- Minimal border radius: `rounded-sm` or `rounded-none`
- Technical, precise appearance
- Pairs well with monospace fonts

**Spacing patterns:**
```tsx
<Card className="gap-4 rounded-sm">
  <CardHeader className="gap-2">
  <CardContent>
</Card>

<Button className="rounded-sm">
<Input className="rounded-sm font-mono">
```

**Best for:** Developer tools, code editors, technical dashboards

## Mira (Dense)

Maximum information density for power users.

**Characteristics:**
- Dense spacing: `gap-1` to `gap-2` sections
- Compact padding throughout
- Small text sizes where appropriate
- Every pixel counts

**Spacing patterns:**
```tsx
<Card className="gap-1.5 p-3">  // Minimal padding
  <CardHeader className="gap-1">
  <CardContent className="text-sm">
</Card>

<Button size="sm" className="h-7 px-2 text-xs">  // Extra compact
```

**Best for:** Admin panels, trading interfaces, data-heavy dashboards

## Spacing Scale by Theme

| Context | Vega | Nova | Maia | Lyra | Mira |
|---------|------|------|------|------|------|
| Section gap | `gap-4` | `gap-2` | `gap-6` | `gap-4` | `gap-1.5` |
| Internal gap | `gap-2` | `gap-1.5` | `gap-2` | `gap-2` | `gap-1` |
| Card padding | `p-6` | `p-4` | `p-6` | `p-6` | `p-3` |
| Button height | `h-9` | `h-8` | `h-10` | `h-9` | `h-7` |

## Border Radius by Theme

| Element | Vega | Nova | Maia | Lyra | Mira |
|---------|------|------|------|------|------|
| Button | `rounded-md` | `rounded-md` | `rounded-full` | `rounded-sm` | `rounded-sm` |
| Input | `rounded-md` | `rounded-md` | `rounded-full` | `rounded-sm` | `rounded-sm` |
| Card | `rounded-lg` | `rounded-md` | `rounded-xl` | `rounded-sm` | `rounded-md` |
| Badge | `rounded-md` | `rounded-sm` | `rounded-full` | `rounded-sm` | `rounded-sm` |

## Core Spacing Principles (All Themes)

### 1. Use `gap-*` for Flex/Grid Containers

```tsx
// ✅ Correct: Flex container with gap
<div className="flex flex-col gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
</div>

// ❌ Avoid: Using space-y-* or margins
<div className="flex flex-col space-y-4">
<div className="flex flex-col">
  <div className="mb-4">
```

### 2. Follow Tailwind Spacing Scale

Use standard Tailwind values (multiples of 4px):

| Class | Pixels | Use Case |
|-------|--------|----------|
| `gap-1` | 4px | Dense internal spacing |
| `gap-1.5` | 6px | Compact internal spacing |
| `gap-2` | 8px | Standard internal spacing |
| `gap-4` | 16px | Section spacing (compact themes) |
| `gap-6` | 24px | Section spacing (generous themes) |
| `gap-8` | 32px | Large section spacing |

Avoid non-standard values: `gap-3` (12px), `gap-5` (20px), `gap-7` (28px)

### 3. Responsive Spacing Pattern

```tsx
// Standard pattern: Smaller on mobile, larger on desktop
<div className="gap-2 md:gap-4">  // Compact
<div className="gap-4 md:gap-6">  // Standard
<div className="gap-6 md:gap-8">  // Generous
```

## Common Spacing Mistakes

### ❌ Using `space-y-*` in Flex Containers

```tsx
// Wrong
<div className="flex flex-col space-y-4">

// Correct
<div className="flex flex-col gap-4">
```

### ❌ Hardcoded Margins Instead of Gap

```tsx
// Wrong
<div className="flex flex-col">
  <div className="mb-4">Item 1</div>
  <div className="mb-4">Item 2</div>
</div>

// Correct
<div className="flex flex-col gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

### ❌ Mixing Theme Densities

```tsx
// Wrong: Maia spacing with Lyra radius
<Card className="gap-6 p-6 rounded-sm">

// Correct: Consistent theme application
<Card className="gap-6 p-6 rounded-xl">  // Maia
<Card className="gap-4 p-6 rounded-sm">  // Lyra
```

## Detecting Your Theme

Check your `components.json` or the CSS in `src/index.css`:

```json
// components.json
{
  "style": "maia"  // or "vega", "nova", "lyra", "mira"
}
```

Or look at the CSS variables in your theme:
- Large `--radius` values (1rem+) → Maia
- Small `--radius` values (0.25rem) → Lyra/Mira
- Standard `--radius` (0.5rem) → Vega/Nova

## Reference Links

- **Theme Picker**: https://ui.shadcn.com/themes
- **Theme Creator**: https://ui.shadcn.com/create
- **Tailwind Spacing**: https://tailwindcss.com/docs/theme#spacing
