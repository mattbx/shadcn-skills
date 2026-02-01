# Component Review Checklist

Detailed checklist for reviewing components against shadcn design patterns and theme conventions.

## Quick Audit

Run through this checklist for every component:

- [ ] Spacing uses `gap-*` in flex containers
- [ ] Spacing follows Tailwind scale (2, 4, 6, 8)
- [ ] Responsive spacing uses `gap-X md:gap-Y` pattern
- [ ] `data-slot` attributes present on main elements
- [ ] No hardcoded colors (check for `neutral-*`, `gray-*`)
- [ ] Semantic design tokens used (`text-foreground`, `bg-muted`, etc.)
- [ ] Component is composable and reusable
- [ ] Mobile-first responsive design
- [ ] Proper component structure (Header, Content, Footer pattern)

## Detailed Review Sections

### 1. Spacing Audit

#### Flex/Grid Container Spacing

- [ ] Uses `gap-*` instead of `space-y-*` or margins
- [ ] Spacing values follow Tailwind scale (multiples of 4px)
- [ ] No hardcoded spacing values (3px, 5px, 7px, etc.)
- [ ] Responsive spacing uses `gap-X md:gap-Y` pattern

**Check for:**
```tsx
// ✅ Good
<div className="flex flex-col gap-4 md:gap-6">

// ❌ Bad
<div className="flex flex-col space-y-4">
<div className="flex flex-col gap-3">  // Non-standard value
```

#### Internal Component Spacing

- [ ] Header sections use `gap-2` (8px) for heading/description
- [ ] Button internal spacing uses `gap-1` or `gap-1.5` (4-6px)
- [ ] Card sections use `gap-6` default, `gap-4` small, `gap-2` compact
- [ ] Consistent spacing within similar components

**Check for:**
```tsx
// ✅ Good
<div className="flex flex-col gap-2">
  <h1>Heading</h1>
  <p>Description</p>
</div>

// ❌ Bad
<div className="flex flex-col">
  <h1>Heading</h1>
  <p className="mt-1">Description</p>  // Using margin instead of gap
</div>
```

#### Container Padding

- [ ] Padding uses standard Tailwind values
- [ ] Responsive padding where appropriate (`px-4 md:px-6`)
- [ ] Consistent padding across similar components

### 2. Component Structure

#### data-slot Attributes

- [ ] Main component wrapper has `data-slot="component-name"`
- [ ] Sub-components have appropriate `data-slot` attributes
- [ ] `data-slot` values are semantic and descriptive

**Check for:**
```tsx
// ✅ Good
<div data-slot="page-content">
  <div data-slot="page-content-header">
  <div data-slot="page-content-block">

// ❌ Bad
<div>  // Missing data-slot
  <div>  // Missing data-slot
```

#### Component Composition

- [ ] Uses composition over modification
- [ ] Doesn't modify `src/ui/*` components directly
- [ ] Sub-components follow naming pattern (`ComponentName.Header`, etc.)
- [ ] Clear separation of concerns

**Check for:**
```tsx
// ✅ Good: Composing components
<Card>
  <CardHeader>
    <CardTitle>Title</CardTitle>
  </CardHeader>
</Card>

// ❌ Bad: Modifying base component
// Editing src/ui/card.tsx directly
```

#### Layout Structure

- [ ] Uses flex or grid appropriately
- [ ] `min-w-0` on flex children to prevent overflow
- [ ] Proper flex direction (`flex-col` vs `flex-row`)
- [ ] Responsive layout changes use breakpoints

### 3. Design Tokens

#### Color Tokens

- [ ] No hardcoded colors (`neutral-*`, `gray-*`, `slate-*`)
- [ ] Uses semantic tokens (`text-foreground`, `text-muted-foreground`)
- [ ] Background tokens (`bg-card`, `bg-muted`, `bg-accent`)
- [ ] Border tokens (`border-border`, `border-border-strong`)

**Check with:**
```bash
grep -r "neutral-\|gray-\|slate-" [component-file]
```

**Check for:**
```tsx
// ✅ Good
<p className="text-muted-foreground">Description</p>
<div className="bg-muted hover:bg-accent">

// ❌ Bad
<p className="text-neutral-500">Description</p>
<div className="bg-gray-100 hover:bg-gray-200">
```

#### Typography Tokens

- [ ] Uses semantic text colors (`text-foreground`, `text-muted-foreground`)
- [ ] Proper font weights (`font-medium`, `font-semibold`)
- [ ] Responsive text sizes (`text-xl md:text-2xl`)

### 4. Composability

#### Reusability

- [ ] Component can be used in multiple contexts
- [ ] Not tightly coupled to specific use case
- [ ] Clear prop interface
- [ ] Default values provided where appropriate

#### Customization

- [ ] Variants supported via props (`variant`, `size`)
- [ ] Customizable via `className` prop
- [ ] Slot-based composition (children, content blocks)
- [ ] Doesn't require modification for different use cases

**Check for:**
```tsx
// ✅ Good: Flexible and composable
<PageContent
  heading="Title"
  description="Description"
  contentBlock={<Tabs />}
  contentBlockSpacing="md"
>
  <DataTable />
</PageContent>

// ❌ Bad: Too specific, not reusable
<WorkflowPageContent />  // Only works for workflows
```

