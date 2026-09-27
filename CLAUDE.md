# proven-group-web

Public corporate/marketing website for Proven Results Group, a Madrid-based
investment and operating group. Bilingual (Spanish/English) static site.

## Stack

- Plain HTML5 pages with inline `<style>`/`<script>` per page — no build
  step, no package manager, no JS/CSS framework.
- Google Fonts (Cormorant Garamond, IBM Plex Sans) loaded from the CDN.
- Deployed as a static site via GitHub Pages custom domain (see `CNAME`,
  `.nojekyll`).

## Structure

- `index.html`, `nosotros.html`, `vision-y-objetivos.html`, `valores.html`,
  `portfolio.html`, `inversiones.html`, `contacto.html` — top-level pages,
  one per route; each page carries its own copy of the header/nav/footer
  (no shared template or includes system).
- `404.html` — GitHub Pages custom 404.
- `assets/img/` — page imagery (JPG/SVG); `assets/aquafortus-intro-deck.pdf`
  — downloadable investor deck.
- `robots.txt`, `sitemap.xml`, `CNAME`, `.nojekyll` — GitHub Pages/SEO config.

## Conventions

- Bilingual copy is duplicated inline as
  `<span class="t-es">…</span><span class="t-en">…</span>`; the toggle is
  pure CSS/JS (`setLang()`), no i18n framework. Keep both spans in sync when
  editing copy.
- Nav links and footer markup are hand-copied into every page — when
  adding/removing a page or nav item, update it in all HTML files, not one.
- No linter/formatter is configured; match each file's existing inline-style,
  hand-minified CSS.
- The contact "form" builds a `mailto:` link in JS (`contacto.html`); there
  is no backend form handler.

## Sensitive areas (critical-reviewer before COMPLETE)

- `CNAME` — binds the GitHub Pages custom domain; an incorrect value takes
  the live site offline.
- `sitemap.xml`, `robots.txt`, and per-page `<meta>`/Open Graph tags —
  publicly visible, affect SEO and social link previews.

## Validation

- No automated build, lint, or test tooling is configured (unverified — no
  `package.json`, `Makefile`, or CI workflow found in the repo).
- Manual: open each edited `.html` file in a browser; check both `ES`/`EN`
  toggle states, the mobile burger menu, nav links, and that referenced
  images under `assets/img/` resolve.

## Engineering orchestration

@.claude/orchestration/POLICY.md
