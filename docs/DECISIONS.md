# Personal Website — Decision Log

A record of key decisions made during planning, and the reasoning behind each.

---

### 1. No server / backend required

**Decision:** Fully static site — HTML, CSS, and static assets only.

**Why:** Every feature (social links, conference list, photo, contact form, and eventually newsletter) can be served as static files. Contact form uses Formspree. Newsletter signup will use a third-party embed (Buttondown or Resend).

---

### 2. Plain HTML/CSS over React + Vite

**Decision:** Use plain HTML and CSS instead of React, TypeScript, and Vite.

**Why:** Initially considered React since the owner is familiar with it. After critical review, determined that React adds overhead without proportional benefit for this use case:
- The site is mostly static content updated every 1-2 months
- React would require a `node_modules` directory with hundreds of packages to audit and maintain
- A build step (`npm install` + `npm run build`) can break after months of inactivity due to dependency drift
- As a cybersecurity professional and solo developer, minimizing attack surface and maintenance burden is a priority
- CSS — not the framework — determines visual design quality. Plain HTML/CSS looks identical to React output.
- If the site grows to need React (interactive features, many pages), migration takes an afternoon

---

### 3. CSS Modules / Tailwind not needed

**Decision:** Single plain CSS file with page-level `<style>` blocks.

**Why:** CSS Modules require a build tool. Tailwind adds dependencies and has had breaking upgrade paths. A shared CSS file with design tokens plus page-specific styles in `<style>` blocks is sufficient and has zero maintenance cost.

---

### 4. Roboto font via Google Fonts

**Decision:** Use Roboto, loaded via a `<link>` tag from Google Fonts.

**Why:** Owner requested Roboto. Google Fonts CDN is free, fast, and widely cached. Single `<link>` tag — no download or self-hosting needed.

---

### 5. GitHub Pages for hosting

**Decision:** Host on GitHub Pages with custom domain alexanderwilczek.com.

**Why:** Free hosting, free HTTPS (via Let's Encrypt), custom domain support at no cost, deploys directly from the repo.

---

### 6. Multi-page structure

**Decision:** Split into 4 pages — Home, Digital Nomad, My Story, Contact.

**Why:** Initially planned as single-page. Split to keep each page focused and reduce scroll depth. Home page highlights speaking (the primary content), while secondary content (travel photos, career story, contact) lives on dedicated pages. Shared nav bar provides consistent navigation across all pages.

---

### 7. Sunset the Public-Speaking repo

**Decision:** Conference data will live in the website HTML. The separate Public-Speaking repo will be sunsetted.

**Why:** No reason to maintain two sources of truth. The website becomes the canonical place for speaking history.

---

### 8. Newsletter — deferred

**Decision:** Newsletter signup will be added later. Provider will be Buttondown or Resend.

**Why:** Owner wants to focus on the core site first. When added, it will be a simple `<form>` embed — no backend code needed.

---

### 9. Formspree for contact form

**Decision:** Use Formspree as the contact form backend.

**Why:** Free tier handles low-volume submissions. No server-side code needed — just a `<form action>` pointing to Formspree's endpoint. Requires setting up a Formspree account and replacing the `YOUR_FORM_ID` placeholder.

---

### 10. WCAG AA contrast compliance

**Decision:** All text colors must pass WCAG AA contrast ratio (4.5:1 for normal text, 3:1 for large text) on all background states.

**Why:** Accessibility is non-negotiable. The muted color was adjusted from `#888` to `#5a5a5a` to pass AA on white, surface, and hover backgrounds. Full contrast audit documented in [STYLING.md](./STYLING.md).
