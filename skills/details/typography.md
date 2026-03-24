# Typography & Text Details

Rules for text rendering, overflow, truncation, and formatting.

## Rules

### Trim text box spacing
Use `text-box-trim: trim-both` with `text-box-edge: cap alphabetic` to remove browser-added space above and below text. Eliminates unpredictable vertical spacing for pixel-perfect alignment, especially in buttons or badges.

### Graceful text overflow
For fixed-width elements like tabs, use a gradient text mask to fade out long labels, or an ellipsis to indicate truncation. Abrupt text clipping feels broken — a fade or ellipsis communicates that more content exists.

### Smart file path truncation
When truncating file paths, always preserve the root folder and file name, collapsing only the middle segments. The root and file name are the two most important reference points.

### Respect brand name capitalization
Always use the correct capitalization for brand names (GitHub, not Github; macOS, not MacOS; YouTube, not Youtube). Incorrect casing signals carelessness and can violate brand guidelines.

### Space-aware cut and paste
Implement space-aware cut and paste — when cutting a word, automatically handle surrounding spaces so no double-spaces or missing spaces remain. A technique dating to 1984 Inside Macintosh.

### Live title sync
Update the browser tab title in real-time as the user edits content (e.g., a document title), before they save. Anticipatory feedback reinforces that the system is responsive and tracking user intent.

### Direct social handles over "Follow us"
Instead of writing "Follow us on X," simply display your social handle directly. Cleaner, more confident, and the handle itself is the call to action.
