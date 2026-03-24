# Layout & Spacing Details

Rules for border radius, layout shifts, optical alignment, and visual spacing.

## Rules

### Nested border radius calculation
When nesting rounded elements, calculate the inner border radius as the outer radius minus the padding between them. Mismatched radii create an optically uneven gap that looks unpolished.

```
inner-radius = outer-radius - padding
```

### Blur test for optical alignment
Blur your layout at design time to check whether elements are optically centered rather than mathematically centered. Human perception of alignment differs from pixel-perfect math — blurring reveals optical imbalances.

### Inset shadow for image borders
Use an inset `box-shadow` with a semi-transparent color instead of a CSS border for image edges. An inset ring blends with the image content and avoids the harsh line a border creates.

```css
img {
  box-shadow: inset 0 0 0 1px rgba(0, 0, 0, 0.1);
}
```

### Reserve space for weight changes
Use an invisible `::after` pseudo-element with bold text to pre-reserve the bold width, so hover/active font weight changes do not cause layout shifts.

### Animate layout expansions
When media controls or panels expand, smoothly slide surrounding elements rather than letting content jump. Choreographed layout transitions maintain spatial relationships.

### Contextual visual guidelines
Show visual guidelines (alignment lines, row highlights) on table hover, and fade them when clicking to avoid visual clutter. Temporary guidelines help users read data without adding permanent visual noise.
