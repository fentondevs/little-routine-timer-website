# Little Routine Timer — Website Final Pre-Deployment Build

A complete static website for the Little Routine Timer iOS app.
Ready to deploy to Cloudflare Pages.

> **Legal notice:** The Terms of Use (`terms.html`) are draft content and have not been reviewed or approved by a solicitor. Do not remove the draft warning until the terms have been reviewed.

---

## Confirmed details

| Detail | Value |
|---|---|
| App owner and publisher | Tom Fenton |
| Copyright | © 2026 Tom Fenton |
| Governing law (Terms) | England and Wales |
| Website domain | littleroutinetimer.com |
| General contact | hello@littleroutinetimer.com |
| Support contact | support@littleroutinetimer.com |
| Privacy contact | privacy@littleroutinetimer.com |

---

## Folder structure

```
little-routine-timer-website/
├── index.html              Homepage
├── privacy.html            Privacy Policy
├── support.html            Help & Support
├── terms.html              Terms of Use (DRAFT — requires legal review)
├── 404.html                Custom 404 page
├── robots.txt              Search engine instructions
├── sitemap.xml             Sitemap for search engines
├── _redirects              Cloudflare Pages clean URL rules
└── assets/
    ├── favicon.svg             SVG favicon — present
    ├── apple-touch-icon.png    Apple touch icon — 180×180 px — present
    ├── og-image.png            Open Graph image — 1200×630 px — present
    ├── home-screen.png         App screenshot — not yet supplied
    ├── active-routine.png      App screenshot — not yet supplied
    ├── parallel-routines.png   App screenshot — not yet supplied
    ├── routine-editor.png      App screenshot — not yet supplied
    ├── quick-timer.png         App screenshot — not yet supplied
    └── bedtime-mode.png        App screenshot — not yet supplied
```

---

## Remaining placeholders

Only four placeholders remain. Everything else is confirmed and filled in.

| Placeholder | Description | File |
|---|---|---|
| `[PRIVACY POLICY EFFECTIVE DATE]` | Date the policy comes into effect | privacy.html |
| `[TERMS EFFECTIVE DATE]` | Date the terms come into effect | terms.html |
| `[SITEMAP DATE]` | Deployment date in YYYY-MM-DD format | sitemap.xml |
| `[APP STORE URL]` | App Store link once approved by Apple | index.html (5 locations — comments only) |

No postal address placeholder remains. No email placeholder remains. No domain placeholder remains.

### Pricing

The planned launch price is shown as **£1.99** in `index.html`. Search for `UPDATE PRICING HERE` to find the exact location. Update the price and remove the "Planned launch price" notice once the App Store listing confirms it.

---

## How to add the App Store URL after approval

When Apple approves the app, search `index.html` for `[APP STORE URL]` — there are 5 locations, each with a comment explaining exactly what to change.

**Convert each pre-launch span to a live link:**

Before (pre-launch, non-clickable):
```html
<span class="appstore-btn btn-lg"
      aria-disabled="true"
      role="img"
      aria-label="Coming soon to the App Store">
  ...
  <span class="appstore-btn-small">Coming soon to the</span>
  <span class="appstore-btn-main">App Store</span>
  ...
</span>
```

After (live link):
```html
<a href="https://apps.apple.com/app/little-routine-timer/idXXXXXXXXXX"
   class="appstore-btn btn-lg"
   aria-label="Download Little Routine Timer on the App Store">
  ...
  <span class="appstore-btn-small">Download on the</span>
  <span class="appstore-btn-main">App Store</span>
  ...
</a>
```

Remove `aria-disabled="true"`, `role="img"`, and `style="cursor:default; ..."` from each converted link.

For the simpler button-style spans, replace:
```html
<span class="btn btn-primary" aria-disabled="true" ...>Coming soon to the App Store</span>
```
with:
```html
<a href="https://apps.apple.com/..." class="btn btn-primary" aria-label="Download Little Routine Timer on the App Store">Download on the App Store</a>
```

---

## Cloudflare Pages deployment

### Step 1 — Fill in remaining placeholders
Before deploying, set:
- `[PRIVACY POLICY EFFECTIVE DATE]` in `privacy.html`
- `[TERMS EFFECTIVE DATE]` in `terms.html`
- `[SITEMAP DATE]` in `sitemap.xml` (use deployment date in YYYY-MM-DD format)

### Step 2 — Create a GitHub repository
Create a new GitHub repository. Name it something like `little-routine-timer-website`.

### Step 3 — Upload all files
Upload the entire contents of this folder to the root of the repository, with `index.html` at the root.

