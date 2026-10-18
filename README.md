# lrikdesigns.github.io

Portfolio site for Elrica M. Metayer, architectural designer and urban design professional, served by
GitHub Pages at <https://lrikdesigns.com>.

GitHub Pages publishes only the `docs/` folder. Files at the repository root are not served.

- `docs/index.html` is the page, a single static file with inline CSS and no JavaScript.
- `docs/images/` holds the project images cropped from the portfolio PDF, plus `og.jpg` for link
  previews.
- `docs/files/ElricaMetayer_Portfolio.pdf` is the full portfolio linked from the page.
- `docs/CNAME` sets the custom domain, and `docs/.nojekyll` makes Pages serve the files as they are,
  without a Jekyll build.

The website files live in `docs/`. To preview locally, serve that directory from the repository
root and open <http://localhost:8000/>:

```sh
uv run python -m http.server --directory docs
```
