# Interactivity Details

Inputs, controls, scrolling, paste behavior, shortcuts, contextual actions, and direct manipulation that make the interface respond to intent.

**Skip when:** The behavior would surprise users, conflict with native platform expectations, or fire in ambiguous contexts. Interactive details should acknowledge intent without stealing control.

## 1. Make Enter context-aware

Enter should submit in single-line intent and insert a newline inside a code block or multi-line context — Discord sends a message normally but wraps when the caret sits in a markdown code fence. Branch on caret context (and modifier keys) so the same key matches what the user is doing.

```js
function onKeyDown(e) {
	if (e.key === "Enter" && !e.shiftKey && !inCodeBlock()) {
		e.preventDefault();
		send();
	}
}
```

## 2. Auto-convert common character sequences (Need confirm)

Replace typed sequences with their intended glyphs as the user types — `->` becomes `→`, `--` becomes `—` (Notion and Linear both do this). Convert only unambiguous patterns so the editor feels smart without fighting the user.

## 3. Make the hit area larger than the visual element

Per Fitts's Law, acquiring a target is faster the bigger it is — so let the button look small and refined while feeling generous and forgiving. Pad the hit area beyond the glyph rather than bloating the glyph itself. Rule of thumb: extend the hit area for any visual smaller than 44px on mobile, 24px on desktop.

## 4. Reserve the pointer cursor for navigation

Default to the arrow cursor everywhere, then opt into `pointer` only where a click takes the user to a new page. The cursor then reliably predicts whether a click navigates or just acts in place.

## 5. Use a contextual cursor over special targets

Swap to a context-specific cursor when hovering an element with a distinct interaction model — e.g. Linear shows a help cursor over an author/people section so the cursor itself signals "more info here, not a link."

## 6. Offer single-key shortcuts in power-user tools

In non-compositional, high-frequency views (a dashboard, not a doc editor), bind bare keys without Cmd/Ctrl/Alt — press `F` and the find menu opens instantly. Removing the modifier shaves a micro-decision off every action and rewards mastery. Skip the shortcut when focus is in a text field, where the keypress should compose text.

## 7. Collapse instead of close

For dismissible panels like "What's New," offer "Collapse" rather than "Close" so the content minimizes instead of vanishing. People are hiding the popup, not destroying it — keep the return path one click away (Linear and Vercel both do this).

## 8. Delay the promo close button

Gate the close button on a promotional banner or "What's New" popup behind a short delay so the headline gets a beat of exposure before it can be dismissed. It forces a split-second glance — less hostile than omitting the close affordance, and it still respects the user's exit.

## 9. Snap crop to component edges

When crop handles drag within a few pixels of a UI boundary, snap to that edge. It eliminates pixel-peeping and produces clean, professional cuts instantly.

```js
if (Math.abs(handleX - edgeX) < SNAP_THRESHOLD) handleX = edgeX;
```

## 10. Respect whitespace on cut and paste

When cutting or pasting words in space-delimited languages, fix up the surrounding spaces so the user never lands on doubled or missing whitespace. A 1984-era Mac detail that still trips up most editors. Skip for languages without word spaces (Chinese, Japanese, Thai).

```js
// deleting a word: collapse the leftover double space
text = text.replace(/  +/g, " ").replace(/ ([.,!?])/g, "$1");
```

## 11. Honor paste context

Read the surface the paste lands on. A URL dropped onto a canvas or visual board becomes a rich embed; the same URL in a text field or code editor stays literal text. Only transform when context makes intent unambiguous and the change is cheaply reversible.

```js
if (target.type === "canvas" && isURL(pasted)) insertEmbed(pasted);
else insertText(pasted);
```

## 12. Live-sync the title to the field being edited

When the field is the primary identifier, reflect edits in the page or tab title in real time, before save — it tightens the loop between "what I'm typing" and "what this becomes," and doubles the browser tab as a live preview. Don't do this for non-identifier fields or values where mid-typing updates would disorient (a banking balance updating per keystroke).

