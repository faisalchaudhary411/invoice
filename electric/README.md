# Al Ghani Electric & Hardware — Invoice Generator

Invoice / bill app for **Al Ghani Electric & Hardware** (T Prime Block, Lahore Motorway City).
58mm mini-printer PNG + normal PNG invoices, customer records, English / اردو, installable and works offline.

## What's inside
- `index.html` — the whole app (logo, signature and stamp are built in)
- `sw.js`, `manifest.webmanifest`, icons — offline cache + installable app

## Deploy on GitHub Pages
1. Create a repo (e.g. `alghani-eh-invoice`), upload **all files in this folder** to the repo root, commit.
2. Repo → **Settings → Pages** → Deploy from branch → `main` / `(root)` → Save.
3. Open `https://YOUR_USERNAME.github.io/alghani-eh-invoice/` in Chrome → ⋮ → **Install app**.
4. Always open it from the home-screen icon — customers are then stored in one place on the phone.

## How it works
1. **Customer** → type a name (old customers appear).
2. **Items** → tap the item box to search ~130 electric & hardware items (the price fills in), or type any item yourself.
   - **🔢 Qty × Price** — Amount = Qty × Price. Change the price any time; tap **Save as default price** to remember it for that item.
   - **💰 Lumpsum** — only Qty and Amount boxes. Nothing is multiplied; the amount is used as typed and no rate is printed.
   - **+ Custom Item** — name, price and qty; it is also saved in the search list under "★ My items".
3. **Save Invoice** → Mini 58mm PNG / Print Mini / Normal PNG / WhatsApp PDF / Share as Images / direct Bluetooth printing.
4. The **QR code** holds only shop name, invoice no, total, due and the Easypaisa number, so the dots are big and it scans from a thermal printout.
5. Prices in the built-in list are starting estimates — edit them as needed.

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
