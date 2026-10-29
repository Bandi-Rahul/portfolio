# Portfolio

Source for [rahulbandi.com](https://rahulbandi.com). A static site with no build step: plain HTML, CSS and a small script.

## Run it locally

```sh
python -m http.server 4173
```

Then open <http://localhost:4173>. Any static file server works.

## Structure

| Path | What it is |
| --- | --- |
| `index.html` | All the content and the SEO/social metadata |
| `style.css` | Design tokens (colour, type, spacing) at the top, then one block per section |
| `script.js` | Theme toggle and mobile menu |
| `assets/fonts/` | Self-hosted Newsreader and JetBrains Mono (latin subset, woff2) |
| `assets/certificates/` | Certificate PDFs linked from the Recognition section |
| `assets/og.png` | 1200x630 social preview image |
| `Rahul_Bandi_Resume.pdf` | Resume linked from the hero and contact sections |
| `robots.txt`, `sitemap.xml` | Crawler files. Update `lastmod` in the sitemap when the content changes |

## Editing

- **Colours and fonts** live in the `:root` and `[data-theme="dark"]` blocks at the top of `style.css`.
- **Numbers on the page** (builds triaged, eval score and so on) are plain text in `index.html`. Search for the number to update it.
- **Resume**: replace `Rahul_Bandi_Resume.pdf` in place. Keep the file name, since the page links to it.
- **Photo**: replace `assets/rahul.webp`. Use a transparent-background cut-out about 560px wide; the page sets the background colour behind it.

## Deploy

The site is served by GitHub Pages from the `main` branch root, with the custom domain in `CNAME`. Merging to `main` publishes it.

## Checks

GitHub Actions runs two jobs on every push to `main` and every pull request (`.github/workflows/checks.yml`):

- **Validate HTML** with `html-validate` (config in `.htmlvalidate.json`).
- **Lighthouse budget** with `@lhci/cli` (thresholds in `lighthouserc.json`: performance and best practices 90+, accessibility and SEO 95+, layout shift under 0.1).

Run the same checks locally:

```sh
npx html-validate index.html 404.html
npx @lhci/cli autorun
```

Also worth a look before merging: the mobile menu, the theme toggle, keyboard navigation, and no horizontal scroll at 360px wide.

## Notes

- A `Content-Security-Policy` meta tag restricts the page to its own files, so there are no inline scripts or styles. Keep it that way, or update the policy in `index.html` and `404.html`.
- With JavaScript off, the nav shows as a normal row of links and the theme button is hidden.
- `404.html` is served by GitHub Pages for unknown URLs.
