# 🎉 Liuxin's 7th Birthday Party Invitation

A fancy, animated, mobile-friendly birthday invitation site built as a single
static `index.html` — perfect for free hosting on **GitHub Pages**.

## ✨ Features

| Feature | How it works |
| --- | --- |
| **Party details + map** | Embedded Google Map, "Open in Google Maps" link, activities |
| **Countdown timer** | Live days/hours/mins/secs until the party |
| **Download invitation** | Generates a real PNG invitation card on the fly (canvas) |
| **Add to calendar** | Downloads an `.ics` file for any calendar app |
| **RSVP form** | Sends responses to your email via [FormSubmit](https://formsubmit.co) — no backend needed |
| **Photo gallery** | Guests upload photos to [Cloudinary](https://cloudinary.com); everyone can view & download |
| **Fancy touches** | Animated gradient background, floating balloons, confetti bursts, scroll reveals, photo lightbox |

## ⚙️ Configuration (required for RSVP + photos)

Open `index.html` and edit the `CONFIG` block near the bottom (inside `<script>`):

```js
const CONFIG = {
    RSVP_EMAIL: "your-email@example.com",        // where RSVPs are emailed
    CLOUDINARY: {
        CLOUD_NAME: "your_cloud_name",
        UPLOAD_PRESET: "your_unsigned_preset",
        TAG: "liuxin_birthday_7"
    },
    ...
};
```

### 1. RSVP email (FormSubmit — free, no signup)
- Set `RSVP_EMAIL` to your email address.
- The **first** time someone submits the form, FormSubmit emails you a one-time
  link to confirm the address. Click it once, and all future RSVPs arrive in your inbox.

### 2. Photo sharing (Cloudinary — free tier)
1. Create a free account at [cloudinary.com](https://cloudinary.com).
2. Copy your **Cloud name** from the dashboard → set `CLOUD_NAME`.
3. Go to **Settings → Upload → Upload presets → Add upload preset**, set
   **Signing Mode = Unsigned**, save, and copy its name → set `UPLOAD_PRESET`.
4. To let the gallery list uploaded photos: **Settings → Security →** uncheck the
   **"Resource list"** restriction. (Photos are tagged with `TAG` so only party
   photos are listed.)

> No Cloudinary account? The site still works — the upload button simply shows a
> friendly "not configured yet" message, and everything else runs fine.

## 🚀 Deploy to GitHub Pages

1. Create a new repository on GitHub (e.g. `liuxin-birthday`).
2. Push these files to it:
   ```bash
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git branch -M main
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment**.
   - **Source:** *Deploy from a branch*
   - **Branch:** `main` / `/ (root)` → **Save**
4. Wait ~1 minute. Your site goes live at:
   `https://<your-username>.github.io/<your-repo>/`

That's it — share the link! 🎈

## 📝 Editing the details

All party info (date, time, location, map) lives directly in `index.html`.
The party date/time for the countdown and calendar file is set in `CONFIG`:

```js
PARTY_START: new Date(2026, 9, 11, 18, 0, 0),  // month is 0-indexed: 9 = October
PARTY_END:   new Date(2026, 9, 11, 19, 45, 0),
```
