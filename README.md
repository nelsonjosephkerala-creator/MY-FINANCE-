# Nelson-Finance → Android APK

Your full app is already inside the `www/` folder here. This project wraps it in
a real Android app using **Capacitor** (the app runs offline, bundled inside the
APK — no server needed).

You have two ways to get the `.apk`. Pick ONE.

---

## ★ Option A — Build in the cloud, no software to install (recommended)

This uses GitHub to build the APK for you and hand you a download link. You don't
install Android Studio or anything.

1. Make a free account at **https://github.com**.
2. Create a new repository (click **+** → **New repository**), name it
   `nelson-finance`, keep it Private, and create it.
3. On the new repo page click **“uploading an existing file”**, then drag in
   **everything from this folder** (the `www` folder, `package.json`,
   `capacitor.config.json`, the `.github` folder, `resources`). Commit.
4. Go to the **Actions** tab. You'll see **“Build Android APK”** running (or click
   **Run workflow**). Wait ~3–5 minutes for the green tick.
5. Click the finished run → scroll to **Artifacts** → download
   **Nelson-Finance-apk**. Inside is **app-debug.apk**.
6. Copy that `.apk` to your phone and tap it to install (you'll enable
   “Install unknown apps” once when Android asks).

That's it — a real installable app with its own icon.

---

## Option B — Build on your own computer

Only if you'd rather build locally.

1. Install **Node.js** (https://nodejs.org) and **Android Studio**
   (https://developer.android.com/studio — it brings the Android SDK + Java).
2. Open a terminal in this folder and run, one line at a time:
   ```
   npm install
   npx cap add android
   npx capacitor-assets generate --android --iconBackgroundColor "#4338CA" --splashBackgroundColor "#F4F6FB"
   npx cap sync android
   npx cap open android
   ```
3. Android Studio opens. Menu **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
   When done, click **locate** →
   `android/app/build/outputs/apk/debug/app-debug.apk`.

---

## Notes
- **App name / icon:** already set to “Nelson Finance” with the finance icon in
  `resources/icon.png`. To change the name edit `capacitor.config.json`.
- **Your data:** stored inside the app on the phone, fully offline. Use the app's
  **Settings → Back up everything** now and then to save a backup file.
- **Signed release (for the Play Store or wide sharing):** the debug APK above is
  fine for your own use and sharing with family. For a Play Store release you'd
  generate a signed APK/AAB with a keystore — ask me and I'll add that step.
