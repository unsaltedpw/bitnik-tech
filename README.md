# bitnik-tech

The "coming soon" landing page for `bitnik.tech`, the public site for Bitnik
LLC (Woodfin, NC), the company behind [Planeshift](../planeshift). It is a
single static page — `index.html` plus the assets in `assets/` — with no
build step and no server-side code.

## How it is served

GitHub Pages serves this repo's `main` branch from the repository root. The
Pages site, the repo itself, and its deploy key are declared in `platform`
(`platform/github.tf`: `module.bitnik_tech_repo` and
`github_repository_pages.bitnik_tech`) — change them with a pull request
there, never in GitHub's settings UI. `CNAME` at the repo root names the
custom domain (`bitnik.tech`); it is committed here because Pages expects it
in the served branch, but the domain itself is DNS, not a Pages setting.

## Domain

`bitnik.tech`'s DNS zone — its address records and the `brad@bitnik.tech`
email forwarding — is declared in `platform/projects/bitnik-tech/` (a
Cloudflare zone, moved there from Namecheap's registrar DNS on 2026-09-20
once the zone grew past a thing Namecheap's own UI could hold). Change DNS
there, not in a registrar or Cloudflare console.

Verified 2026-10-01: `dig +short bitnik.tech A` returns the four GitHub Pages
addresses, `NS` returns Cloudflare's nameservers, and `https://bitnik.tech/`
serves this page with a `200` from GitHub.com. The domain resolves and the
page is live.

## Changing the page

Edit `index.html` or `assets/`, push to `main`, and GitHub Pages republishes
within a few minutes — no separate deploy step.
