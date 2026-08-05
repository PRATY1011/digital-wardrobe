# Wardrobe — trial PWA

See everything you own. Buy less, wear more.

A zero-backend, installable web app for closet digitization. Each tester's data lives entirely on their own phone (IndexedDB) — no accounts, no server, no cost.

## Trial limits
- 20 pieces per user (keeps the trial light)
- One profile per device — share the link with up to 5 friends/family, each installs on their own phone

## Host on GitHub Pages (one-time, ~3 minutes)
1. Create a new **public** repository on github.com (e.g. `wardrobe`)
2. Upload all files in this folder (`index.html`, `manifest.json`, `sw.js`, `icons/`, `README.md`) — drag-and-drop works on the repo page via **Add file → Upload files**
3. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main` / `(root)` → Save
4. After ~1 minute your app is live at `https://<your-username>.github.io/wardrobe/`

## Install on a phone
Send testers the link, then:
- **Android (Chrome):** open the link → menu (⋮) → **Add to Home screen** → Install
- **iPhone (Safari):** open the link → Share button → **Add to Home Screen**

It runs full-screen like a native app and works offline after the first load.

## What's in this trial
- Add pieces via camera snap, photo gallery (with a privacy consent gate), tag scan, or pasted product link
- Auto colour detection from the photo; everything editable before saving
- Occasion buckets: Casual, Office, Gym, Ethnic, Party, Lounge
- Per-item analytics: wear count, last worn, cost-per-wear, 12-week wear strip
- Insights: closet value, % asleep, monthly & quarterly spend, most worn, brands owned, duplicate-purchase nudge
- Profile: usual size + optional body measurements (stored on-device only)

## Not in this trial (by design)
- Auto-fill from store links (needs a small server — next version)
- AI category tagging (colour only for now)
- Cross-device sync / real accounts

## Turn on AI tagging (Claude vision)
Photos can be read by Claude — garment type, category (Top/Bottom/Dress/Ethnic/…), occasion bracket (Office/Gym/Ethnic/Party/…), colour, and even brand/size/price off a swing-tag photo.

1. Go to **console.anthropic.com** → sign in → **API Keys** → Create Key
2. **Set a monthly spend limit first** (Settings → Limits) — e.g. $5 is far more than a 5-person × 20-piece trial can use. Each photo costs a fraction of a rupee (small image + Haiku model).
3. Share the key with your 5 testers **privately** (WhatsApp/Signal) — never commit it to the repo or paste it in any public place
4. Each tester opens the app → **You** tab → pastes the key under **AI tagging** → Save profile

The key is stored only in that phone's local storage. Without a key the app still works — it falls back to on-device colour detection.

**If the key ever leaks:** delete it in the console and issue a new one — takes seconds, and the spend limit caps the damage meanwhile.
