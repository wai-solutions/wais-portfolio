# WAI-S — Branding & Brand Experience Portfolio

An interactive, single-page parallax portfolio for **WAI-S (WAI-Solutions)**, a branding
and brand experience agency.

**Zero build step. Zero dependencies.** It is one HTML file plus an image folder — open
it, or drop it on any static host.

---

## Quick start

Any static file server works. From the project root:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

> Opening `index.html` directly with `file://` mostly works, but serve it over HTTP so
> relative asset paths and the Google Fonts request behave exactly as they will in
> production.

---

## Deploying

The site is fully static — no build, no server runtime, no environment variables.

| Host | How |
|---|---|
| **Netlify** | Drag the folder onto the dashboard, or connect the repo. Publish directory: `/` — leave the build command empty. |
| **Vercel** | Import the repo, framework preset **Other**, leave build & output settings empty. |
| **GitHub Pages** | Settings → Pages → deploy from branch `main`, folder `/ (root)`. |
| **Cloudflare Pages** | Connect the repo, build command empty, output directory `/`. |
| **Any shared host** | Upload `index.html`, `assets/`, `robots.txt`, `sitemap.xml` to the web root. |

### Required after you deploy

The SEO metadata is written for the canonical domain **`https://wai-s.com/`**. If you
deploy anywhere else, update that URL in these places or search engines will index the
wrong address:

1. `index.html` — `<link rel="canonical">`
2. `index.html` — `og:url`, `og:image`, `twitter:image`
3. `index.html` — the `@id` and `url` fields in the JSON-LD block
4. `robots.txt` — the `Sitemap:` line
5. `sitemap.xml` — `<loc>` and `<image:loc>`

There is a comment block at the top of `<head>` in `index.html` listing exactly these.

---

## Structure

```
index.html        The entire site — markup, CSS and JS in one file
assets/           Optimised backgrounds, logos and brand artwork (~1.5 MB total)
robots.txt        Crawl rules, including AI/answer-engine bots
sitemap.xml       Single-page sitemap
```

---

## What's in the page

**14 sections** from the company profile, in the order of the original deck: hero,
focus, philosophy, what we do, the three service pillars (Branding & Strategy /
Identity & Brand Experience / Brand Scale & Sustain), how we execute, impact,
WAI-Solutions, portfolio, why WAI-S, partners and contact — plus a white statement
divider between sections.

**Interaction**

- Scroll-linked parallax on backgrounds, clamped so layers can never overlap content
- Reveal-on-scroll animations, staggered per section
- Animated SVG ripple diagram and philosophy rings
- Count-up statistics (97%, 5X, 33%, 25+)
- Section progress bar and labelled dot navigation
- Mouse-parallax and particle field in the hero
- Swipeable card carousels on mobile with tappable progress dots

**Accessibility & robustness**

- Fully responsive; carousels replace stacked cards below 980px
- Honours `prefers-reduced-motion` (animation, parallax and smooth scrolling all stop)
- Visible keyboard focus states
- `<noscript>` fallback so content is readable with JavaScript disabled
- Every `mailto:` button falls back to copying the address if the browser blocks it
  (common in WhatsApp / Instagram in-app browsers)

**SEO / AEO**

Open Graph and Twitter cards, canonical URL, and JSON-LD structured data covering
`Organization`, `WebSite`, `WebPage`, a 25-service `OfferCatalog`, and a 6-question
`FAQPage` for rich results and AI answer engines.

---

## Browser support

Current Chrome, Safari, Firefox and Edge, on desktop and mobile. Uses
`IntersectionObserver`, CSS scroll-snap, `background-clip: text` and CSS custom
properties — all broadly supported. No polyfills, no external JS.

---

## Not included in this repo

Deliberately excluded (see `.gitignore`):

- The print-resolution `@2x` brand source files (~13 MB)
- The original company-profile PDF (~24 MB)

The site needs neither. Ask WAI-S if you need the design sources.

---

## Contact

**marketing@wai-s.com** · [wai-s.com](https://wai-s.com) · /WeAreWAIS

---

© WAI-S (WAI-Solutions). The code in this repository may be used to host and deploy
this site. All brand assets — the WAI-S name, logo, imagery, copy and the client
logos shown in the Partners section — remain the property of their respective owners
and are **not** licensed for reuse.
