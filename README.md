# POS Mobile — standalone Android app

A complete point-of-sale app that runs **entirely on the phone**. No server, no internet, no XAMPP.
Data is stored on the phone itself.

**Features:** sell (POS) · products & stock · customers · credit / partial-payment sales ·
receive payments · **payment reminders** (WhatsApp / SMS / call / copy, with history) ·
receipts (share via WhatsApp) · daily sales & profit · backup & restore · works offline.

---

## Get the app on your phone — pick ONE way

### Way 1 — Build an APK in the cloud (no software to install)  ✅ recommended
You need a free GitHub account and a computer or a phone browser in "Desktop site" mode, once.

1. Go to github.com → **New repository** → name it `pos-mobile` → Create.
2. Upload **all files and folders from this project** (including the hidden `.github` folder)
   - Easiest: on the repo page choose **Add file → Upload files** and drag the *contents* of the unzipped folder.
3. Open the **Actions** tab → **Build Android APK** → **Run workflow**. (It also runs automatically after upload.)
4. Wait ~5–8 minutes until it shows a green tick. Open the run and download **POS-Mobile-APK** (a zip).
5. Unzip it, send `app-debug.apk` to your phone (WhatsApp / USB / Drive), tap it, allow
   **"Install unknown apps"** when Android asks, and install.

Updates: build again and install the new APK over the old one — your data is kept, because every
build is signed with the same key (`keystore/debug.keystore`). Still, make a backup first.

### Way 2 — Install straight from Chrome (no APK)
1. Put the contents of the `www` folder on any free HTTPS host, e.g. **Netlify Drop**
   (app.netlify.com/drop — drag the `www` folder), GitHub Pages or Cloudflare Pages.
2. Open the link in Chrome on your phone → menu ⋮ → **Install app**.
It then has its own icon, opens full-screen and works offline.

### Way 3 — Android Studio on your PC
```
npm install
npx cap add android
npx capacitor-assets generate --android
npx cap sync android
npx cap open android      # then Build ▸ Build APK(s)
```
Before building, copy `keystore/debug.keystore` to `~/.android/debug.keystore` (Windows:
`C:\Users\<you>\.android\debug.keystore`) so updates keep working.

---

## First use
1. Open the app → **More → Settings**: set shop name, currency and **country code** (92 = Pakistan).
2. **More → Products** → add products (or **Settings → Load demo products** to try it).
3. **Sell** → tap products → cart bar → **Checkout** → choose customer → set *Amount paid now* → **Complete sale**.
   If the customer pays less than the total, the rest becomes a credit balance.
4. **Reminders** tab → everyone who owes money. Tap **Remind on WhatsApp** — WhatsApp opens with the
   message ready; press send. Edit the message in Settings.
5. When money comes in: **Receive** (customer page) or the invoice page → **Record payment**.

## IMPORTANT: your data lives only on the phone
* **Backup regularly:** Settings → **Backup data** → share the file to WhatsApp / Google Drive.
* Restore on a new phone: Settings → **Restore from backup**.
* Uninstalling the app or clearing its storage **erases the data** (unless you have a backup).
* This version is single-phone: two phones do not sync with each other.

## Notes
* Reminders are sent from your own WhatsApp/SMS — the app never sends anything by itself.
* Search products by typing name or code (barcode scanning is not included in this version).
* The signing key in `keystore/` is a **debug** key meant for private/shop use, not Google Play.
