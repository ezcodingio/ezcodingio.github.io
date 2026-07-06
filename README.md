# ezcoding.io

Company website for EasyCoding, built with [Hugo](https://gohugo.io/) and deployed to GitHub Pages.

## Development

```sh
hugo server          # live-reload dev server at http://localhost:1313
hugo --gc --minify   # production build into ./public
```

Site copy lives in `data/*.yaml` (services, client engagements) and `hugo.toml` (`[params]`).
Layouts are hand-rolled (no theme) in `layouts/`, styling in `assets/css/main.css`.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds the site and
publishes it via GitHub Pages (repo Settings → Pages → Source: **GitHub Actions**).

### Custom domain (ezcoding.io)

`static/CNAME` keeps the custom domain pinned across deploys. DNS records at the registrar:

| Host | Type  | Value |
|------|-------|-------|
| `@`  | A     | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| `@`  | AAAA  | `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153` |
| `www`| CNAME | `ezcodingio.github.io` |

(If the DNS provider supports ALIAS/ANAME at the apex, a single `@ ALIAS ezcodingio.github.io`
replaces the A/AAAA sets.)

After DNS propagates: repo Settings → Pages → tick **Enforce HTTPS** (cert issuance can take
a few hours). Also verify the domain at the org level (Org Settings → Verified domains).

### Email

`contact@ezcoding.io` is published on the site and needs mail routing configured separately
(e.g. Cloudflare Email Routing or ImprovMX forwarding, plus an SPF record).
