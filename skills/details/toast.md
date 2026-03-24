# Toast & Notification Details

Rules for feedback, notifications, status indicators, and loading states.

## Rules

### Proactive content validation
Scan user-generated content for common mistakes (e.g., missing unsubscribe link in emails, broken URLs) and show a warning before sending. Proactive validation prevents costly errors and builds user trust.

### Shake on disabled click
When a user clicks a disabled button, play a subtle shake animation instead of doing nothing. Silent failure is confusing — the shake communicates "I heard you, but you cannot do this yet" without an intrusive alert.

### Lifecycle indicators
Use a small animated indicator (pulsing dot, ring) to communicate the current lifecycle state of a process (loading, active, complete). Continuous ambient feedback reduces anxiety and the urge to re-trigger actions.

### Self-explanatory loading
Design loading bars that visually explain what they trigger — e.g., a bar that fills to initiate a view switch. Makes the interaction self-documenting; users understand causality without instructions.

### Dynamic favicon as status
Update the browser favicon to reflect current page status (build passing, PR merged, notification count). Users with many tabs can glance at favicons for status without switching tabs.

### Color code previews
When displaying hex color codes in text, show a small colored chip next to the code. This bridges the gap between abstract code and visual meaning — users can identify colors instantly.

### Collapse instead of close
Use "Collapse" instead of "Close" for dismissible panels like "What's New" popups, keeping them accessible in a minimized state. Users are hiding, not destroying — they can return to the content later.

### Delay promotional close button
Add a brief delay before the close button on promotional banners becomes active. This guarantees at least a moment of exposure to your message without being as hostile as removing the close button entirely.
