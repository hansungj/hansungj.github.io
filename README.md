# hansungj.github.io

Personal site. Hand-written static HTML and CSS — no build step, no dependencies.

```
index.html               home: about, selected publications
publications/index.html  the full publication list
experience/index.html    experience and education
404.html
assets/css/main.css   all styling; colors live in the token block at the top
assets/img/           portrait.jpg, favicon.svg
assets/pdf/           paper PDFs
.github/workflows/deploy.yml
```

## Editing

Open `index.html` and edit it. Sections are marked with comment banners
(`<!-- ===== publications ===== -->`). Adding a publication means copying one
`.item` block and changing the text.

Two caveats of hand-written HTML with no templating:

- The top bar is duplicated across `index.html`, `publications/index.html`
  and `experience/index.html`. Edit all three when changing the nav.
- The four selected papers appear on both pages. Edit both when changing them.

Colors and type scale are CSS custom properties at the top of `main.css`.
Dark mode is a single `@media (prefers-color-scheme: dark)` block that
overrides only the color tokens.

## Preview locally

```
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Deploying

Push to `master`. The workflow copies the static files into `_site/` and
publishes them to the `gh-pages` branch, which GitHub Pages serves.

The stylesheet is linked as `main.css?v=dev`. At deploy time the workflow
replaces `dev` with a hash of the CSS contents, so browsers can never pair new
HTML with a stale cached stylesheet. Leave the `?v=dev` marker in place when
editing the HTML.
