# Personal Website — Design Considerations

## Owner

- **Name:** Alexander Wilczek
- **Domain:** alexanderwilczek.com
- **Focus:** Cybersecurity professional, public speaker

## Visual Theme

- **Color palette:** Black and white — minimal, high contrast. See [STYLING.md](./STYLING.md) for the full color token system.
- **Aesthetic:** Clean, minimalist — content-first, no visual clutter
- **Font:** Roboto (loaded via Google Fonts `<link>` tag, weights 300/400/500/700)
- **Layout:** Multi-page with shared nav, responsive (mobile + desktop)
- **Profile photo:** `images/IMG_1276.JPG` — outdoor headshot, displayed on home page hero

## Pages

1. **Home (`index.html`)** — hero (photo, name, bio, social links) + speaking section (upcoming/past with embedded YouTube)
2. **Digital Nomad (`digital-nomad.html`)** — travel photo gallery with captioned dividers + setup video
3. **My Story (`my-story.html`)** — quick stats + career backstory
4. **Contact (`contact.html`)** — contact form (Formspree) + social links in footer
5. **Newsletter** — deferred (planned: Buttondown embed)

## Principles

- **Lightweight** — fast load times, zero dependencies
- **Smart, secure, neat code** — senior-level quality, no shortcuts
- **Simple to maintain** — edit HTML directly, push, done
- **Zero build step** — no tooling that can break while you're away
- **Solo developer friendly** — everything should be obvious to edit after months away
- **Reusable components** — common UI patterns (cards, links, sections) built as reusable CSS classes
- **Best practice development** — semantic HTML, accessible markup, mobile-first responsive CSS, consistent naming conventions, DRY code. See [ARCHITECTURE.md](./ARCHITECTURE.md) for full details.
