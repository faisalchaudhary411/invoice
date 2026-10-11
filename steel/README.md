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
   - **💰 Lumpsum** — tick one or more items. For **each** ticked item enter qty, gauge, **measurements** and **that item's own amount**. The amount is a lump sum for the whole item, so **no rate is printed** (a dash is shown) and nothing is divided by qty. Each item becomes its own invoice line and all amounts are added into the invoice total.
     - Normal items: one measurements box, several sizes separated by a space (`3.5x7 4x8` prints as `3.5 ft × 7 ft, 4 ft × 8 ft`). Leave it empty to print only qty and amount.
     - **Chogath** (and any custom item with *Ask depth* ticked): a list of size rows — measurement, depth (inch), pcs. Tap **➕ Add size** for more. Each row prints on its own line, e.g. `3.5 ft × 7 ft = 5 inch = 2 pcs`, and the item's qty becomes the total pcs of the rows. To add depth to another item, use **Add custom item** and tick *Ask depth for this item*.
3. **Save Invoice** → then **Mini 58mm PNG / Print Mini / Normal PNG / 📲 Share WhatsApp (PDF) / 🖼 Share as Images**. The invoice keeps its number until you tap **New Invoice**; saving the same number again updates it (no double-counting of outstanding). Invoice numbers are checked so two invoices never get the same number.
   - **WhatsApp:** WhatsApp stretches very tall images, so *Share WhatsApp* sends a sharp PDF. *Share as Images* splits a tall invoice into page-shaped pictures instead.
4. Signature and stamp each have their own checkbox (on by default).
5. **Account statement / receipt:** Customers → **Use in Invoice** starts a fresh invoice for that customer and loads their last invoice items so you can reuse/edit. Past purchases are written as a complete record on the **digital (Normal PNG) invoice only** (not on mini printer). With no items, Preview / Print gives an **ACCOUNT STATEMENT**. Tick **📜 Include account history** to print the last account entries under a normal invoice too.

## Customers, payments and history
- **Add Payment** accepts amounts like `5,000` or Urdu digits. Any overpayment is kept as customer credit and offsets later bills.
- In each customer's history, **✎** corrects the paid amount of an invoice or payment, and **🗑** deletes it (balance recalculates). To change the *items* of an old invoice, delete it and create a new one.
- Deleting a customer or an entry is remembered, so it does not come back when you sync or import a backup.
- Same name + different phone number = two different customers. Same name with no phone (or the same phone) = the same customer.
- The mini invoice lists each history item on two lines (name + amount, then size and rate) with a dotted line between items.
- Long statements are never cut off: the invoice image is sized to its content.

## Cloud sync (optional, GitHub)
- Customers tab → sync settings: repo, file path (`customers.json`), branch and token. Pull merges cloud data into the phone; push merges the cloud copy first, so one phone never overwrites another phone's invoices.
- The cloud file is `{ "customers": [...], "deleted": {...} }`. The old plain-list format is still read.
- Use a **fine-grained token limited to that one repo** (Contents: Read and write). It is stored on the phone only; **🔒 Forget token** removes it.
- Backups and imports accept files with a trailing comma, and a plain list or `{customers: [...]}`.

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

Developed by Easy Tech Solutions · 0334 1771875
