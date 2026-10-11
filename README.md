# Al Ghani invoices — one link, two businesses
- `index.html` — start page: choose **Steel Arts** or **Electric & Hardware**
- `steel/` — Al Ghani Steel Arts app (existing app, QR fixed)
- `electric/` — Al Ghani Electric & Hardware app
Upload everything to the repo root (replace the old files). Open `https://USER.github.io/REPO/`. Each app has a "🔁 Switch business" button at the top.

## Shared cloud sync
Repo, branch and token are entered once (Customers → Backup & Tools → Cloud Sync) and shared by both apps. Each business uses its own data file in that repo: `customers.json` (Steel) and `customers-electric.json` (Electric), so customers never mix.
