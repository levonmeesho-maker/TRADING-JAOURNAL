# Trading Journal — Android App

This is a ready-to-build Android Studio project that wraps your Trading
Journal web app in a native Android app. It installs like any other app,
works fully offline for day-to-day use, and needs internet only once to
load the Excel export library.

## What it does natively (beyond the web version)

- **Image uploads** open your phone's camera or gallery directly (Before/After buttons).
- **Export to Excel** saves the `.xlsx` file straight into your phone's **Downloads** folder — no browser download prompt needed.
- Your trades, notes, and photos are stored on-device (same auto-save as before) and survive closing the app.

## Option A — Get the APK built for you automatically (no Android Studio needed)

This project includes a GitHub Actions workflow that builds the APK in the
cloud every time you push code. You don't need Android Studio, Java, or
the Android SDK installed on your own computer for this option.

1. Go to https://github.com and create a free account if you don't have one.
2. Click **New repository** (top right → the "+" icon). Name it anything,
   e.g. `trading-journal-app`. Keep it **Public** or **Private**, either works. Click **Create repository**.
3. On the new repo's page, click **uploading an existing file** (or use the
   "Add file → Upload files" button), then drag in the entire unzipped
   `TradingJournalApp` folder contents (all files and subfolders, including
   the hidden `.github` folder — if your drag-and-drop hides it, use the
   command-line steps below instead).

   **Command-line alternative (more reliable for hidden folders):**
   ```
   cd TradingJournalApp
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/trading-journal-app.git
   git push -u origin main
   ```
4. Go to the **Actions** tab on your GitHub repo page. You'll see a workflow
   run called "Build Android APK" already running (or click **Run workflow**
   if it hasn't started).
5. Wait 2–4 minutes for it to finish (green checkmark ✅).
6. Click into the finished run, scroll to **Artifacts**, and download
   **TradingJournal-debug-apk**. Unzip it — that's your `app-debug.apk`.
7. Send that `.apk` to your phone and tap it to install (allow "install
   from unknown sources" when prompted).

## Option B — Build it yourself in Android Studio

1. **Install Android Studio** (free): https://developer.android.com/studio
2. Unzip this project folder anywhere on your computer.
3. Open Android Studio → **Open** → select the unzipped `TradingJournalApp` folder.
4. Let Gradle sync (Android Studio will prompt to download anything missing — just accept).
5. Plug in your Android phone via USB with **USB debugging** enabled (Settings → About phone → tap "Build number" 7 times → Developer options → USB debugging), or use an emulator.
6. Click the green **Run ▶** button in Android Studio, choose your device, and the app installs and launches automatically.

### To get a shareable APK file from Android Studio (install without a cable)

1. In Android Studio: **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
2. Once it finishes, click the **locate** link in the notification, or find it at:
   `app/build/outputs/apk/debug/app-debug.apk`
3. Send that `.apk` file to your phone (email, WhatsApp, USB, etc.) and tap it to install.
   You'll need to allow "install from unknown sources" the first time — Android will prompt you for this automatically.

## Notes

- App name: **Trading Journal**, package id: `com.topanalyst.tradingjournal`.
- Minimum Android version supported: Android 6.0 (API 23) and up — covers virtually all phones in use today.
- If you ever want to change colors, columns, or text, edit `app/src/main/assets/index.html` — that's the same file as the web version, just running inside a native wrapper.
- To publish this on the Google Play Store later, you'd need to generate a **signed release build** (Build → Generate Signed Bundle/APK) and create a Play Console developer account — a different process from the debug APK above, happy to walk through that when you're ready.
