# HURL Project

## Style Guide

All design decisions should follow the style guide at **[style.md](./style.md)**.

Key references:
- **Primary color:** `#7F3708`
- **Background color:** `#F5F0EA`
- **Secondary (text) color:** `#111827`
- **Default font:** Open Sauce Sans (files in `fonts/`)
- **Main logo:** `images/hurl_white.png`

Always consult `style.md` for full details on colors, typography, font-face setup, and usage guidelines.

## Dev Server Setup

`.claude/launch.json` is **gitignored** — each worktree needs its own. When starting work in a worktree that doesn't have one, create it with a **unique port** (pick a random port between 8100–8999 that isn't already in use):

```json
{
  "version": "0.0.1",
  "configurations": [
    {
      "name": "brochure",
      "runtimeExecutable": "python3",
      "runtimeArgs": ["-m", "http.server", "<PORT>"],
      "port": <PORT>
    }
  ]
}
```

## Design Options Pattern

When presenting multiple design options to the user, use the **Design Options** system built into the project. This lets the user browse options visually with arrow keys or a floating picker, rather than having to imagine differences from descriptions.

### How to use it

1. **Wrap alternatives** in a `<div class="design-options">` container with:
   - `data-option-group="unique-id"` — identifies this choice point
   - `data-label="Human-readable label"` — describes **what design choice** this is about (e.g., "Keynote Card Style", "Header Layout")

2. **Each option** is a `<div class="design-option">` with:
   - `data-option="A"` (or B, C, D...) — the letter label
   - `data-desc="Short description"` — what makes this option different (e.g., "Horizontal + accent bar", "Outline cards, left stripe")
   - Add class `active` to the default/first option

3. **The picker JS** (at the bottom of the HTML file) automatically:
   - Renders a floating bottom bar with ← → arrows, dot indicators, and the option label/description
   - Supports keyboard arrow keys for navigation
   - Hides non-active options and shows only the selected one
   - Hides itself when printing

### Multiple groups
When there are multiple independent design choices on the same page, use multiple `<div class="design-options">` containers. The picker automatically:
- Shows **clickable tabs** at the top of the bar for each group (labeled by `data-label`)
- Highlights the active group's tab in gold
- **Tab / Shift+Tab** keyboard shortcuts switch between groups
- **← →** arrows cycle options within the active group
- Each group's state is tracked independently — switching groups preserves each group's selected option

### Rules
- **Always make it clear what the option is about** via `data-label`. Don't just say "Option A/B" — say "Card Style" or "Layout Variant."
- **Every option must have a `data-desc`** that concisely explains the difference.
- **Remove the `design-options` wrapper** once the user picks a final option — replace it with just the chosen markup.
- If there is only one group, the group tabs are hidden automatically.
- **Do NOT screenshot each option individually.** The user can browse options themselves using the picker. After adding design options, take one screenshot to confirm they're working, then describe the options in text. Let the user explore them live.
