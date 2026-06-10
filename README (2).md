# downnow.cloud

Executor status tracker. Hosted on GitHub Pages at downnow.cloud.

## Setup

1. Push this repo to GitHub (e.g. `your-org/downnow-cloud`)
2. Go to **Settings → Pages → Source**: deploy from `main` branch, root `/`
3. Under **Custom domain**, enter `downnow.cloud` and hit Save
4. At your DNS provider, add:
   - `A` records pointing to GitHub's IPs: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Or a `CNAME` record: `www` → `your-org.github.io`
5. Enable **Enforce HTTPS** once the cert provisions (a few minutes)

## Custom 404

`404.html` is served by GitHub Pages for any path that doesn't exist (e.g. `downnow.cloud/e`).
It shows our branded page instead of GitHub's default.

## Bot API

All status updates live in `localStorage` client-side by default.
To wire up a real backend, replace the `API.*` functions in `index.html`
with `fetch()` calls to your own server (Cloudflare Worker, Railway, etc.)

Demo console commands:
```js
API.updateStatus('xeno-status', 'offline', 'demo-key-change-me')
API.bulkUpdate([{name:'volt-status',status:'shutdown'}], 'demo-key-change-me')
```
