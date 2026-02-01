# Animation Patterns Reference

Authentic shadcn components use consistent, subtle animations. This guide covers timing, easing, and patterns that make components feel native.

## Core Principles

1. **Subtle over dramatic** - Animations enhance, never distract
2. **Consistent timing** - Same duration/easing for similar interactions
3. **Accessibility first** - Always respect `prefers-reduced-motion`
4. **GPU-accelerated** - Prefer `transform` and `opacity`

## Timing Standards

| Context | Duration | Use Case |
|---------|----------|----------|
| 150ms | Fast | Hover states, button press, focus rings |
| 200ms | Normal | Color transitions, most interactions |
| 300ms | Slow | Modal enter/exit, drawer slide, emphasis |

**Rule of thumb**: If it's a direct response to user action, use 150-200ms. If it's a state change the user is watching, use 200-300ms.

## Easing Curves

```tsx
// Enter animations (appearing)
transition={{ ease: "easeOut" }}
className="ease-out"

// Exit animations (disappearing)
transition={{ ease: "easeIn" }}
className="ease-in"

// Continuous/looping
transition={{ ease: "linear" }}
className="ease-linear"

// Spring (interactive elements)
transition={{ type: "spring", stiffness: 400, damping: 17 }}
```

## Tailwind Patterns

### Hover & Focus States

```tsx
// Button hover (fast, transform-based)
<Button className="transition-transform duration-150 hover:scale-[1.02] active:scale-[0.98]">

// Color transition (normal speed)
<Card className="transition-colors duration-200 hover:bg-accent">

// Focus ring (fast)
<Input className="transition-shadow duration-150 focus:ring-2 focus:ring-ring" />
```

### Loading States

```tsx
// Spinner
<Loader className="animate-spin" />

// Skeleton pulse
<div className="animate-pulse bg-muted rounded" />

// Notification ping
<span className="animate-ping absolute h-2 w-2 rounded-full bg-primary" />
```

### Accessibility

```tsx
// Always use motion-safe for transforms
className="motion-safe:transition-transform motion-safe:hover:scale-105"

// Or for any animation
className="motion-safe:animate-spin"
```

## Radix Primitive Animations

Radix components expose `data-state` attributes for CSS animations:

```css
/* Dialog/Sheet animations */
[data-state="open"] {
  animation: fadeIn 200ms ease-out;
}
[data-state="closed"] {
  animation: fadeOut 150ms ease-in;
}

/* Accordion/Collapsible */
[data-state="open"] {
  animation: slideDown 200ms ease-out;
}
[data-state="closed"] {
  animation: slideUp 150ms ease-in;
}
```

### Tailwind v4 with data-state

```tsx
// Using Tailwind's data-* variants
<DialogContent className="
  data-[state=open]:animate-in
  data-[state=open]:fade-in-0
  data-[state=open]:zoom-in-95
  data-[state=closed]:animate-out
  data-[state=closed]:fade-out-0
  data-[state=closed]:zoom-out-95
">
```

## Framer Motion Patterns

### Modal/Dialog

```tsx
<AnimatePresence>
  {isOpen && (
    <motion.div
      initial={{ opacity: 0, scale: 0.95 }}
      animate={{ opacity: 1, scale: 1 }}
      exit={{ opacity: 0, scale: 0.95 }}
      transition={{ duration: 0.2, ease: "easeOut" }}
    >
      <DialogContent />
    </motion.div>
  )}
</AnimatePresence>
```

### Drawer/Sheet

```tsx
<motion.div
  initial={{ x: "100%" }}
  animate={{ x: 0 }}
  exit={{ x: "100%" }}
  transition={{ type: "spring", damping: 25, stiffness: 300 }}
>
```

### Staggered Lists

```tsx
const container = {
  hidden: { opacity: 0 },
  show: {
    opacity: 1,
    transition: { staggerChildren: 0.05 }
  }
}

const item = {
  hidden: { opacity: 0, y: 10 },
  show: { opacity: 1, y: 0, transition: { duration: 0.2 } }
}
```

### Reduced Motion Hook

```tsx
import { useReducedMotion } from "framer-motion"

function Component() {
  const shouldReduceMotion = useReducedMotion()

  return (
    <motion.div
      animate={{
        x: shouldReduceMotion ? 0 : 100,
        opacity: 1 // opacity is usually fine
      }}
    />
  )
}
```

## Decision Tree

```
Is it hover/focus/active state?
  → Tailwind (transition-*, duration-150)

Is it a loading indicator?
  → Tailwind (animate-spin, animate-pulse)

Does element enter/exit DOM?
  → Framer Motion (AnimatePresence)
  → OR Radix data-state with Tailwind animate-in/out

Multiple elements in sequence?
  → Framer Motion (staggerChildren)

Gesture-based (drag, press)?
  → Framer Motion (whileHover, whileTap, drag)

Otherwise?
  → Start with Tailwind, upgrade if needed
```

## Anti-Patterns

❌ **Avoid:**
- Durations over 400ms for UI interactions
- `transition: all` (use specific properties)
- Animating `width`/`height` (use `transform: scale`)
- Forgetting `motion-safe:` prefix
- Dramatic bounces or overshoots

✅ **Prefer:**
- Specific transition properties (`transition-transform`, `transition-colors`)
- `transform` and `opacity` only when possible
- Subtle, professional motion
- Consistent timing across similar components
