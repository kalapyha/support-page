# Support Page

A generic, reusable support page for iOS apps. Self-contained (HTML + CSS + JS inline, no dependencies). Bilingual EN/FR with auto-detection from browser language, pre-filled `mailto:` bug report template, light/dark mode, and mobile-responsive layout.

## Deploy to GitHub Pages

### Option A — new dedicated repo (recommended)

1. Create a new **public** repo on GitHub, e.g. `support-page`
2. Copy `index.html` to the repo root
3. Push to `main`
4. Repo → **Settings → Pages → Source**: `main` branch, `/ (root)` folder → **Save**
5. After ~1 minute, live at `https://kalapyha.github.io/support-page/`
6. Use that URL as the **Support URL** in App Store Connect for any app

### Option B — subfolder of an existing repo

1. Clone the target repo (e.g. `https://github.com/kalapyha/privacy-policy`)
2. Create a `support/` folder and place `index.html` inside
3. Commit + push
4. Available at `https://kalapyha.github.io/privacy-policy/support/`

> **Same process as the privacy policy repo** — GitHub Pages serves any `index.html` it finds in the branch root or subfolder automatically, no extra config needed.

## Test locally

```bash
cd support-page
python3 -m http.server 8000
# open http://localhost:8000
```

Click "Contact Support" — your mail client should open with subject and body pre-filled.

## Reusing for a new app

The page is intentionally generic — no app-specific content. To point it at a different email address, change the `EMAIL` constant at the top of the `<script>` block:

```js
const EMAIL = "your@email.com";
```

Everything else (FAQ, layout, bilingual support) works as-is for any iOS app.

## What's included

- Bilingual EN/FR with auto-detect (`navigator.language`) and manual toggle
- FAQ covering common support topics (reduces email volume)
- "Contact Support" button → opens mail client with pre-filled bug report template
- Email address shown as plain-text fallback
- Light/dark mode via `prefers-color-scheme`
- Mobile-responsive
- No external resources (works offline once loaded)
