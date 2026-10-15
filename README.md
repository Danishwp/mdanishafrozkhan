# Danish Afroz — static HTML portfolio

A complete, self-contained static website. No build step, no dependencies,
no server code. Open `index.html` and it works.

## Preview it

- **Double-click `index.html`** — works straight off your disk.
- Or serve it locally, which is closer to real hosting:

  ```bash
  cd danish-afroz-portfolio-html
  python3 -m http.server 8080
  # then open http://localhost:8080
  ```

## Put it online

Upload **everything inside this folder** to your host's public directory
(`public_html`, `www`, `dist`, ...). That is the whole process.

Works as-is on Netlify, Cloudflare Pages, Vercel, GitHub Pages (drag-and-drop
the folder) and any cPanel/FTP host.

Every path inside is relative, so it also works in a sub-directory such as
`https://example.com/portfolio/` with no configuration.

## What is in here

```
index.html          home
about/index.html    about
services/index.html services and pricing
wordpress/index.html 25 WordPress projects
shopify/index.html   3 Shopify stores
contact/index.html  contact form
404.html            not-found page
_astro/             stylesheet + self-hosted font files
images/             brand and project screenshots (WebP)
favicon.svg  apple-touch-icon.png  icon-192.png  icon-512.png
site.webmanifest    app icons
og-default.png      1200x630 social sharing card
sitemap.xml  robots.txt
```

## Editing

| What | Where |
| --- | --- |
| Contact details, prices, copy | the relevant `index.html` |
| Colours, spacing, typography | `_astro/about.*.css` -> the `:root` block at the top |
| Project screenshots | `images/projects/` |
| Your photo | `images/brand/danish-afroz.webp` |

The contact form composes the message and opens WhatsApp with it — there is
no server involved, so it keeps working on any host.

## One thing to change if you move domain

The `<link rel="canonical">`, `og:url`, `og:image`, `twitter:image` tags and
`sitemap.xml` still point at https://danishafroz.42web.io. If you host this
somewhere else, search-and-replace that string:

```bash
grep -rl 'https://danishafroz.42web.io' . | xargs sed -i 's|https://danishafroz.42web.io|https://your-domain.com|g'
```

## Notes

- Trailing slashes are gone: pages are plain `/about/index.html` files, so
  nothing depends on server rewrite rules.
- `.nojekyll` is present for GitHub Pages, which would otherwise ignore the
  `_astro` folder because it starts with an underscore.
