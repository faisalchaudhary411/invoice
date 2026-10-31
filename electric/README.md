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
1. **Customer** → type a name (old customers appear). **Name is optional**: leave it blank for a **Walk-in Customer** — a cash sale, always paid in full, stored under one shared “Walk-in Customer” record (no balance, no past-purchase list on the invoice). For credit / part payment, type the customer's name.
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

## Product sync between phones
- **My items** (custom items), **default prices** and **barcodes** now travel in the same cloud file as customers (`products` section). Save a product on one phone → it appears on the other after the next pull (on app open, when you return to the app, or **Pull now**). Changes are pushed automatically if *Auto-push* is ticked.
- Newest change wins per item. Deleting an item or resetting a price also syncs.
- Update the app on **both** phones, otherwise an old copy will overwrite the products section when it pushes.

## If sync says “GitHub 401”
GitHub is rejecting the token stored on *that* phone (mistyped, cut-off, expired, or deleted). Tap **🔎 Test token & repo** — it says exactly what is wrong. **👁 Show / hide token** lets you check the paste (classic token = 40 characters starting `ghp_`). Create a new token and paste it on that phone.

## Stock, purchase price, suppliers, expenses, reports (new tabs)
- **📦 Stock** — every item can have a **sale price**, a **purchase price**, a quantity in stock and a *low-stock level*. Tap an item to track it. Quantity is calculated, never typed over: *adjustments + supplier purchases − sales*. So two phones selling at the same time always add up correctly, and deleting an invoice puts the pieces back. **➕ New product** adds an item with price, purchase price, opening quantity and barcode. The invoice shows “📦 In stock” under each item and **blocks a sale when stock is not enough** (switch off with the tick box). Damaged / lost stock: **➖**. Low items appear in a yellow bar on the Invoice tab and can be shared as a **reorder list** on WhatsApp.
- **🏭 Suppliers** — add suppliers, record a **purchase bill** (items, quantity, purchase price, cash paid now) and **payments**. The bill adds stock and updates the item's purchase price; the supplier balance (what you owe) is always shown. Share the balance on WhatsApp.
- **💸 Expenses** — rent, bills, wages, transport, tea… by month, with category totals. You can add your own categories.
- **📊 Reports** — today / yesterday / 7 days / month / year / custom: sales, gross profit, expenses, net profit, money received and net cash, top items, day-by-day table, and where the business stands now (customers owe you, you owe suppliers, stock value). Share the summary on WhatsApp or export **CSV (Excel)** for sales, expenses, stock and suppliers. **Backup everything (JSON)** / **Restore**.
- **Profit** is counted for items that had a purchase price when they were sold. Old invoices (made before this update) have no purchase price, so they are not counted in profit.
- **Owner PIN** (Reports tab): staff on that phone cannot see purchase prices, profit, suppliers, expenses or reports. The PIN stays on that phone only.
- Everything syncs through the same GitHub file as customers and products. **Update the app on both phones.**
- Customers tab: **🔔 Remind** sends a WhatsApp payment reminder to a customer who owes money.

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

## Barcode scan & labels (new)
- **Scan in the item search box**: a USB / Bluetooth scanner just types into the box; or tap the 📷 button to use the phone camera (Chrome on Android, continuous scanning). Scanning an item adds it with its price; scanning again adds +1 qty.
- An unknown barcode (e.g. a manufacturer sticker) asks you to pick the item once — it is then linked forever.
- **🏷️ Barcode Labels** (under Items): set how many labels per item, pick size/layout (Barcode→Name→Price or Name→Barcode→Price), then Print / Direct Print (Bluetooth) / Download PNG. Missing barcodes are generated automatically (8 digits, Code 128). Price is printed as text, not inside the barcode.
- Barcodes are stored on the device (like item prices).
