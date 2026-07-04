# Easter Egg Details

Small moments of delight, hidden details, and overlooked surfaces that reward curiosity without blocking the main task.

**Skip when:** The user is trying to recover from a serious failure, finish urgent work, or operate in a regulated/high-stakes flow. Delight must never obscure consequence or recovery.

## 1. Turn error and 404 pages into a moment of delight
A missing page or error is a dead end by default. Treat it as a hidden room of your site rather than a void: add warmth and light interactivity so the few who land there leave less frustrated, not more. It's the same care you'd give the corners of a house guests never see.

## 2. Carry the active state into the footer
When the same navigation appears in both the header and the footer, light up the active link in the footer too. Most sites forget the footer nav; honoring it reinforces spatial awareness and shows the system is coherent everywhere, not just up top.

## 3. Reward the explorer in overlooked corners
The least-visited surfaces — the footer, an empty state, the inspect panel — reach only the users who explore furthest, exactly the audience worth a small surprise. A quiet detail there signals craft to the people most likely to notice it.

## 4. Embed a real detail where people look closely
Hide a genuine, verifiable detail in a high-craft surface like the app icon — Apple's Mail icon carries a real address ("Apple Park, California 95014"). It rewards the curious and signals that someone cared about the small stuff.

## 5. Make mundane tokens memorable
Where a product generates a throwaway string — an invite code, a share link — give it a shape worth remembering instead of random characters. Paper formats invite codes as color names with their hex values, turning a forgettable token into something delightful to share.
```js
const palette = { tomato: "#FF6347", azure: "#007FFF", amber: "#FFBF00" };
const name = pickRandomKey(palette);
const code = `${name}-${palette[name].slice(1)}`; // "azure-007FFF"
```

## 6. Give folders semantic icons by name (Need confirm)

Assign recognizable icons by naming convention — "Documents", "Developer", "Downloads" — so users scan instead of read. macOS does this automatically the moment a folder is named.

```js
const ICONS = { Documents: "📄", Developer: "⌨️", Downloads: "⬇️" };
const icon = ICONS[folder.name] ?? "📁";
```
