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

Custom domain (e.g. annotello.com): add it in the host's settings and create the DNS records they
show. For GitHub Pages also add a `CNAME` file containing the domain.

## Images
`./scripts/render-site-images.sh` regenerates `assets/*` with Annotello's own drawing code
(see `Tests/AnnotelloTests/MarketingAssets.swift`).