### Step 4 — Connect to Cloudflare Pages
1. Sign in to [dash.cloudflare.com](https://dash.cloudflare.com)
2. Go to **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**
3. Authorise Cloudflare and select the repository

### Step 5 — Build settings (no build needed)

| Setting | Value |
|---|---|
| Framework preset | None |
| Build command | *(leave blank)* |
| Build output directory | `/` |

### Step 6 — Deploy
Click **Save and Deploy**.

### Step 7 — Add custom domain
1. In your Pages project, go to **Custom domains**
2. Add `littleroutinetimer.com`
3. Follow Cloudflare's DNS instructions
4. HTTPS is automatic

### Step 8 — Test all routes

| URL | Expected |
|---|---|
| `https://littleroutinetimer.com` | Homepage |
| `https://littleroutinetimer.com/privacy` | Privacy Policy (clean URL) |
| `https://littleroutinetimer.com/privacy.html` | Privacy Policy (direct) |
| `https://littleroutinetimer.com/support` | Support page (clean URL) |
| `https://littleroutinetimer.com/support.html` | Support page (direct) |
| `https://littleroutinetimer.com/terms` | Terms of Use (clean URL) |
| `https://littleroutinetimer.com/terms.html` | Terms of Use (direct) |
| `https://littleroutinetimer.com/this-does-not-exist` | Custom 404 page |
| `https://littleroutinetimer.com/assets/favicon.svg` | Favicon (accessible) |
| `https://littleroutinetimer.com/assets/og-image.png` | OG image (accessible) |

### Step 9 — Add the App Store URL
Once Apple approves the app, follow the instructions above to convert the pre-launch CTAs to live links.

---

## About the _redirects file

```
/privacy    /privacy.html    200
/support    /support.html    200
/terms      /terms.html      200
```

These serve clean URLs. The `200` code means the URL stays clean in the browser (a rewrite, not a redirect).

**There is no catch-all redirect.** This is intentional — Cloudflare Pages will automatically serve `404.html` for unknown URLs. Do not add `/* /index.html 200`.

---

## Pre-launch App Store CTA behaviour

All CTA buttons display "Coming soon to the App Store" as non-clickable `<span>` elements with `aria-disabled="true"` and no `href`. They will not jump users to the top of the page.

CSS in `index.html` ensures these spans have `pointer-events: none` and `cursor: default`.

Once the App Store URL is confirmed, follow the conversion instructions above.

---

## Screenshot asset checklist

| File | Dimensions | Status |
|---|---|---|
| `assets/favicon.svg` | Vector | ✅ Present |
| `assets/apple-touch-icon.png` | 180×180 px | ✅ Present |
| `assets/og-image.png` | 1200×630 px | ✅ Present |
| `assets/home-screen.png` | ~390×844 px recommended | ⏳ Not yet supplied |
| `assets/active-routine.png` | ~390×844 px recommended | ⏳ Not yet supplied |
| `assets/parallel-routines.png` | ~390×844 px recommended | ⏳ Not yet supplied |
| `assets/routine-editor.png` | ~390×844 px recommended | ⏳ Not yet supplied |
| `assets/quick-timer.png` | ~390×844 px recommended | ⏳ Not yet supplied |
| `assets/bedtime-mode.png` | ~390×844 px recommended | ⏳ Not yet supplied |

To replace a CSS placeholder with a real screenshot, find the `<!-- PLACEHOLDER:` comment in the HTML and follow the instructions there.

---

## Terms of Use — legal review required

`terms.html` is draft content. A visible warning banner is shown at the top of the page. Do not remove it until the terms have been reviewed by a qualified solicitor.

Currently confirmed in the terms:
- Owner and publisher: **Tom Fenton** ✅
- Governing law: **England and Wales** ✅
- Contact email: **hello@littleroutinetimer.com** ✅

Still outstanding:
- `[TERMS EFFECTIVE DATE]`

---

## QA checklist — final checks before launch

### Content
- [ ] `[PRIVACY POLICY EFFECTIVE DATE]` filled in
- [ ] `[TERMS EFFECTIVE DATE]` filled in
- [ ] `[SITEMAP DATE]` updated to deployment date
- [ ] App Store URL inserted (see instructions above)
- [ ] Pricing updated and "Planned launch price" note removed
- [ ] Terms of Use reviewed by a solicitor and draft warning removed

### Links
- [ ] All internal links work
- [ ] No `href="#"` links remain (all App Store CTAs are spans or live links)
- [ ] Back-to-homepage links on all subpages work
- [ ] Footer links resolve correctly

### SEO and metadata
- [ ] Canonical URLs correct on all pages (`https://littleroutinetimer.com/...`)
- [ ] Open Graph URLs correct on all pages
- [ ] OG image loads correctly when URL is shared (test with a social media link debugger)
- [ ] sitemap.xml date updated

### Privacy
- [ ] No analytics or tracking scripts (verify by viewing page source)
- [ ] No cookies set (verify in browser dev tools → Application → Cookies)
- [ ] No external API calls or CDN requests (check Network tab)

### Accessibility
- [ ] Keyboard navigation works through all interactive elements
- [ ] FAQ accordion operable by keyboard
- [ ] Mobile navigation operable by keyboard
- [ ] Focus rings visible on all focusable elements
- [ ] All images have `alt` text or `aria-hidden="true"` where decorative
- [ ] Disabled CTA spans labelled with `aria-disabled` and `aria-label`
- [ ] Heading hierarchy valid on all pages

### Responsive design
- [ ] Homepage looks correct at 320px, 480px, 768px, 1280px
- [ ] Mobile navigation opens and closes
- [ ] Cards stack cleanly on mobile

### Deployment
- [ ] All clean URL routes return HTTP 200
- [ ] Unknown URL shows custom 404 page (not Cloudflare default)
- [ ] HTTPS on all pages, no mixed-content warnings

---

## Design notes

**No redesign was made.** All corrections in this build are accuracy fixes, ownership corrections, and placeholder replacements only.

**Profile colours** — the app uses coloured initial avatars, not emoji. All copy reflects this.

**Quick Timer** — accessed from app navigation, not directly from the Home screen. All copy reflects this.

**App Store CTAs** — non-clickable spans before launch. No `href`, no page jump.

**No external dependencies** — no analytics, no CDN, no remote fonts, no cookies. Fully self-contained static site.
