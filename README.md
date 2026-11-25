# Grech Press storefront

Static catalogue site for Grech Press (36 titles). No build step, no dependencies, no external requests.

- **Live (Netlify):** connect this repo at https://app.netlify.com/start → "Import from GitHub" → `grech-press-site`. `netlify.toml` already sets the publish directory, so no configuration is needed.
- **Live (GitHub Pages preview):** https://anotherrandomuser1234.github.io/grech-press-site/
- Prices shown are USD 9.99 direct (see `docs/PRICING-2026-11-25.md` in the main repo). Canonical/OG/sitemap still point at `grechpress.com`, which is not registered yet; they switch over when the domain is bought and the Netlify custom domain is set.

Source of truth: the main repo `X:\Projects\grech-consultancy\site\grechpress`. Deploy by copying that folder here, or connect Netlify directly to the main repo with base directory `site/grechpress`.
