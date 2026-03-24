# Button & Interactive Element Details

Rules for buttons, click states, cursors, hit areas, and keyboard shortcuts.

## Rules

### Larger hit area than visual size
Make touch/click targets at least 44px on mobile and 24px on desktop, even if the visual element is smaller. Fitts's Law — a larger target means faster, more confident interactions without compromising visual refinement.

### Correct cursor semantics
Use `cursor: pointer` only for elements that navigate to a new page. Use the default cursor for in-page actions like buttons and toggles. Consistent cursor semantics help users predict the result of a click.

### Prevent duplicate submissions
Disable or debounce buttons after the first click to prevent duplicate submissions. Double-click accidents cause duplicate orders, messages, and API calls.

### Contextual cursor on hover
Change the cursor to a contextual style (e.g., a custom avatar cursor) when hovering over interactive elements like user profiles or special controls. The cursor becomes a signal of the interaction model.

### Consistent active states everywhere
Ensure active/selected state indicators appear consistently across all navigation instances, including the footer. Spatial awareness should persist everywhere — inconsistency breaks mental models.

### Animated hover states on icons
Use animated hover states on icon actions (e.g., a paperclip that opens on hover to signal "unpin") to communicate both current state and available action.

### Single-key shortcuts for power users
In power-user tools, allow single-key shortcuts (e.g., press `F` to find) without requiring modifier keys. Removes finger gymnastics and turns the interface into a high-velocity command center.

### Tap active tab to reset
When a user taps an already-active tab, reset its state (scroll to top, refresh data, clear filters). Creates a predictable "home base" gesture that builds muscle memory.
