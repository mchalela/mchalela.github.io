# Portfolio site (Hugo + Blowfish)

Source for mchalela.github.io. Theme: [Blowfish](https://blowfish.page/).

## Run locally

Needs Hugo extended (0.150 or newer). The theme is a git submodule in `themes/blowfish`:

    git submodule update --init
    hugo server

Update the theme later with `git submodule update --remote --merge`.

## Layout

- `config/_default/` theme and site settings. `params.toml` has `layoutSwitcher = true` for testing; turn it off for the real site.
- `assets/css/schemes/solarpunk.css` custom colour scheme. `assets/css/custom.css` fonts.
- `content/software/` packages and pipelines, `content/publications/`, `content/teaching/`, `content/posts/` blog, `content/contact/` services pitch and links. The About text lives on the home page.
- `layouts/partials/comments.html` giscus comments. Fill in the repo and category ids from https://giscus.app.
- `.github/workflows/hugo.yml` deploys to GitHub Pages on push to `main`.
