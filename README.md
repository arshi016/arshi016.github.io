# arshichadha.com

Personal website of Arshi Chadha — AI security researcher & PSIRT engineer.
Single-file static site (`index.html`) + `CNAME`, zero build step, zero dependencies.

The page reads as an unfolding agentic-AI incident (with a live T+ incident clock),
then pivots to the person who writes the playbook for what comes after.

## Deploy: GitHub Pages + custom domain (~10 min, mostly DNS waiting)

### 1. Push the site

Create a **public** repo named `<your-username>.github.io`, then:

```bash
git init
git add index.html CNAME README.md
git commit -m "arshichadha.com — launch ♞"
git branch -M main
git remote add origin git@github.com:<your-username>/<your-username>.github.io.git
git push -u origin main
```

(The `CNAME` file in the repo root tells GitHub Pages which domain to serve.
Don't delete it — GitHub also recreates it when you set the domain in Settings.)

### 2. Point DNS at GitHub Pages

At your registrar (Namecheap / Cloudflare / GoDaddy — wherever you bought
arshichadha.com), add these records:

| Type  | Host / Name | Value                        |
|-------|-------------|------------------------------|
| A     | `@`         | `185.199.108.153`            |
| A     | `@`         | `185.199.109.153`            |
| A     | `@`         | `185.199.110.153`            |
| A     | `@`         | `185.199.111.153`            |
| CNAME | `www`       | `<your-username>.github.io`  |

Optional but nice (IPv6):

| Type | Host | Value                  |
|------|------|------------------------|
| AAAA | `@`  | `2606:50c0:8000::153`  |
| AAAA | `@`  | `2606:50c0:8001::153`  |
| AAAA | `@`  | `2606:50c0:8002::153`  |
| AAAA | `@`  | `2606:50c0:8003::153`  |

> Cloudflare note: set the records to **DNS only** (grey cloud) at least until
> GitHub issues the TLS certificate; you can proxy afterwards if you want.

### 3. Tell GitHub about the domain

Repo → **Settings → Pages** → Custom domain: `arshichadha.com` → Save.
Wait for the DNS check to pass, then tick **Enforce HTTPS**.
Certificate provisioning is usually minutes, occasionally up to ~24h.

### 4. Verify

- `https://arshichadha.com` loads with a padlock
- `https://www.arshichadha.com` redirects to the apex
- `https://<your-username>.github.io` redirects to the domain

Recommended extra: GitHub **Settings → Pages → Verified domains** — verify
`arshichadha.com` so nobody can hijack the domain onto their own Pages site
if your DNS ever outlives the repo.

## Before you publish — edit checklist

Search `index.html` for these placeholders and replace:

- [ ] `YOUR-GITHUB` — GitHub username (links + JSON-LD)
- [ ] `YOUR-LINKEDIN` — LinkedIn handle
- [ ] `YOUR-TWITTER` — X/Twitter handle
- [ ] `YOUR-EMAIL@example.com` — real email (or delete the button)
- [ ] Patent citation count, talk dates, anything else you want to tune

## Notes

- Fonts: Fraunces, Spline Sans, Spline Sans Mono via Google Fonts; everything else inline.
- Fully responsive, keyboard-accessible, respects `prefers-reduced-motion`
  (the incident clock degrades gracefully).
- SEO ready: canonical URL, meta description, Open Graph tags, JSON-LD `Person`
  schema — all pointed at `arshichadha.com`.
- Easter egg in the browser console for fellow inspectors.
# arshichadha
