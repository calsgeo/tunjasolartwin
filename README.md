# Tunja Solar Twin test site

This repository contains the built static viewer for GitHub Pages. It does not need a Node server after deployment. The site must be published at the root of a domain or subdomain because Cesium and the PMTiles basemap use root-relative URLs.

## Publish with GitHub Pages

The `main` branch is published automatically by [`.github/workflows/pages.yml`](.github/workflows/pages.yml) after each push. The workflow validates and deploys the static site files from this repository; it does not build the viewer source project.

To refresh the built site, run this from the `solar_twin` source project after installing dependencies with `npm ci`:

```sh
python scripts/publish_github_pages.py --publish-repo "/path/to/tunjasolartwin"
```

The script runs the production build and copies the generated viewer files into this checkout. It does not commit or push. Review the changes, then commit and push them to `main` to trigger deployment. In GitHub, set **Settings → Pages → Build and deployment → Source** to **GitHub Actions**.

For a custom subdomain, set it under **Custom domain** in the Pages settings. In Squarespace DNS, add a `CNAME` record pointing to `calsgeo.github.io`. Once DNS has resolved, enable **Enforce HTTPS**.

The site is publicly accessible after publication, including its `data/` files. Confirm that prepared research data and map extracts may be shared publicly before pushing.

## Contents and updates

The deployable files are `index.html`, `assets/`, `cesiumStatic/`, `basemap/`, and `data/`. The `data.old/` and `data_corrected/` backup folders from the source project's `public/` directory are intentionally excluded. `.nojekyll` tells GitHub Pages to serve the files without Jekyll processing.

Use `scripts/publish_github_pages.py` from the source project to refresh these generated files. It updates only `index.html`, `assets/`, `cesiumStatic/`, `basemap/`, and `data/`; it preserves the repository documentation and settings and excludes backup folders from the source project `public/` directory. Keep `README.md`, `LICENSE`, `.nojekyll`, and `CNAME` in this repository.

`LICENSE` covers the viewer software (MIT). The prepared data and PMTiles basemap have separate provenance and licensing requirements; see the source project's `data_release/README.md` and `basemap/README.md`.
