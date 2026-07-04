# Typography Details

Text rendering, truncation, inline formatting, document typography, and typographic polish that make content easier to read.

**Skip when:** Content is purely structural or machine-readable. Don't typographically rewrite code, identifiers, API fields, or exact user input.

## 1. Trim text box spacing

Browsers add invisible space above capital letters and below the baseline, breaking vertical centering in tight components. Trim it so the visual box equals the cap-to-baseline box, removing the need for negative-margin hacks. Most impactful in buttons, badges, and chips.

```css
.button {
	text-box-trim: trim-both;
	text-box-edge: cap alphabetic;
}
```

## 2. Fade and ellipsis on overflow

Abrupt clipping reads as broken. For fixed-width elements like tabs, fade the end with a gradient mask so long labels dissolve instead of being chopped, and pair it with an ellipsis so users know text was truncated.

```css
.tab-label {
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;
	mask-image: linear-gradient(to right, black 80%, transparent);
}
```

## 3. Truncate file paths from the middle

The two things that matter in a path are the root folder and the file name — collapse the middle segments only, never those anchors. Truncating the file name destroys the path's purpose.

```js
function truncatePath(path, maxSegments = 3) {
	const parts = path.split("/").filter(Boolean);
	if (parts.length <= maxSegments) return path;
	return `${parts[0]}/…/${parts[parts.length - 1]}`;
}
```

## 4. Respect brand name capitalization

Render brand names with their official casing: GitHub not Github, macOS not MacOS, iOS, iPad, iPhone, YouTube not Youtube. Wrong casing reads as careless and can breach brand guidelines. Keep a canonical map so it stays consistent everywhere.

## 5. Style text selection on brand

The default selection highlight is a missed surface. A custom `::selection` color carries the brand into an interaction users trigger constantly, adding a moment of delight to plain text.

## 6. Preview color strings inline

A hex string like `#3B82F6` is machine-readable but not human-readable. Render a small color chip directly beside the code so the value becomes recognizable instantly, with no picker or hover required.

```css
.color-chip {
	display: inline-block;
	width: 0.85em;
	height: 0.85em;
	margin-right: 0.3em;
	border-radius: 3px;
	border: 1px solid rgba(0, 0, 0, 0.15);
	vertical-align: -0.1em;
	background: var(--chip-color);
}
```

## 7. Give generated documents real typography
Invoices, receipts, and exported PDFs default to boring system layouts. Treat them as a branded surface: deliberate type scale, aligned columns, and spacing that matches the product, so the document reads as crafted rather than auto-generated.
