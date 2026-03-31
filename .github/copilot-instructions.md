# Copilot instructions for `personal-pages-website`

## Project shape (Jekyll + Minima)
- This repo is a Jekyll site using `minima` (`Gemfile`, `_config.yml`).
- Source content lives at repo root and in collections; generated output is in `_site/`.
- Do not edit `_site/` files directly; change sources and rebuild.

## Content model and routing
- Standard posts are in `_posts/` and follow `YYYY-MM-DD-title.<ext>` naming.
- A custom `photos` collection is enabled in `_config.yml` with `output: true`.
- Photo collection entries live in `_photos/` and are surfaced on `/photos/` via `photos.md`.
- `photos.md` loops over `site.photos`:
  - `{% for post in site.photos %}` → links to each photo page.
- Keep front matter consistent with existing entries (e.g., `layout: post`, `title`, `date`).

## Reusable include pattern
- Use `_includes/external_photo.html` for externally hosted images.
- Existing usage pattern in `_posts/2025-06-08-photo.md`:
  - `{% include external_photo.html url="..." %}`
- Include supports `url` (required) and optional `caption`/`alt`.

## Editing conventions in this repo
- Prefer minimal Liquid + Markdown changes over theme overrides unless required.
- Keep permalink-driven pages as root markdown files (`about.markdown`, `photos.md`, `index.markdown`).
- If modifying `_config.yml`, restart `jekyll serve` (config is not hot-reloaded).
- Keep generated/cache paths untracked (`_site`, `.jekyll-cache`, `.sass-cache`, `.jekyll-metadata`, `vendor`).

## Local workflow (Ruby/Bundler)
- Install deps: `bundle install`
- Serve locally with rebuild/watch: `bundle exec jekyll serve`
- Default local URL is typically `http://127.0.0.1:4000`

## Agent-specific guardrails
- Before adding new structure, check whether the change fits:
  - root page (`*.markdown`/`*.md`),
  - `_posts/` blog post,
  - or `_photos/` photo collection item.
- When adding photo-heavy content, prefer the include (`external_photo.html`) over raw `<img>` duplication.
- Validate links and collection output by checking `/photos/` and the generated item page after serving.