#### Sub-Components

- [ ] Sub-components exported for advanced usage
- [ ] Sub-components follow naming pattern
- [ ] Sub-components are properly typed

### 5. Responsive Design

#### Mobile-First Approach

- [ ] Designed for mobile (< 768px) first
- [ ] Progressive enhancement for larger screens
- [ ] Uses `md:` breakpoint appropriately
- [ ] Uses `lg:` breakpoint when needed

#### Breakpoints

- [ ] Breakpoints used consistently
- [ ] Responsive spacing (`gap-4 md:gap-6`)
- [ ] Responsive typography (`text-xl md:text-2xl`)
- [ ] Responsive layout changes (`flex-col md:flex-row`)

#### Touch Targets

- [ ] Interactive elements minimum 44px (11 Tailwind units)
- [ ] Adequate spacing between touch targets
- [ ] Mobile-friendly interactions

#### Content Overflow

- [ ] Uses `min-w-0` on flex children
- [ ] Proper text truncation where needed
- [ ] Horizontal scroll handled appropriately
- [ ] Content doesn't overflow containers

### 6. Accessibility

#### Semantic HTML

- [ ] Proper HTML elements used (`h1`, `p`, `button`, etc.)
- [ ] ARIA attributes where needed
- [ ] Proper heading hierarchy

#### Focus States

- [ ] Visible focus indicators
- [ ] Keyboard navigation works
- [ ] Focus management in modals/dialogs

#### Screen Reader Support

- [ ] Proper labels and descriptions
- [ ] ARIA labels where needed
- [ ] Hidden decorative elements properly marked

### 7. Performance

#### Rendering

- [ ] No unnecessary re-renders
- [ ] Proper use of `React.memo` where appropriate
- [ ] Efficient conditional rendering

#### Bundle Size

- [ ] No unnecessary dependencies
- [ ] Tree-shakeable imports
- [ ] Minimal runtime overhead

## Review Workflow

### Step 1: Visual Inspection

1. Open component in browser
2. Test at breakpoints (375px, 768px, 1280px)
3. Check spacing visually
4. Verify responsive behavior

### Step 2: Code Review

1. Check spacing patterns (`gap-*` usage)
2. Verify `data-slot` attributes
3. Check for hardcoded colors
4. Review component structure
5. Verify composability

### Step 3: Comparison

1. Compare with similar shadcn components
2. Check against Maia theme examples
3. Verify alignment with project patterns
4. Review against checklist above

### Step 4: Documentation

1. Document any deviations from patterns
2. Note any customizations needed
3. Update component documentation
4. Add examples if needed

## Common Issues and Fixes

### Issue: Using `space-y-*` in Flex Container

**Fix:**
```tsx
// Before
<div className="flex flex-col space-y-4">

// After
<div className="flex flex-col gap-4">
```

### Issue: Hardcoded Colors

**Fix:**
```tsx
// Before
<p className="text-neutral-500">Description</p>

// After
<p className="text-muted-foreground">Description</p>
```

### Issue: Missing `data-slot` Attributes

**Fix:**
```tsx
// Before
<div className="flex flex-col gap-4">
  <div>Header</div>
</div>

// After
<div data-slot="component-name" className="flex flex-col gap-4">
  <div data-slot="component-header">Header</div>
</div>
```

### Issue: Inconsistent Spacing

**Fix:**
```tsx
// Before
<div className="gap-3">  // Non-standard
<div className="gap-5">  // Non-standard

// After
<div className="gap-2">  // Standard (8px)
<div className="gap-4">  // Standard (16px)
```

### Issue: Missing Responsive Spacing

**Fix:**
```tsx
// Before
<div className="gap-6">

// After
<div className="gap-4 md:gap-6">
```

## Review Checklist Template

Copy this template for each component review:

```markdown
## Component: [ComponentName]

### Spacing
- [ ] Uses `gap-*` in flex containers
- [ ] Follows Tailwind spacing scale
- [ ] Responsive spacing implemented
- [ ] Consistent spacing values

### Structure
- [ ] `data-slot` attributes present
- [ ] Proper component composition
- [ ] Sub-components follow pattern

### Design Tokens
- [ ] No hardcoded colors
- [ ] Semantic tokens used
- [ ] Proper typography tokens

### Composability
- [ ] Reusable across contexts
- [ ] Prop-based customization
- [ ] Slot-based composition

### Responsive
- [ ] Mobile-first approach
- [ ] Proper breakpoints
- [ ] Touch targets adequate
- [ ] Content overflow handled

### Issues Found
1. [Issue description]
2. [Issue description]

### Fixes Applied
1. [Fix description]
2. [Fix description]
```

## Additional Resources

- **Main Skill**: See [../SKILL.md](../SKILL.md) for overview
- **Theme Styles**: See [theme-styles.md](theme-styles.md) for spacing patterns by theme
- **Animation Patterns**: See [animation-patterns.md](animation-patterns.md) for motion guidelines
- **shadcn Theming Docs**: https://ui.shadcn.com/docs/theming
