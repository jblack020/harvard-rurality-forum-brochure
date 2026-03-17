# HURL Design Style Guide

## Brand Colors

| Role        | Color     | Usage                                      |
|-------------|-----------|---------------------------------------------|
| Primary     | `#7F3708` | Buttons, links, accents, interactive elements |
| Background  | `#F5F0EA` | Page and section backgrounds                |
| Secondary   | `#111827` | Body text, headings, general typography     |

## Logo

- **Main logo:** `images/hurl_white.png`
- The white version of the HURL logo is the primary logo asset.
- Use on dark or primary-colored backgrounds for best contrast.

## Typography

- **Default font:** Open Sauce Sans
- Font files are located in the `fonts/` directory.
- Variable font (woff2): `fonts/OpenSauceSansVF.woff2` / `fonts/OpenSauceSansVF-Italic.woff2`
- Static TTF weights are also available in `fonts/` (Regular, Medium, SemiBold, Bold, ExtraBold, Black, Light — plus italics).

### CSS @font-face Setup

```css
@font-face {
  font-family: 'Open Sauce Sans';
  src: url('./fonts/OpenSauceSansVF.woff2') format('woff2-variations');
  font-weight: 100 900;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Open Sauce Sans';
  src: url('./fonts/OpenSauceSansVF-Italic.woff2') format('woff2-variations');
  font-weight: 100 900;
  font-style: italic;
  font-display: swap;
}
```

### Font Usage

```css
body {
  font-family: 'Open Sauce Sans', system-ui, -apple-system, sans-serif;
  color: #111827;
  background-color: #F5F0EA;
}
```

## General Guidelines

- Use the **primary color** (`#7F3708`) sparingly for emphasis — buttons, active states, links, and key UI accents.
- Use the **background color** (`#F5F0EA`) as the default page/section background.
- Use the **secondary color** (`#111827`) for all body text and headings.
- Always use **Open Sauce Sans** as the default typeface. Fall back to `system-ui` if unavailable.
