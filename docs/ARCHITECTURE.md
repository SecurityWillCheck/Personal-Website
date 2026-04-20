# Personal Website — Architecture

## Static / Frontend-Only

**Decision: No server required.** The entire site is built as static HTML/CSS.

| Feature | Approach |
|---|---|
| Social links | Static HTML |
| Conference list | Static HTML — edited directly when entries change |
| Profile photo | Static asset |
| Contact form | Formspree (third-party `<form>` action) |
| Newsletter signup | Deferred — Buttondown or Resend embed |

## Hosting

| Platform | Notes |
|---|---|
| **GitHub Pages** | Free, deploys from this repo, custom domain, free HTTPS |

- **Custom domain:** alexanderwilczek.com
- **HTTPS:** Free via Let's Encrypt (GitHub Pages provides this automatically)
- **Setup:** CNAME file in repo + DNS A/CNAME records pointing to GitHub

## Tech Stack

| Layer | Choice | Rationale |
|---|---|---|
| Markup | **Plain HTML** | Zero dependencies, zero build step, always works |
| Styling | **Plain CSS** | Single shared file + page-level `<style>` blocks |
| Hosting | **GitHub Pages** | Free, custom domain support, free HTTPS |
| Domain | **alexanderwilczek.com** | Custom domain, pointed at GitHub Pages |
| Contact form | **Formspree** | Serverless form handling, no backend needed |
| Newsletter | Deferred — Buttondown or Resend | Third-party embed, no backend needed |

## Site Structure

```
index.html          — Home: hero (photo, bio, socials) + speaking section
digital-nomad.html  — Travel photo gallery with captioned dividers
my-story.html       — Career stats + backstory
contact.html        — Contact form (Formspree) + social links
styles.css          — Shared CSS (tokens, nav, footer, socials, utilities)
images/             — Photos, favicon, OG image
docs/               — Project documentation
```

Each HTML page links the shared `styles.css` first, then adds page-specific styles in a `<style>` block in the `<head>`.

### Navigation

All pages share a consistent nav bar: `Speaking | Digital Nomad | My Story | Contact`. The nav uses a full-width border with content constrained to `--max-width`.

### JavaScript

Minimal JS on `index.html` only — auto-moves upcoming talks to the past section when their `data-date` has passed. No JS on other pages.

### Favicon & Open Graph

All pages include:
- `favicon-32-v2.png` — browser tab icon
- `favicon-180-v2.png` — Apple touch icon (filenames versioned to bust Google's favicon cache after an orientation fix)
- `og-image.png` — Open Graph / Twitter Card image for link previews

OG image URLs are relative and must be converted to absolute URLs when deploying with a custom domain.

## Maintainability

- **Zero dependencies** — nothing to audit, nothing to break
- **Single source of truth** — conference data lives in the website HTML
- **Clean, semantic HTML** — `<header>`, `<section>`, `<nav>`, `<footer>`, `<article>`
- **BEM-like naming** — `.talk__conference`, `.hero__photo`, `.form__input`
- **CSS custom properties** — change the theme in one place
- **Reusable components** — talk cards, social links, nav, footer follow repeatable patterns
- **Mobile-first** — base styles for mobile, `768px` breakpoint for desktop
