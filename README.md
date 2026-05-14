# ArtVault — landing site

Static landing site for **ArtVault** (US private credit fund originating short-term senior secured loans against fine art, watches, and collectibles).

Production domain: `artvault.fund` (already owned by the team — connect via Vercel; see below).

---

## Stack

Pure static HTML + CSS. No build step, no JavaScript, no framework. Fonts are loaded from Google Fonts at runtime.

```
.
├── index.html              # Hero
├── terms/index.html        # Terms of Service (draft template)
├── privacy/index.html      # Privacy Policy (draft template)
├── data-retention/index.html
├── assets/
│   ├── style.css           # Single shared stylesheet
│   ├── geometric.svg       # Hero artwork (hand-coded XML)
│   └── favicon.svg
├── vercel.json             # cleanUrls so /terms resolves without /index.html
└── README.md
```

## Local preview

Open `index.html` directly in a browser, or run any static server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to Vercel (5 steps)

1. Go to **vercel.com/new** and sign in with the GitHub account that has access to `zega-rwa/artvault-site`.
2. Click **Import** on the `artvault-site` repo. Framework preset: **Other**. Build command: leave empty. Output directory: leave as root. Click **Deploy**.
3. Wait ~20s for the first deploy to complete. Confirm the preview URL renders correctly.
4. In the Vercel project → **Settings → Domains** → add `artvault.fund` and `www.artvault.fund`. Vercel will show you the DNS records to create.
5. At the domain registrar where `artvault.fund` is held, add the DNS records Vercel asks for:
   - For the apex (`artvault.fund`): **A record** → `76.76.21.21`
   - For `www`: **CNAME** → `cname.vercel-dns.com`
   - Propagation usually takes minutes; SSL is provisioned automatically.

That's it — the site is live.

## Editing copy

All content is in plain HTML. The hero copy lives in `index.html`. The three legal pages each carry an italic *"Draft template — pending counsel review"* note at the top; counsel should review and the note removed before relying on them.

CTA links are `mailto:info@artvault.fund` with pre-filled subject lines. Update the email or replace with a form when one is ready.

## Brand tokens

CSS custom properties at the top of `assets/style.css`:

- `--cream` `#F8F4EC` (background)
- `--navy`  `#14213d` (text + accent)

Type stack:

- Headlines — **Fraunces** 300 (serif, low opsz)
- Body / UI — **Inter** 400/500
- Caption / monospace — **JetBrains Mono** 400

Do not introduce a third colour or change the type system without buy-in from the founders — this palette is the locked v1 spec.
