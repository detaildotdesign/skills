# Interface Details Skill

A [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code) that helps developers bring crafted micro-interactions, polish, and thoughtful details to their interfaces — based on 100+ real-world examples curated on [detail.design](https://detail.design).

## What this skill does

Most users will never notice any single design detail. But they will feel all of them together. This skill encodes that craft into actionable rules an AI coding assistant can apply while building UI.

It covers:

- **Form** — inputs, keyboards, labels, paste behavior
- **Toast & Notifications** — feedback, loading states, status indicators
- **Motion & Animation** — transitions, hover states, layout choreography
- **Button & Interactive Elements** — cursors, hit areas, shortcuts
- **Typography & Text** — overflow, truncation, formatting
- **Scroll & Navigation** — anchoring, overscroll, ToC highlighting
- **Accessibility** — focus rings, reduced motion, touch targets
- **Layout & Spacing** — border radius, optical alignment
- **Browser & URL** — favicons, theme-color, meta tags, PWA
- **Content & Intelligence** — smart defaults, auto-detection
- **Easter Eggs & Delight** — hidden features, personality

## Install

```bash
claude install-skill rivertwilight/detail-skill
```

## Usage

Once installed, the skill is automatically available in Claude Code. You can also load specific guideline files:

```
Load details/form.md and review my form component for missing details.
```

## License

MIT
