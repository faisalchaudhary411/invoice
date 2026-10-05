# Al Ghani Steel Arts — Invoice Generator

Invoice / bill app for **Al Ghani Steel Arts** (welding workshop, Lahore Motorway City).
58mm mini-printer PNG + normal PNG invoices, customer records, English / اردو, installable and works offline.

## What's inside
- `index.html` — the whole app (logo, signature and stamp are built in)
- `sw.js` — offline cache (network-first, so new deploys show immediately)
- `manifest.webmanifest` + `icon-*.png`, `apple-touch-icon.png` — installable app + home-screen icon

## Deploy on GitHub Pages
1. Create a repo (e.g. `alghani-invoice`), upload **all files in this folder** to the repo root, commit.
2. Repo → **Settings → Pages** → Deploy from branch → `main` / `(root)` → Save.
3. Open `https://YOUR_USERNAME.github.io/alghani-invoice/` in Chrome → ⋮ → **Install app**.
4. Always open it from the home-screen icon — customers are then stored in one place on the phone.

## How it works
1. **Customer** → type a name (old customers appear), pick the job.
2. **Items** → tap the item box to search (English or Urdu) or type your own; enter the rate. Sq-ft items auto-calculate Qty from W × L (untick "Qty = W × L" to type a flat quantity).
3. **Save Invoice** → then **Mini 58mm PNG / Print Mini / Normal PNG**. The invoice keeps its number until you tap **New Invoice**; saving the same number again updates it (no double-counting of outstanding).
4. Signature and stamp each have their own checkbox (on by default).

## Backup (important)
- Customers tab → **Export Backup JSON** (or tick *download a backup after every save*).
- **Save App Copy (with data)** downloads the app with all customers inside it.
- **Import Backup** merges a backup into what is already on the phone.
- Clearing Chrome's site data deletes customers unless you have a backup.

Developed by Faisal Tech Solutions · 0334 1771875
