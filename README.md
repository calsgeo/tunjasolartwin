# Tunja Solar Twin test site

This repository contains the built static viewer for GitHub Pages. It does not need a Node server after deployment. The site must be published at the root of a domain or subdomain because Cesium and the PMTiles basemap use root-relative URLs.

## Publish with GitHub Pages

1. Commit and push the files in this repository.
2. In GitHub, open **Settings → Pages** and select **Deploy from a branch**, `main`, `/ (root)`.
3. If using a custom subdomain, enter it under **Custom domain** in the Pages settings. In Squarespace DNS, add a `CNAME` record for the subdomain pointing to `calsgeo.github.io`.
4. Once DNS has resolved, select **Enforce HTTPS** in GitHub Pages.

The site is publicly accessible after publication, including its `data/` files. Confirm that the prepared research data and map extract may be shared publicly before pushing.

## Contents and updates

The deployable files are `index.html`, `assets/`, `cesiumStatic/`, `basemap/`, and `data/`. The `data.old/` and `data_corrected/` backup folders from the source project's `public/` directory are intentionally excluded. `.nojekyll` tells GitHub Pages to serve the files without Jekyll processing.

Build updates in the `solar_twin` source project with `npm run build`, then replace the deployable files here with the new build output, excluding the backup folders. Keep `README.md`, `LICENSE`, and `.nojekyll` in this repository.

`LICENSE` covers the viewer software (MIT). The prepared data and PMTiles basemap have separate provenance and licensing requirements; see the source project's `data_release/README.md` and `basemap/README.md`.
