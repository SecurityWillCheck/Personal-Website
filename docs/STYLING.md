# Personal Website — Styling Guide

Reference for all color, typography, and spacing decisions. Every page must follow these rules to maintain visual consistency.

---

## Color System

All colors are defined as CSS custom properties in `styles.css` under `:root`. Never use raw hex values in page-level styles — always reference a token.

| Token | Value | Contrast on White | Usage |
|---|---|---|---|
| `--color-primary` | `#111` | 18.9:1 (AAA) | Headings, names, conference titles, nav logo, buttons |
| `--color-body` | `#2a2a2a` | 14.7:1 (AAA) | Body text, paragraphs, bios, story content — the default reading color |
| `--color-secondary` | `#444` | 9.7:1 (AAA) | Supporting text, nav links, social links |
| `--color-muted` | `#5a5a5a` | 7.0:1 (AAA) | Locations, labels, section titles, footer text |
| `--color-border` | `#ddd` | — | Dividers, card borders, separators, nav border (decorative, not text) |
| `--color-surface` | `#f5f5f5` | — | Card/stat backgrounds, hover states use `--color-border` |
| `--color-bg` | `#fff` | — | Page background |

### When to use each color

- **Primary (`#111`)** — anything that needs to stand out as a heading or primary identifier. Conference names, page titles, your name.
- **Body (`#2a2a2a`)** — anything the visitor reads as continuous text. Bio, story paragraphs, talk titles, form inputs. Dark enough to read comfortably, softer than pure black to reduce eye strain. Passes WCAG AAA.
- **Secondary (`#444`)** — supporting information that's important but not the main focus. Nav links at rest, social link labels. Passes WCAG AAA.
- **Muted (`#5a5a5a`)** — metadata and chrome. Locations, "Upcoming"/"Past" labels, footer copyright, form labels. Passes WCAG AAA (7.0:1). Never use anything lighter for text.

### Upcoming talk cards

Upcoming talks use a dark background (`--color-upcoming-bg: #333`) with light text to visually separate them from past talks.

| Token | Value | Usage |
|---|---|---|
| `--color-upcoming-bg` | `#333` | Card background |
| `--color-upcoming-hover` | `#3d3d3d` | Card hover state |
| `--color-upcoming-text` | `#ccc` | Talk title text |
| `--color-upcoming-muted` | `#aaa` | Location text |

Conference name and date on upcoming cards use `--color-bg` (white).

---

## Typography

| Element | Font Size | Weight | Color Token |
|---|---|---|---|
| Page title / Name | `2rem` | 700 | `--color-primary` |
| Conference name | `1.25rem` | 700 | `--color-primary` |
| Body text / Bio | `1rem` | 300 | `--color-body` |
| Talk title | `0.9375rem` | 400 | `--color-body` (hover: inherits card) |
| Nav links | `0.8125rem` | 400 | `--color-secondary` (hover: `--color-primary`) |
| Social links | `0.8125rem` | 400 | `--color-secondary` (hover: `--color-primary`) |
| Stat numbers | `2rem` | 700 | `--color-primary` |
| Stat labels | `0.75rem` | 300 | `--color-secondary` |
| Section title | `0.75rem` uppercase | 400 | `--color-muted` |
| Subsection label | `0.6875rem` uppercase | 500 | `--color-muted` |
| Talk dates | `0.8125rem` | 400 | `--color-body` |
| Locations | `0.8125rem` | 400 | `--color-muted` |
| Form labels | `0.75rem` uppercase | 500 | `--color-muted` |
| Footer | `0.75rem` | 400 | `--color-muted` |

**Font family:** Roboto via Google Fonts (`300, 400, 500, 700` weights loaded).

**Line heights:**
- Body text / paragraphs: `1.8`–`1.9`
- Headings: `1.1`–`1.3`
- Base: `1.6`

---

## Spacing

| Property | Value |
|---|---|
| Page padding (desktop) | `2rem` |
| Page padding (mobile) | `1.5rem` |
| Max content width | `760px` |
| Nav content width | `760px` (same as `--max-width`, border extends full-width) |
| Section gap | `3rem`–`4rem` |
| Card padding | `2rem 2.5rem` (mobile: `1.5rem`) |
| Card gap | `1rem` |

---

## Components

### Talk cards
- Background: `--color-surface`
- Hover: `--color-border`
- Conference name: `--color-primary`, bold
- Talk title: `--color-body`, regular weight
- Date: `--color-body`, regular weight
- Location: `--color-muted`, light weight

### Subsection dividers
- Label: `--color-muted`, `0.6875rem`, uppercase, `letter-spacing: 2px`
- Line: `--color-border`, `1px`

### Upcoming talk cards
- Background: `--color-upcoming-bg`
- Hover: `--color-upcoming-hover`
- Conference name: `--color-bg` (white), bold
- Date: `--color-bg` (white)
- Talk title: `--color-upcoming-text`
- Location: `--color-upcoming-muted`

### Navigation
- Outer `.nav`: full-width, `border-bottom: 1px solid --color-border`
- Inner `.nav__inner`: constrained to `--max-width`, centered
- Logo: `--color-primary`, bold
- Links: `--color-secondary`, underline on hover/active

---

## Rules

1. **Never use raw hex values** in page-level `<style>` blocks. Always use a `--color-*` token.
2. **Body text is `--color-body`** (`#2a2a2a`), not `--color-primary`. Primary is for headings only.
3. **Metadata is `--color-muted`** (`#5a5a5a`). If the text is a location, label, or caption, it's muted. Dates use `--color-body`.
4. **Supporting text is `--color-secondary`** (`#444`). Nav links, social labels.
5. **Font weight 300** (light) is used for body text and descriptions. **700** (bold) for headings and emphasis only.
6. **All pages** link the shared `styles.css` first, then add page-specific styles in a `<style>` block.
7. **Mobile breakpoint** is `768px`. Use `var(--page-padding)` which adjusts automatically.
