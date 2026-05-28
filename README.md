# 🌱 Sprout — Learning Adventure
### NDIS Early Childhood Intervention Therapy App
**Ages 3–8 · Australian Curriculum F–2 · Speech & OT Activities**

---

## Files in this package

| File | Purpose |
|------|---------|
| `index.html` | Main app (all therapy activities, routines, dashboard) |
| `quest.html` | Sprout's Quest dungeon crawler game |
| `manifest.json` | PWA install configuration |
| `sw.js` | Service worker — makes app work fully offline |
| `icons/` | App icons (192px and 512px) |
| `package.json` | Capacitor build dependencies |
| `capacitor.config.json` | Capacitor native app configuration |

---

## Option 1 — Install as a PWA (Easiest, works today)

A PWA installs directly from the browser — no app store needed.
Works on **iPad, iPhone, Android tablets and phones**.

### iPad / iPhone
1. Open **Safari** and navigate to the app URL (or open `index.html` from a local server)
2. Tap the **Share** button (box with arrow)
3. Tap **"Add to Home Screen"**
4. Tap **"Add"**
5. The Sprout icon now appears on the home screen — tap to open full screen

> **Running locally on iPad:** Use a simple server. On a Mac on the same Wi-Fi:
> ```bash
> cd sprout-app
> python3 -m http.server 8080
> ```
> Then open `http://YOUR-MAC-IP:8080` in Safari on the iPad.

### Android
1. Open **Chrome** and navigate to the app URL
2. Tap the **three-dot menu** → **"Add to Home screen"**
3. Tap **"Add"**
4. Or: Chrome may show an install banner automatically

### Fully offline after first load
Once installed, the service worker caches everything.
The app works with no internet connection — important for clinic use.

---

## Option 2 — Build a native app with Capacitor

This produces a real `.apk` (Android) or `.ipa` (iOS) you can sideload
or submit to app stores.

### Prerequisites
- Node.js 18+ — [nodejs.org](https://nodejs.org)
- **Android:** Android Studio — [developer.android.com/studio](https://developer.android.com/studio)
- **iOS:** Mac + Xcode 15+ — Mac App Store

### Steps (both platforms)
```bash
# 1. Install dependencies
cd sprout-app
npm install

# 2a. Build for Android
npm run build:android
# This opens Android Studio. Press the green Run ▶ button.
# For a release APK: Build → Generate Signed Bundle/APK

# 2b. Build for iOS (Mac only)
npm run build:ios
# This opens Xcode. Press the Run ▶ button.
# For distribution: Product → Archive
```

### Android — install APK directly on a device (no Play Store)
```bash
# After building in Android Studio, find the APK at:
# android/app/build/outputs/apk/debug/app-debug.apk
# 
# Transfer to device via USB or email, then:
# Settings → Security → Allow installation from unknown sources
# Open the APK file on the device
```

### iOS — install IPA on iPad (no App Store, using AltStore)
```bash
# Build IPA in Xcode: Product → Archive → Distribute App → Ad Hoc
# Install AltStore on iPad: altstore.io
# Open AltStore and sideload the IPA
```

---

## Option 3 — Use PWABuilder (no coding required)

1. Host the app somewhere (e.g. GitHub Pages, Netlify — free)
2. Go to **pwabuilder.com**
3. Enter your URL
4. Click **"Package for stores"**
5. Download Android APK or iOS package ready to submit

---

## Hosting for free (to enable remote PWA install)

### GitHub Pages (recommended)
```bash
# Create a free GitHub account at github.com
# New repository → upload all files in this folder
# Settings → Pages → Source: main branch, root folder
# Your app is live at: https://USERNAME.github.io/REPO-NAME
```

### Netlify (drag and drop)
1. Go to **netlify.com** → sign up free
2. Drag the entire `sprout-app` folder onto the Netlify dashboard
3. Done — live URL in 30 seconds

---

## Clinic / school network use (no internet)

The simplest setup for a single clinic iPad:
1. Copy the folder to the iPad using **Files app** + a USB cable
2. Use **"Whisk"** (free App Store app) to open `index.html` locally
3. Or host on a local network server (Raspberry Pi, NAS, Mac Mini)

---

## Technical notes

- Pure HTML/CSS/JavaScript — no build step required for web use
- All sounds synthesised via Web Audio API (no audio files)
- localStorage used for saving progress, profile, and star count
- Speech recognition uses Web Speech API (en-AU)
- OpenMoji 15.0 illustrations (CC BY-SA 4.0) via jsDelivr CDN
  (cached offline after first load)
- Target: modern browsers, iOS 15+, Android 9+
- Minimum screen: 375px wide (iPhone SE)

---

## Support

Built for NDIS Early Childhood Early Intervention (ECEI) supports.
Aligned with Australian Curriculum Foundation–Year 2.

Activities: Speech & Sounds, Phonological Awareness, Receptive Language,
Vocabulary, Scene & Language, Pragmatics, Story Time, Draw & Colour,
Letters & Writing, Matching Games, OT Activities, Feelings & Emotions,
My Routine, Sprout's Quest (dungeon crawler game).
