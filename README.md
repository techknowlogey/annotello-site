# Annotello website

Static site — no build step. `index.html`, `styles.css`, `assets/`, `downloads/` and `latest.json`.

## Publish a new version
1. Edit `VERSION` and `RELEASE_NOTES.md` in the project root.
2. `./scripts/release.sh` — builds the DMG, copies it to `downloads/`, rewrites `latest.json`.
   The download buttons, version, size, checksum and changelog on the page all read `latest.json`.
3. Preview: `./scripts/preview-site.sh` → http://localhost:8765
4. Deploy the `website/` folder (below).

## Hosting
Any static host works. The site is ~1 MB plus the ~5 MB DMG.
- **GitHub Pages** (free): push this folder to a repository and enable Pages (Settings › Pages).
- **Cloudflare Pages / Netlify** (free): drag the `website` folder into their dashboard.

Live at **https://annotello.com** (GitHub Pages, repo `techknowlogey/annotello-site`; DNS in Cloudflare:
CNAME `@` and `www` → `techknowlogey.github.io`, *DNS only*, plus the `_github-pages-challenge-techknowlogey`
TXT verification record). The `CNAME` file in this folder must stay — it tells GitHub Pages the domain.

## Images
`./scripts/render-site-images.sh` regenerates `assets/*` with Annotello's own drawing code
(see `Tests/AnnotelloTests/MarketingAssets.swift`).
