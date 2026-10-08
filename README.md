# gha-demo-site

The Pages half of a GitHub Actions demo. This repo holds no real data. **Deploy site** pulls it from **gha-demo-data** at deploy time:

1. Triggered by `repository_dispatch` (`data-updated`) from the data repo, or run by hand.
2. Downloads the **stats-json** artifact straight from the data repo's run (`repository` + `run-id` + `github-token`).
3. Packs `site/` with `upload-pages-artifact` and publishes it with `deploy-pages`.

`site/data/stats.json` is sample data. It goes live only until the first green data run exists.

Setup: Settings → Pages → Source: **GitHub Actions**, plus a `CROSS_REPO_TOKEN` secret (the same token as the data repo).

Preview locally: `python -m http.server -d site 8000`, then open http://localhost:8000.
