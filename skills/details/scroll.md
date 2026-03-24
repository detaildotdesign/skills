# Scroll & Navigation Details

Rules for scroll behavior, anchoring, navigation patterns, and overscroll effects.

## Rules

### Three-phase anchored scrolling
In long lists with keyboard navigation, lock the highlight at ~70% viewport height and scroll the list beneath it, releasing at the boundaries. Three-phase scrolling (move highlight → scroll list → release at end) creates a stable visual anchor.

### Prevent accidental swipe-back
Use `overscroll-behavior-x: none` on horizontally scrollable UI to prevent the browser's swipe-back navigation. Accidental page-back during horizontal scrolling destroys user state.

### Overscroll in nested scrollers
Enable overscroll effects (rubber-banding) on nested scrollable containers. Without overscroll feedback, nested scrollers feel dead-ended and users cannot tell they have reached the boundary.

### Don't hide scrollbar with fade edges
When adding a fade-out mask to a scrollable container, ensure it does not overlap or hide the scrollbar. Obscuring the scrollbar removes a critical navigation affordance.

### Always-visible scroll-to-top
Provide a visible, always-accessible button to scroll back to the top of long pages. Platform shortcuts (like iOS status-bar tap) are not discoverable or universal.

### Keep origin visible in detail views
When a user is viewing a detail panel opened from a list, keep the originating list item visible or highlighted. Maintaining the visual link between entry point and detail prevents spatial disorientation.

### Searchable collapsed content
Use the HTML `hidden="until-found"` attribute so browser find-in-page (Cmd+F) can discover and auto-expand collapsed sections. Content hidden with `display: none` is invisible to browser search.

### Show recent actions near pending ones
Show recently completed items near pending items so users can quickly access what they just acted on. Closure design — after completing an action, the user should have immediate access to its result.

### Viewport-based ToC highlighting
Highlight table-of-contents items based on which sections are currently visible in the viewport, not just which anchor was last crossed. This allows multiple items to be active, making the ToC a true minimap.
