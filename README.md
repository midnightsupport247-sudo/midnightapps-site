# Midnight Apps — midnightapps.dev

The official website for **Midnight Apps**, the mobile application studio operated by
**Midnight Holdings LLC**.

> Midnight Apps is the public brand. Midnight Holdings LLC is the legal entity that owns
> and operates it.

**Live site:** <https://midnightapps.dev>

---

## What this repository is

A static, dependency-free website: plain HTML, one stylesheet, and one small JavaScript
file. There is no build step, no framework, no package manager, and no server. It is
served by GitHub Pages from the root of the `main` branch on the custom apex domain
`midnightapps.dev`.

**What it deliberately does not have:** analytics, cookies, advertising, tracking pixels,
third-party fonts, CDN requests, contact forms, accounts, or a backend of any kind. Every
byte the browser loads comes from this repository.

---

## Repository layout

```
/
├── index.html                Homepage — hero, studio, company, focus, apps, support, contact
├── 404.html                  Not-found page (served automatically by GitHub Pages)
├── privacy/index.html        Privacy policy for this website
├── terms/index.html          Terms of use for this website
├── support/index.html        Support page — how to get help, all by email
├── assets/
│   ├── css/styles.css        The single stylesheet for every page
│   ├── js/site.js            Mobile menu + reveal-on-scroll. Optional; site works without it
│   └── img/
│       ├── og-image.png      1200×630 social preview card
│       └── icon-512.png      512px app-style icon
├── favicon.svg               Primary favicon (vector crescent mark)
├── favicon.ico               Fallback favicon, 16/32/48/64px
├── apple-touch-icon.png      180px home-screen icon
├── robots.txt                Allows all crawlers, points at the sitemap
├── sitemap.xml               The four indexable URLs
├── CNAME                     Custom domain binding: midnightapps.dev
├── .nojekyll                 Serve files verbatim, skip Jekyll
├── .gitignore
└── README.md
```

Directory-style URLs (`/privacy/`) come from each folder containing an `index.html`.

---

## Pages

| Page | URL |
| --- | --- |
| Home | <https://midnightapps.dev/> |
| Support | <https://midnightapps.dev/support/> |
| Privacy Policy | <https://midnightapps.dev/privacy/> |
| Terms of Use | <https://midnightapps.dev/terms/> |

---

## Contact addresses used on the site

| Purpose | Address |
| --- | --- |
| Business, developer program, press | developer@midnightapps.dev |
| Customer support | support@midnightapps.dev |
| Legal and privacy | legal@midnightapps.dev |

These are `mailto:` links. There is no contact form anywhere on the site, by design.

---

## Editing

All links are **root-absolute** (`/privacy/`, `/assets/css/styles.css`). That is what the
apex domain needs, and it is what makes `404.html` work from any depth.

Because there is no build step and no templating, the header and footer markup is repeated
in each HTML file. **If you change navigation, the footer, or the brand mark, change it in
all five HTML files:** `index.html`, `404.html`, `privacy/index.html`, `terms/index.html`,
`support/index.html`.

Styling lives entirely in `assets/css/styles.css`. Colors are CSS custom properties in the
`:root` block at the top of that file.

### When adding a page

1. Create `new-page/index.html` by copying an existing page's structure.
2. Add it to the nav and footer in every HTML file.
3. Add its URL to `sitemap.xml` and to the table above.
4. Set `<link rel="canonical">` and the Open Graph `og:url` to the new address.

### When an app ships

The apps section of `index.html` and the app block on `support/index.html` both carry a
status pill reading **"In development — not yet released."** Do not remove that wording or
add a store link until the app is genuinely live and publicly downloadable.

---

## Testing locally

Serve the folder over HTTP rather than opening files directly — root-absolute links need a
server root to resolve against:

```powershell
python -m http.server 8080
```

Then open <http://localhost:8080/>. Check that every nav link resolves, that the layout
holds at ~375px wide, and that the pages still read correctly with JavaScript disabled.

---

## Deployment

GitHub Pages, from the **root of `main`**. Pushing to `main` redeploys automatically,
usually within a minute or two.

**Repository → Settings → Pages:** Source `Deploy from a branch`, Branch `main`,
Folder `/ (root)`, Custom domain `midnightapps.dev`, **Enforce HTTPS** enabled once the
certificate has been issued.

### DNS (apex + www)

At the domain's DNS provider:

```text
A      @      185.199.108.153
A      @      185.199.109.153
A      @      185.199.110.153
A      @      185.199.111.153
CNAME  www    <github-username>.github.io
```

**Do not delete MX, SPF, DKIM, or DMARC records.** Those carry email for the
`@midnightapps.dev` addresses; removing them silently breaks every contact link on the
site. Only remove conflicting *website* records (a parking A record, a redirect, or an
ALIAS on the apex).

---

## Rules for this repository

This repository is **public**. It must never contain:

- application source code, API keys, tokens, credentials, or `.env` files;
- signing keys, provisioning profiles, or keystores;
- private user data or support correspondence;
- the company's registered business address or other private business records — those stay
  in local documentation only, and `.gitignore` excludes `COMPANY-VERIFICATION.md` for that
  reason.

If a secret is ever committed here, treat it as compromised: rotate it, then remove it.

---

## Legal note

The privacy policy describes this website only. Each application has its own privacy policy
published with its store listing. The terms of use govern this website and are not the
end user licence agreement for any application.

The governing-law section of the terms refers to the state in which Midnight Holdings LLC
is organised without naming it. Have a licensed attorney confirm that clause, and the
limitation of liability, against the entity's actual state of formation before relying on
them.

---

**Midnight Apps** — mobile apps by **Midnight Holdings LLC**.
© 2026 Midnight Holdings LLC. All rights reserved.
