# Portfolio Site

Static portfolio page (builder export). No backend, no build step.

## Structure

- `site/` — the published folder (this is what Netlify serves)
  - `index.html` — the page
  - `support.js` — builder runtime (loads React + Babel from unpkg at runtime)
  - `assets/` — referenced images
- `uploads/`, `screenshots/` — **private, never published** (excluded via `.gitignore` and kept outside `site/`)
- `netlify.toml` — publish dir + security headers

## Deploy to Netlify

Option A — connect the repo (recommended):
1. Netlify → Add new site → Import from Git → pick `TFFy1/ProjectsPortfolio`.
2. Netlify reads `netlify.toml` automatically. Leave build command empty; publish dir is `site`.
3. Deploy. Every push to `main` redeploys.

Option B — manual: drag the `site/` folder into the Netlify dashboard.

## Notes

- Security headers (CSP, HSTS, nosniff, frame/referrer/permissions policy) are set in `netlify.toml`.
- The CSP allows `unsafe-eval` because the page transpiles JSX in-browser via Babel. To tighten it, pre-bundle the JS instead of loading React/Babel from unpkg at runtime.