## 13. Tap the active tab again to reset it

Re-tapping the tab you're already on should reset state: scroll to top, refresh data, or pop back to the section root. The first tap navigates, the second gives a predictable, muscle-memory home base when you're lost deep in a feed.

```js
function onTabPress(tab) {
	if (tab === activeTab) tab.scrollToTop({ refresh: true });
	else navigate(tab);
}
```

## 14. Prevent accidental swipe-back

Set `overscroll-behavior-x: none` on any horizontally scrollable UI. Without it, a horizontal swipe past the edge triggers the browser's built-in back gesture and destroys page state.

```css
.carousel {
	overflow-x: auto;
	overscroll-behavior-x: none;
}
```

## 15. Enable overscroll in nested scrollers

Let inner scrollable containers rubber-band at their boundaries so an edge reads as "end of this region," not a dead surface — now supported across Chrome, WebKit, and Firefox. Use `overscroll-behavior: contain` to give the inner scroller its own bounce without leaking scroll to the parent.

```css
.panel {
	overflow-y: auto;
	overscroll-behavior: contain;
}
```

## 16. Provide a scroll landmark back to the top

Long pages need a discoverable, persistent way back to the top that also remembers where the user was. Platform shortcuts (iOS status-bar tap, Home key) are device-specific, undiscoverable, and can't return to the original position.

```jsx
<button onClick={() => window.scrollTo({ top: 0, behavior: "smooth" })}>
	↑ Top
</button>
```

## 17. Pre-fill fields with example content

Seed empty fields with realistic, editable sample values — not just gray placeholder text — because people love to copy. Concrete examples teach the expected format and lower the activation cost of starting.

## 18. Accept natural-language dates

Parse phrases like "next Friday" or "in 3 days" alongside the calendar picker. People express dates in relative terms; resolving them to a concrete date is faster than navigating a grid.

```js
import * as chrono from "chrono-node";
const date = chrono.parseDate("next Friday"); // → Date
```

## 19. Tolerate overflow so people can finish their thought

Don't hard-truncate or block typing at a visual boundary — let the value scroll or wrap past the field's width and let people complete the input before you validate or trim. Cutting them off mid-thought loses content and trust.

## 20. Combine magic-link and password into one login field (Need confirm)

Let a single field accept either an email (for a magic link) or a password, branching on what was entered instead of forcing the user to pick an auth method up front. One field reads as less work than a choice between two flows.

## 21. Guard against duplicate clicks

Disable the trigger the instant it fires so a rapid double-click or impatient repeat-tap can't submit a second order, message, or API call. Re-enable only after the request resolves.

## 22. Confirm subscriptions with double opt-in

Send a confirmation email and require the user to click before activating a newsletter signup. It protects people from being subscribed by someone else's typo and protects your sender reputation by keeping the list to addresses that actually exist and want in.

