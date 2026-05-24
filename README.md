# Crystal FM Hygiene Order Form

Standalone web order form for hygiene supplies. **Completely separate from the Crystal Mission Control dashboard** — different Vercel project, different URL, no shared code or data.

## How it works

1. Manager shares the form's URL on WhatsApp
2. Recipient opens the link on their phone, sees all 37 items with photos
3. Types quantities for items they need (leaves rest blank)
4. Hits "Generate Order Link" — JavaScript encodes the order as base64 in the URL hash
5. Recipient copies the link (or hits the WhatsApp button) and sends it back to the manager
6. Manager taps the link — page detects the hash, decodes, shows a clean read-only review

**No backend. No database. No email. No accounts.** The order data lives inside the URL each recipient generates.

## Files

| Path | Purpose |
|---|---|
| `public/index.html` | The whole form + review view (single page) |
| `public/img/*.png` | 36 product photos (extracted from the original PDF) |
| `vercel.json` | Vercel hosting config — serves `public/` as static |
| `.gitignore` | Standard ignores |

## To deploy

### Option A — via GitHub + Vercel UI (recommended for non-developers)

1. Create a new GitHub repo (e.g. `crystal-order-form`).
2. Push this folder to it:
   ```
   cd ~/crystal-order-form
   git init -b main
   git add .
   git commit -m "Initial commit"
   git remote add origin git@github.com:musadhillu-lang/crystal-order-form.git
   git push -u origin main
   ```
3. Go to https://vercel.com/new and import the new repo.
4. Click **Deploy** (no env vars, no build command needed).
5. Vercel gives you a URL like `crystal-order-form.vercel.app`.

### Option B — via Vercel CLI

```
npm i -g vercel
cd ~/crystal-order-form
vercel
```

## To update later

Edit `public/index.html` (product list, styling, etc.) → push to GitHub → Vercel auto-redeploys in ~30s.
