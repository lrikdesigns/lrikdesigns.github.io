# CLAUDE.md

Portfolio landing page for Elrica M. Metayer, served by GitHub Pages at https://lrikdesigns.com.

## Layout

Everything served by Pages lives in `docs/`. Root files (`CLAUDE.md`, `README.md`, `LICENSE`,
`.gitignore`) are not published. Put anything meant for the site in `docs/`, and nothing else.

- `docs/index.html`: the whole site. One static page with inline CSS and no JavaScript.
- `docs/images/`: project card images (800x600 WebP, 4:3) cropped from the portfolio PDF, plus
  `og.jpg` (1200x630) for the Open Graph preview.
- `docs/files/ElricaMetayer_Portfolio.pdf`: the full portfolio. Project cards link into it with
  `#page=N`.
- `docs/CNAME`: holds the custom domain. Do not remove or edit it.
- `docs/.nojekyll`: makes Pages serve files as-is without a Jekyll build.
- `LICENSE`: all rights reserved. The content is not open source.
- `plans/`: local working notes, gitignored.

## Deployment

Pages builds from `main` at `/docs` (legacy branch build). Merging to `main` publishes the site.
There is no build step.

## Preview

The website files live in `docs/`, so serve that directory, not the repo root:

```sh
python3 -m http.server --directory docs
```

Run it from the repo root, open http://localhost:8000/, and check widths of 320 px, 768 px and
1280 px. The page must not scroll horizontally at 320 px.

## Conventions

- Keep the site static: no JavaScript, no analytics, no external scripts. Google Fonts (Montserrat
  600/700 and Open Sans 400/600) is the only external resource.
- Colors come from the CSS tokens on `:root`, which match the PDF branding. There is one light theme
  with black accent panels and no dark mode.
- Mustard (`--accent`, `#F6BE00`) fails WCAG AA as text on white. Use it only on black panels or as
  a decorative fill. Text on mustard uses `--ink`.
- Content comes from the PDF. The About paragraphs are copied word for word from page 2, including
  "10 + years of experience" with the spaces as the PDF has them. Do not invent facts about
  projects, roles or dates.
- Every `<img>` needs descriptive alt text, explicit `width` and `height`, and `loading="lazy"`.
- Keep the PDF size label on the buttons ("PDF, 6.7 MB") in sync if the PDF is replaced.
- Comment the CSS concisely and keep one section comment per block of HTML.

## Images

The images embedded in the PDF are 443 to 1329 px wide, so the cards use 800x600. To replace an
image, extract it with `pdfimages -j -f N -l N`, or render the page with `pdftoppm -r 200` when the
embedded image has a transparency mask. Crop to 4:3, resize to 800x600, and encode with
`magick ... -strip -quality 78 out.webp`. Do the extraction in a temporary directory outside the
repo. Keep total page weight, excluding the PDF, under 1 MB.
