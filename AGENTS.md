## Development Commands

- `pnpm run typecheck` - Run typecheck
- `pnpm run lint` - Run ESLint

## Code Policy

- Refer the README.md for preferred file tree structure when creating new files
- Use kebab case for file names
- Prefer named exports over default exports
- DO NOT add `import React from "react"` to the top of a new file
- ALWAYS USE the `cn` util for writing conditional tailwind classes. DO NOT use template literals
- Prefer using the `function` keyword when creating components/functions over arrow functions
- DO NOT write trivial comments
- ABSOLUTELY AVOID `any`. Always prefer `unknown` over `any`
- Narrow down types and avoid type assertions

## UI Components Best Practices

### Popover and Select Components in Dialogs

When using Popover or Select components inside Dialog components, always add `modal={true}` to prevent scroll behavior issues:

```tsx
// ✅ Good - Inside Dialog
<Popover modal={true}>
  <PopoverTrigger>...</PopoverTrigger>
  <PopoverContent>...</PopoverContent>
</Popover>

<Select modal={true}>
  <SelectTrigger>...</SelectTrigger>
  <SelectContent>...</SelectContent>
</Select>

// ✅ Good - Outside Dialog (default behavior)
<Popover>
  <PopoverTrigger>...</PopoverTrigger>
  <PopoverContent>...</PopoverContent>
</Popover>
```

**Why this matters:**
- Fixes scroll behavior when popovers/selects open inside dialogs
- Prevents the dialog from scrolling unexpectedly when dropdown content appears
- Ensures proper focus management and accessibility

**Reference:** [shadcn/ui issue #4759](https://github.com/shadcn-ui/ui/issues/4759)

### Dialog close button action

- **Never use `AlertDialogAction` or `DialogClose`** for actions that require loading states or error handling
- **Always use regular `Button`** in dialog footers when you need to:
  - Show loading states during async operations
  - Handle errors without auto-closing the dialog
  - Manually control when the dialog closes
- **Reason**: Both `AlertDialogAction` and `DialogClose` have built-in behavior that closes the dialog immediately on click, preventing proper UX during async operations
- **Use controlled dialogs**: For complex interactions, manage dialog state with `useState` and the `open` prop rather than relying on built-in close triggers

## Animations Guidelines

### Keep your animations fast

- Default to use `ease-out` for most animations.
- Animations should never be longer than 1s (unless it's illustrative), most of them should be around 0.2s to 0.3s.

### Easing rules

- Don't use built-in CSS easings unless it's `ease` or `linear`.
- Use the following easings for their described use case:
  - **`ease-in`**: (Starts slow, speeds up) Should generally be avoided as it makes the UI feel slow.
    - `ease-in-quad`: `cubic-bezier(.55, .085, .68, .53)`
    - `ease-in-cubic`: `cubic-bezier(.550, .055, .675, .19)`
    - `ease-in-quart`: `cubic-bezier(.895, .03, .685, .22)`
    - `ease-in-quint`: `cubic-bezier(.755, .05, .855, .06)`
    - `ease-in-expo`: `cubic-bezier(.95, .05, .795, .035)`
    - `ease-in-circ`: `cubic-bezier(.6, .04, .98, .335)`
  - **`ease-out`**: (Starts fast, slows down) Best for elements entering the screen or user-initiated interactions.
    - `ease-out-quad`: `cubic-bezier(.25, .46, .45, .94)`
    - `ease-out-cubic`: `cubic-bezier(.215, .61, .355, 1)`
    - `ease-out-quart`: `cubic-bezier(.165, .84, .44, 1)`
    - `ease-out-quint`: `cubic-bezier(.23, 1, .32, 1)`
    - `ease-out-expo`: `cubic-bezier(.19, 1, .22, 1)`
    - `ease-out-circ`: `cubic-bezier(.075, .82, .165, 1)`
  - **`ease-in-out`**: (Smooth acceleration and deceleration) Perfect for elements moving within the screen.
    - `ease-in-out-quad`: `cubic-bezier(.455, .03, .515, .955)`
    - `ease-in-out-cubic`: `cubic-bezier(.645, .045, .355, 1)`
    - `ease-in-out-quart`: `cubic-bezier(.77, 0, .175, 1)`
    - `ease-in-out-quint`: `cubic-bezier(.86, 0, .07, 1)`
    - `ease-in-out-expo`: `cubic-bezier(1, 0, 0, 1)`
    - `ease-in-out-circ`: `cubic-bezier(.785, .135, .15, .86)`

### Hover transitions

- Use the built-in CSS `ease` with a duration of `200ms` for simple hover transitions like `color`, `background-color`,`opacity`.
- Fall back to easing rules for more complex hover transitions.
- Disable hover transitions on touch devices with the `@media (hover: hover) and (pointer: fine)` media query.

### Accessibility

- If `transform` is used in the animation, disable it in the `prefers-reduced-motion` media query.

### Origin-aware animations

- Elements should animate from the trigger. If you open a dropdown or a popover it should animate from the button. Change `transform-origin` according to the trigger position.

### Performance

- Stick to opacity and transforms when possible. Example: Animate using `transform` instead of `top`, `left`, etc. when trying to move an element.
- Do not animate drag gestures using CSS variables.
- Do not animate blur values higher than 20px.
- Use `will-change` to optimize your animation, but use it only for: `transform`, `opacity`, `clipPath`, `filter`.
- When using Motion/Framer Motion use `transform` instead of `x` or `y` if you need animations to be hardware accelerated.

### Spring animations

- Default to spring animations when using Framer Motion.
- Avoid using bouncy spring animations unless you are working with drag gestures.
