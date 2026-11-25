# Deploy — Grech Press storefront

Static, no build step, no external requests. Upload this directory as-is.

## Cloudflare Pages
1. Create a Pages project, connect the repo (or upload this folder via direct upload).
2. Build command: none. Output directory: `site/grechpress` (or the folder contents).
3. Set the custom domain to `grechpress.com`; Cloudflare issues TLS automatically.
4. Verify `https://grechpress.com/sitemap.xml` and submit it in Search Console.

## GitHub Pages
1. Copy this folder to a `gh-pages` branch root (or `/docs` and select it).
2. Repository → Settings → Pages → deploy from branch/folder.
3. Add `CNAME` with `grechpress.com` if using the custom domain.

## Netlify Drop
1. Zip this folder and drop it at app.netlify.com/drop.
2. Add the custom domain in Site settings → Domain management.

## Store gate — read this before deploying (2026-11-24)

**Concurrency warning:** a separate Grech OS agent process in this repo can rewrite this folder (observed 2026-11-24 01:06Z). Re-run the checks below immediately before deploying; the authoritative description of the verified storefront is `reports/store-truth-2026-11-24.md`.

**Do not deploy this folder until every card you keep is truthful about what a visitor can buy today.** The catalogue is honest but pre-launch:

- **5 paid titles are live** on Gumroad: off41 Index Funds, off42 ADHD at Work, off43 Career Change, off67 Overthinking, off76 Stoicism Without the Statue. The free Index Funds sample is live too.
- **6 titles are drafts**: off44–off49. Their cards say `data-store-state="draft"` and `Preview on Gumroad`; a draft page opens but cannot be bought.
- **25 titles are in preparation** (`data-store-state="planned"`). Their Gumroad links are the planned permalinks and will 404 until each product is created. Before deploying, either (a) create/publish those products, or (b) delete their cards and sitemap entries. This is a decision, not a default.
- Page counts and prices on the site come from `revenue/assets-v2/*/manifest.json` for the nine titles that have a v2 typeset build. Titles without a v2 build no longer claim a page count. Do not re-introduce the old v1 page counts (the 96/140 pair) or the old KDP 9.99 price line: those were v1 claims.
- **Do not run `node scripts/site-add-books.mjs`** until `revenue/marketing/offers.json` is updated: it regenerates cards from the stale v1 `spec.stats.pageCount` (96/140) and the old KDP price claim.

## Before/after launch checklist
- Replace the planned Gumroad product URLs (`https://grechsolutions.gumroad.com/l/<slug>`) with the real permalinks if the store handle changes; keep the UTM parameters.
- Confirm each Gumroad product is live, has the correct price and the sample file attached.
- Confirm `og-image.png` and all cover SVGs render on mobile.
- Submit `sitemap.xml` to Google/Bing; keep `robots.txt` allowing crawl.
- Check the affiliate links on each Gumroad product use the commission rate you approved.
- No analytics/trackers are included; if added later, update the privacy note and re-check weight.

## Weight
Total directory size was 317 KB on 2026-11-24 (measured after the store-truth pass), kept under 400 KB (covers are compact SVGs optimised from the 1600x2560 `deliverables/d2d/*/cover.png` files; one 59 KB OG image). No external fonts, CSS, JS, analytics or image CDNs.