```js
async function subscribe(email) {
	const token = crypto.randomUUID();
	await store.pending(email, token);
	await sendEmail(email, `Confirm: https://app/confirm?t=${token}`);
	// activate only when the link is clicked
}
```

## 23. Turn completion into presence, not absence

When a background action finishes (updates, syncs, migrations), don't just remove the item from its pending list — surface it in a "Recently updated" section right below. Apple moves finished App Store updates there instead of letting them vanish; the loop closes visually, reassuring the user it actually shipped and giving quick access to what just changed.

## 24. Validate content before the destructive send

Scan user-generated content for predictable mistakes (missing unsubscribe link, broken URL, empty required field) and surface a warning before the irreversible action fires. Catching the error pre-send is cheaper than an apology email after.

## 25. Name files from their capture context

Auto-name screenshots and exports from the visible app, page title, or content at capture time — don't try to be clever with timestamps and metadata prefixes, just name the thing what it is. A file named `Stripe-dashboard.png` is findable months later; `Screenshot 2026-06-29.png` is a graveyard entry.

```js
const name = `${detectVisibleTitle() ?? activeApp}.png`;
```

## 26. Auto-segment video chapters

Detect real content changes in video and create chapter markers automatically. Users jump to the relevant section instead of scrubbing blindly. Trigger on scene cuts, slide changes, or speaker shifts — not fixed intervals.

## 27. Pre-flight user content for missing pieces

Scan user content for omissions that will cause real harm — a missing unsubscribe link before sending a broadcast, "I've attached" with no attachment, a merge with unresolved conflicts — and block or warn before the irreversible action. This is poka-yoke: move the checklist off the user and onto the system.

```js
if (action === "send" && !/unsubscribe/i.test(emailHtml)) {
	block("No unsubscribe link found — add one before sending.");
}
```

## 28. Make detected data actionable

Detect addresses, phone numbers, and links in document and message viewers and make them tappable. Removes the copy-paste-switch-app cycle for common real-world data like an address buried in a PDF.

```html
<a href="tel:+14155550123">(415) 555-0123</a>
<a href="https://maps.apple.com/?q=...">1 Infinite Loop</a>
```

## 29. Offer inline unit conversion

Detect units — temperature, distance, weight, currency — in text and offer inline conversion to the user's preferred system. Kills mental math and app-switching at the point of reading.

```js
text.replace(
	/(\d+)°F/g,
	(m, f) => `${m} (${Math.round(((f - 32) * 5) / 9)}°C)`,
);
```

## 30. Tap an amount in a photo to convert it

When a viewer shows monetary amounts in an image, let users tap any value for an instant local-currency conversion in a contextual popover — no copy, no calculator, no exchange-rate search. The same "tap to transform" pattern extends to measurements, time zones, and dates.

## 31. Search by intent, not keyword match

Resolve what the user means, not just what they typed: "change my password" must surface account-security settings even when those exact words never appear, and "John" should mean something different in mail than in contacts. Match on meaning, synonyms, and the current context.

## 32. Interpret time against the human day model

When a user says "wake me at 9am tomorrow" at 1am, "tomorrow" means after their next sleep — eight hours out, not 32. The human day flips at sleep, not midnight. When the interpretation is genuinely ambiguous, ask which day rather than guessing wrong.

## 33. Anchor list scrolling in three phases

In a long list with arrow-key navigation, first move only the highlight; once it reaches ~70% down the viewport, lock it and scroll the list beneath it; release the lock at the top and bottom so the user lands on the final item. A fixed visual anchor keeps the eye still while the data moves. Keep any input field anchored too — center the whole panel and its position will drift as the list height changes. Belongs in every CMDK-style menu.

## 34. Keep the active view's entry visible

When a detail view opens from a list or sidebar, keep its originating row visible and highlighted. The persistent link between entry point and content prevents spatial disorientation when the user navigates back.

## 35. Highlight the ToC by visibility, not last anchor

Activate table-of-contents items based on which sections are currently in the viewport, not just the last anchor crossed. Multiple items can be active at once, turning the ToC into a true minimap; transition the highlight bar smoothly rather than letting it stagger between items.

## 36. Reflect live status in the favicon

On pages with a clear state — a GitHub PR, a CI workflow, an export job — repaint the favicon to mirror it (pending → pass/fail, draft → published, unread count). It becomes an at-a-glance indicator readable across a wall of tabs without switching to any of them. Deep respect for a cluttered workspace.

## 37. Serialize UI state into the URL

Encode filters, search query, sort, view mode, selection, and even scroll position as URL params. The view becomes shareable, bookmarkable, and survives back-button and refresh — a saved URL is a snapshot of a configuration, not just a destination. For one-way data it also avoids a database round-trip entirely.

## 38. Serve from the apex domain (Need confirm)

Drop the `www.` subdomain and serve from the bare apex. Modern DNS, CDNs, and HTTP/2/3 handle apex domains fine; the prefix is legacy noise, and cleaner URLs are easier to type, share, and remember.
