# Accessibility Details

Rules for focus management, reduced motion, screen reader support, and inclusive design.

## Rules

### Never remove focus rings
Never remove the browser's default `outline` on focusable elements. Customize it if needed, but always provide a visible focus indicator. The focus ring is the primary landmark for keyboard users.

### Reduce animation for frequent features
Reduce or eliminate animations for tools users invoke repeatedly throughout the day. Delight fades with repetition — frequent-use tools should prioritize speed over spectacle. Respect `prefers-reduced-motion`.

### Describe link destinations
Provide descriptive text for link actions (e.g., "Opens in new tab" or "Downloads PDF") rather than generic "Click here." Screen reader users and sighted users alike benefit from knowing what will happen.

### Minimum 44px touch targets
Extend touch targets beyond the visible bounds to at least 44px on mobile and 24px on desktop. Accessible tap targets are a WCAG requirement and improve usability for users with motor impairments.

### Preserve meaningful parts in truncation
When truncating text (especially file paths), ensure the meaningful parts remain readable. Assistive technologies read the truncated string — the important segments must survive.

### Single-key shortcuts as alternatives
In specialized tools, support single-key shortcuts alongside modifier-based ones. Single-key shortcuts reduce the physical effort required, benefiting users with motor limitations.

### Natural language as accessible alternative
Accept natural-language input (e.g., for dates) as an alternative to complex widgets. Calendar pickers can be difficult for screen reader users — natural language is universally accessible.
