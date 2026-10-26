# makevention.org

Source for the Makevention website. It is a static site built with [Hugo](https://gohugo.io) and published with GitHub Pages. Content is edited in the browser with [Pages CMS](https://pagescms.org). Editors should read **[EDITING.md](EDITING.md)**.

## How it fits together

```
staging branch ──push──▶ Deploy workflow ──▶ gh-pages:/preview/   (preview copy, noindex)
main branch    ──push──▶ Deploy workflow ──▶ gh-pages:/           (live site)
"Publish preview to live site" workflow: merges staging → main, rebuilds both
```

- `content/*.md`: one file per page. Page content is a list of blocks in the front matter (`sections:`), rendered by `layouts/_partials/sections/<type>.html`.
- `data/site.yml`, `data/navigation.yml` and `data/sponsors.yml` hold site-wide settings, the menu, and the sponsor tiers shown on Home and Sponsors.
- `assets/css/main.css` holds all styling, matched to the old WordPress Neve theme.
- `static/wp-content/uploads/`: files from the old WordPress site, kept at their original URLs so existing links keep working.
- `static/uploads/` is where new uploads from Pages CMS go.
- `.pages.yml` configures the Pages CMS editor.
- `.github/workflows/` contains `deploy.yml` (on push), `publish.yml` (preview → live) and `build-deploy.yml` (shared build and publish steps).

Root-relative links (`/sponsors/`, `/wp-content/...`) are rewritten at build time, so the same content works at the live root, under `/preview/`, and at a `github.io/<repo>/` address.

## Working on it locally

```sh
hugo server          # http://localhost:1313, rebuilds as you edit
```

Install Hugo from <https://gohugo.io/installation/>. The workflows pin the version, currently 0.160.0.

## GitHub settings this relies on

- **Settings → Pages**: Source **Deploy from a branch**, branch `gh-pages`, folder `/ (root)`.
- **Settings → General → Default branch**: `staging`, so Pages CMS opens the preview branch by default.
- **Settings → Actions → General → Workflow permissions**: Read and write.

## Pointing www.makevention.org here (cut-over)

Do this only after the preview has been approved.

1. In **Settings → Pages → Custom domain**, enter `www.makevention.org` and save. GitHub adds a `CNAME` file to `gh-pages`, and the deploy keeps it.
2. At the DNS provider:
   - `www` → **CNAME** to `sherman617.github.io`.
   - Apex `makevention.org` → **A** records `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`. Optionally add AAAA records `2606:50c0:8000::153`, `…8001::153`, `…8002::153`, `…8003::153`.
   - Leave the **MX** and other mail records untouched.
3. Once the certificate is issued, tick **Enforce HTTPS**.
4. Run the **Deploy** workflow on `main` and `staging` once, so both copies are rebuilt with the new address.
5. Keep the WordPress site until the new one has been live for a while.
