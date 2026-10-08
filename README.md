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
2. **Items** → tap the item box to search (English or Urdu) or type your own. Every item has 3 simple pricing modes:
   - **📐 Sq ft** — enter Width and Length; Amount = W × L × Rate.
   - **📏 Running ft** — enter total running feet; Amount = ft × Rate.
   - **💰 Lumpsum** — enter the total price only (no calculation; values pasted as-is).
3. **Save Invoice** → then **Mini 58mm PNG / Print Mini / Normal PNG / 📲 Share WhatsApp**. The invoice keeps its number until you tap **New Invoice**; saving the same number again updates it (no double-counting of outstanding).
4. Signature and stamp each have their own checkbox (on by default).
5. **Account statement / receipt:** Customers → **Use in Invoice** starts a fresh invoice for that customer and loads their last invoice items so you can reuse/edit. Past purchases are written as a complete record on the **digital (Normal PNG) invoice only** (not on mini printer). With no items, Preview / Print gives an **ACCOUNT STATEMENT**. Tick **📜 Include account history** to print the last account entries under a normal invoice too.

## Direct printing to a Bluetooth mini printer
- Invoice tab → **🔌 Connect Printer** (printer on, close to the phone) → **⚡ Print Direct**.
- **MXW01 / Fun Print printers** (cat-style mini printers) are detected automatically and use their own Bluetooth protocol (service AE30). Settings: *Darkness*, *Data chunk size* (keep 480 for the cleanest print — small chunks make the printer stop-and-start and print streaky), *Rotate 180°* (untick if the print comes out upside down).
- Other BLE ESC/POS printers use the *Image — GS v 0 / ESC ** modes. If nothing prints: **⚙️ Printer settings** → **Test Print**, then try another *Print mode*, *Speed* **Slowest**, or another *Bluetooth channel*.
- Classic-Bluetooth printers: install the free **RawBT** print service, pair the printer there, then use **Print Mini** and choose RawBT in Android's print dialog.
- Needs Chrome on Android and the app opened from its https link.

## Backup (important)
- Customers tab → **Export Backup JSON** (or tick *download a backup after every save*).
- **Save App Copy (with data)** downloads the app with all customers inside it.
- **Import Backup** merges a backup into what is already on the phone.
- Clearing Chrome's site data deletes customers unless you have a backup.

Developed by Faisal Tech Solutions · 0334 1771875
