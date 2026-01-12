# Guidance for AI coding agents

Purpose: quick orientation so an AI can safely and productively edit this repo (static personal website).

- Repo type: single-page static site built from the HTML5 UP "Dimension" template.
- Primary files: `index.html` (site content), `assets/css/main.css` (compiled styles), `assets/js/main.js` (site behaviour), `assets/sass/` (Sass sources), and `images/` (media).

Big picture
- No backend or tests: this is a static site. Edits are usually content (HTML), styles (Sass → compiled CSS), or static assets (images, fonts, JS).
- The HTML references compiled CSS in `assets/css/main.css`. The Sass source is under `assets/sass/` but CSS is already compiled — update the compiled CSS when changing Sass.

Key files & patterns
- `index.html`: single-page content, Turkish copy. Modify for content updates (profile, videos, embeds).
- `assets/sass/main.scss` and subfolders: canonical source for styles. If you change SCSS, compile to `assets/css/main.css`.
- `assets/js/main.js`: primary site script (slideshow, simple UI). Third-party libs are checked in (`jquery.min.js`, `breakpoints.min.js`).
- `images/` and `images/wp/`: slideshow and site images (prefer .webp where present). Keep filenames and directory structure intact when updating references.
- `LICENSE.txt`: template license (HTML5 UP). Preserve design credit in footer.

Build / local dev (how to test changes)
- Serve locally to test: run a static server at repo root and open `index.html`:
```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```
- Compile Sass to the compiled CSS used by `index.html` (if editing `.scss`):
```bash
# requires Dart Sass
sass assets/sass/main.scss assets/css/main.css
```

Project-specific conventions
- Edits to styling should update the Sass source when possible and then compile to `assets/css/main.css`. Direct edits to `assets/css/main.css` are acceptable for quick fixes but will be overwritten if Sass is recompiled.
- Keep external embed IDs and analytics (Google Analytics UA string) unless explicitly asked to remove them; they are intentional site integrations.
- Content is in Turkish — preserve encoding (UTF-8) and existing punctuation/spacing.

External integrations to be aware of
- Google Analytics snippet (top of `index.html`).
- YouTube iframes and Sketchfab 3D embed in `index.html` (no server-side changes required to maintain these).
- Contact form uses Formspree action URL — changing the form action will alter where submissions go.
- Google Maps embed iframe in contact section.

Editing examples
- To change the hero title: edit `index.html` heading block (the `<h1>` inside the header).
- To add a new video embed: add an `<h3>` title and an `<iframe>` in the Intro article in `index.html`.
- To update slideshow images: put image files in `images/wp/` and update the corresponding `<img src="...">` entries in `index.html`.

Safety / policy notes for AI agents
- Do not remove or alter the HTML5 UP design credit in the footer (license requirement).
- Preserve analytics IDs, embed URLs, and third-party links unless the repo owner asks for removal.
- Keep commits small and content-focused; this is a personal site with minimal automation.

If anything is unclear (preferred Sass workflow, whether to keep compiled CSS changes or only update SCSS), ask the repo owner for clarification before large refactors.

---
Please review — tell me what else you'd like the instructions to cover (deploy steps, preferred Sass toolchain, or commit style).
