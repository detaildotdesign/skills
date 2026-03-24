# Motion & Animation Details

Rules for transitions, hover states, micro-animations, and layout choreography.

## Rules

### Animate with meaning
Animate action buttons with meaningful motion that reflects their purpose (e.g., a plus icon that rotates into a close icon). Motion should reinforce function, not just add flair.

### Smooth color transitions
When changing an element's color (e.g., in an icon picker), smoothly transition through intermediate hues rather than snapping instantly. Smooth transitions feel natural and help users track the change.

### Mirror action in icon
Animate toggle icons (like sidebar open/close) to mirror the actual motion of the element they control. The icon becomes a miniature preview of the action, reinforcing spatial understanding.

### Close modals to their origin
When dismissing a modal that expanded from a specific element, animate it back to its origin point, tracking scroll position changes. Physics-based return animations maintain spatial continuity.

### Lock cursor during morphs
Lock the cursor style during morph transitions so form elements do not cause cursor flickering mid-animation. A consistent cursor maintains the illusion of a single fluid motion.

### Make animations interruptible
Allow users to immediately trigger close/cancel during an opening animation without waiting for it to complete. Non-interruptible animations make interfaces feel sluggish and unresponsive.

### Slide highlights between items
Animate the highlight indicator between items (e.g., in a navigation menu) with a smooth sliding motion rather than an instant jump. Sliding creates a sense of physical continuity between states.

### Stagger sequential reveals
When multiple elements appear simultaneously, stagger their timing to create a sequential reveal. Staggering guides the eye through a clear reading order and prevents visual chaos.

### Animate between tooltips
When moving between adjacent tooltips, animate the tooltip's position and content transition rather than hiding and re-showing. This eliminates the flicker of tooltip off/on.

### Prevent font-weight layout shift
Use an invisible `::after` pseudo-element with bold text to pre-reserve the bold width, so toggling font weight (e.g., on hover) does not cause layout shifts.

### Choreograph layout changes
When expanding elements (like album art or media controls), smoothly slide surrounding elements rather than letting them jump. Choreographed layout shifts maintain spatial relationships.

### Blurred gradient edges
When adding a fade-out gradient at the edge of scrollable content, use a blur-based approach and ensure it bleeds to the container edge. A soft blurred edge looks more natural than a hard gradient mask.

### Physical metaphors
Design digital interactions to mimic physical behaviors — expanding like bubbles, sliding like cards, bouncing on impact. Physical metaphors leverage real-world intuition.

### Frosted glass surfaces
Combine backdrop blur, transparency, thin borders, and soft shadows to create frosted-glass-style buttons and surfaces. Glass-morphism surfaces feel elevated and modern while maintaining readability.

### ASCII loaders for text UI
Use character-based spinner animations in terminal or text-based interfaces. Adds personality and progress indication even in constrained text environments.

### Reduced animation for frequent use
Reduce or eliminate animations for tools and features that users invoke repeatedly. Delight fades with repetition — frequent-use tools should prioritize speed over spectacle.

### Colorful cursor blink
Cycle the text cursor through brand colors on each blink in special input contexts. A low-cost micro-detail that reinforces brand identity.

### Chat minimap
Pin a subtle minimap to the viewport in long chat transcripts showing which region the user is reading. Provides spatial awareness and prevents users from losing their place.
