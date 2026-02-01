# V2 Enhancement Ideas

Future improvements for the shadcn-component-review skill.

## Medium Priority

### Radix Primitive Composition Patterns

Detailed guidance on composing with Radix primitives:

- Compound component pattern (`Root`, `Trigger`, `Content`)
- `asChild` prop for custom elements
- `data-state` attributes for styling/animation
- Portal handling for overlays (z-index, scroll lock)
- Proper `forwardRef` patterns for form integration
- Keyboard navigation expectations per component type

### Form Integration Patterns

React Hook Form + Zod validation patterns:

```tsx
// Pattern to document:
<Form {...form}>
  <FormField
    control={form.control}
    name="email"
    render={({ field }) => (
      <FormItem>
        <FormLabel>Email</FormLabel>
        <FormControl>
          <Input {...field} />
        </FormControl>
        <FormMessage />
      </FormItem>
    )}
  />
</Form>
```

- Zod schema patterns
- Error message handling
- Async validation
- Field arrays

## Lower Priority

### Keyboard Navigation Checklist

Detailed checklist per component type:

- **Buttons**: Enter/Space activation
- **Menus**: Arrow navigation, Escape to close
- **Dialogs**: Focus trap, Escape to close
- **Tabs**: Arrow navigation, Home/End
- **Combobox**: Arrow navigation, Enter to select

### Empty State Patterns

Consistent empty state design:

- When to use `empty` component vs custom
- Icon + message + action pattern
- Illustration guidelines
- Copy tone recommendations

### Loading State Patterns

Decision tree for loading indicators:

- Skeleton vs spinner decision matrix
- Inline loading states
- Full-page loading
- Optimistic updates
- Error recovery patterns

### TanStack Table Integration

For data-heavy components:

- When native shadcn table vs TanStack Table
- Column definition patterns
- Sorting/filtering integration
- Virtual scrolling for large datasets
- Selection state management

## Research Needed

### Performance Patterns

- `React.memo` guidelines for shadcn components
- `useCallback` for event handlers in lists
- Virtual scrolling patterns
- Code splitting for heavy components

### Testing Patterns

- Component testing with @testing-library
- Accessibility testing with jest-axe
- Visual regression testing considerations
- Interaction testing for Radix components

---

*Last updated: 2025-02-01*
