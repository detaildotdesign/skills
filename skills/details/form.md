# Form Details

Rules for crafting form inputs, keyboards, labels, and data entry interactions.

## Rules

### Label clicks focus the input
Use HTML `<label for="id">` so clicking a label focuses its associated input field. This expands the hit area of form controls, improving usability for all users — especially on touch devices.

### Respect the keyboard
Ensure every form interaction can be completed entirely with the keyboard. Keyboard-only users must never be blocked. This is both an accessibility requirement and a power-user expectation.

### Handle CJK input methods
Detect composing state via `compositionstart`/`compositionend` before acting on keystrokes in search or command fields. CJK input methods pre-fill candidate characters — listening for single-letter keys or Enter during composition breaks the experience for hundreds of millions of users.

### Context-aware Enter key
Make the Enter key context-aware: send a message normally, but insert a newline when the user is inside a code block or multi-line context. Match user intent based on editing context to prevent accidental sends.

### Pre-fill with example content
Show realistic example content in empty form fields instead of leaving them blank. Examples reduce cognitive load, teach by demonstration, and encourage users to take action.

### Offer a paste-from-clipboard button
Place a one-tap "Paste from Clipboard" button near input fields that commonly receive pasted content (URLs, codes, addresses). This saves the tap-hold-paste dance and speeds up common workflows.

### Morph button to input
Transition a button into an inline input field with a smooth morph animation rather than opening a separate dialog. This keeps the user in context and reduces the disorientation of modal switches.

### Live character counter
Transform a static element into a live ring-style character counter as the user types in a constrained field. Continuous, glanceable feedback on remaining capacity without adding extra UI elements.

### Accept natural language for dates
Accept natural language input (e.g., "next Friday", "in 3 days") for date pickers alongside the calendar UI. This matches how people think about dates, making scheduling faster and more intuitive.

### Auto-convert character sequences
Auto-convert character sequences like `->` into their proper symbol equivalents (e.g., arrows `→`) as the user types. This reduces friction for common input patterns and makes the editing experience feel intelligent.
