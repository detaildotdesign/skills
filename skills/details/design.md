# Design Details

Visual craft across layout, surfaces, browser chrome, media, spacing, and platform presentation.

**Skip when:** The surface is plain text, a throwaway internal screen, or a layout that does not benefit from visual polish. Prefer consistency with the product system over one-off styling.

## 1. Match nested border radius to padding

Concentric corners must stay parallel. Set the inner radius to the outer radius minus the gap between them, or the curves drift and the gap looks optically uneven. This won't fit every layout, but reach for it whenever one rounded box sits inside another.

```css
.outer {
	border-radius: 16px;
	padding: 4px;
}
.inner {
	border-radius: 12px;
} /* 16 - 4 */
```

## 2. Blur-test optical alignment

Mathematically centered isn't always perceptually centered — icons with visual weight on one side, triangles, and glyphs read as off-center. Blur or squint at the layout (watch a recording at 0.5x) and nudge until it sits right; misalignments that survive the blur are real.

## 3. Use an inset ring instead of a border on images

A solid `border` adds a hard line that competes with the image and shifts layout by its width. A semi-transparent inset `box-shadow` sits inside the bounds, blends with light or dark content, and gives the edge a softer, more natural boundary.

```css
img {
	box-shadow: inset 0 0 0 1px rgba(0, 0, 0, 0.1);
}
```

## 4. Reveal alignment guides only on hover, hide them on click

Persistent gridlines and row highlights become noise. Show the guide on table hover so the eye can trace a value, then temporarily fade it out on click so the active selection highlight stands alone.

```css
.row:hover {
	background: var(--guide-tint);
}
.table.is-clicking .row:hover {
	background: transparent;
}
```

## 5. Style the video player, not just its toolbar

Owning the player means more than recoloring the default controls. Blur the poster frame until the stream loads so there's no hard pop-in, add speed control, and theme the toolbar to match the product surface.

```css
video[data-loading] {
	filter: blur(12px);
	transition: filter 200ms;
}
.player__rate {
	/* 0.5x / 1x / 1.5x / 2x toggle */
}
```

## 6. Style the scrollbar to match the surface

A default OS scrollbar reads as chrome bolted onto your UI. A thin, low-contrast scrollbar recedes until needed and keeps the design coherent.

## 7. Don't let fade edges cover the scrollbar

A fade-out mask on a scroll container must not overlap the scrollbar track. Inset the mask or apply it to the content layer only — obscuring the scrollbar removes a load-bearing navigation affordance.

## 8. Sync theme-color with the page background

The address bar shouldn't be a white strip. Match `<meta name="theme-color">` to the current background so the browser chrome merges with the app for a native-like, immersive feel. Update it dynamically on scroll, theme, or route changes — not just at load.

## 9. Ship light/dark favicon variants

Serve separate favicon SVGs gated by `prefers-color-scheme` so the icon never clashes with the OS tab bar in either mode.

```html
<link
	rel="icon"
	href="/favicon-light.svg"
	media="(prefers-color-scheme: light)"
/>
<link
	rel="icon"
	href="/favicon-dark.svg"
	media="(prefers-color-scheme: dark)"
/>
```

## 10. Adapt media to theme mode

Almost anything on the page can respond to light/dark mode — not just colors. Swap photos, illustrations, or video sources so imagery stays legible and on-brand in both modes instead of glowing or washing out against the opposite background.

```html
<picture>
	<source srcset="/hero-dark.avif" media="(prefers-color-scheme: dark)" />
	<img src="/hero-light.avif" alt="" />
</picture>
```

## 11. Use PNG or JPEG for Open Graph images

Render OG images as PNG or JPEG, never WebP — Facebook, X, LinkedIn, and iMessage have inconsistent or no WebP preview support, so it silently fails to render. Keep key content (text, logos) inside a ~1000×500px center safe zone to survive cropping across platforms.
