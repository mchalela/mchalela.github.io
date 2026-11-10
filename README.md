# Portfolio site (Hugo + Blowfish)

Source for mchalela.github.io. Theme: [Blowfish](https://blowfish.page/).

## Run locally

Needs Hugo extended (0.150 or newer). The theme is a git submodule in `themes/blowfish`:

    git submodule update --init
    hugo server

Update the theme later with `git submodule update --remote --merge`.

## Layout

- `config/_default/` theme and site settings. `params.toml` holds the theme options; `layoutSwitcher` is off for the real site. Author links (GitHub, LinkedIn, Upwork, ORCID) and the site title are in `languages.en.toml`.
- `assets/css/schemes/solarpunk.css` custom colour scheme. `assets/css/custom.css` fonts, the wide layout for pages without a table of contents, the publications "first author" marker, the home page tools row and the header logo colours.
- `assets/img/logo.svg` header logo (the lens mark; colours come from custom.css). `static/favicon*` and the Android and Apple icons are the same mark in fixed colours. `assets/img/social-card.png` is the preview image for shared links.
- `assets/icons/` SVG icons for the tools row and the Upwork author link, mostly from Simple Icons with `fill="currentColor"`. Astropy is hand-drawn.
- `layouts/shortcodes/skills.html` the tools row on the home page: one `icon|Label` per line.
- `content/software/` packages and pipelines (problem, what I did, outcome; `_index.md` cascades the article settings), `content/publications/`, `content/teaching/`, `content/contact/`. The About text and the tools row live on the home page.
- `content/posts/` blog, hidden for now: its `_index.md` sets `build: render: never` and the Blog menu items are commented out in `menus.en.toml`. Reverse both to publish.
- `static/cv/` copies of the two CV PDFs linked from the contact page. Recopy them after rebuilding the LaTeX sources.
- `layouts/partials/comments.html` giscus comments, off site-wide (`showComments = false`). Fill in the repo and category ids from https://giscus.app when the blog goes live.
- `.github/workflows/hugo.yml` deploys to GitHub Pages on push to `main`.
