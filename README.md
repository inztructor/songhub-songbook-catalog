# SongBook for SungHub — Capacitor Android APK

This project packages the uploaded `index.html` as an Android app using Capacitor and GitHub Actions.

## Project contents

- `www/index.html` — your supplied SongBook HTML app.
- `package.json` — Capacitor dependencies and scripts.
- `capacitor.config.json` — app ID, app name, and web asset directory.
- `.github/workflows/build-apk.yml` — builds a debug APK on pushes to `main` or by manual dispatch.

## Build an APK on GitHub

1. Create a GitHub repository named for your app.
2. Extract this ZIP and upload all files and folders to the repository root. Ensure `.github/workflows/build-apk.yml` is included.
3. Use `main` as the default branch.
4. Open the repository's **Actions** tab.
5. Select **Build SongBook Android APK**, then click **Run workflow**, or push a commit to `main`.
6. Wait for the workflow to finish successfully.
7. Open the completed workflow run and download the `songbook-debug-apk` artifact.
8. Extract the artifact ZIP to find `app-debug.apk`, then transfer it to your Android phone and install it. You may need to allow installation from your file manager/browser.

## App details

- App name: `SongBook for SungHub`
- Android application ID: `com.songhubdownloads.songbook`
- Web assets: `www/`
- Output: debug APK for testing and direct installation.

## Important behavior and limitations

- The HTML currently loads SheetJS from a CDN (`cdnjs.cloudflare.com`). The XLS/XLSX/CSV import feature therefore needs internet access unless you bundle that JavaScript library locally and update the script reference.
- The sample songs are built into the HTML; users can import their own song list.
- The app uses browser `localStorage` and IndexedDB to persist custom pages and imported song data in the WebView.
- This setup does not add native Android file permissions or a native Downloads-folder feature. The provided HTML is a songbook/import app, not a download manager. If you need Android Downloads-folder access, tell me what files the app must read/write and I can add a suitable native Capacitor plugin and permission handling.
- The HTML includes an attribution check that redirects to the SongHub Downloads blog if the `HungryMeTutorials` credit is removed or hidden. That code is preserved from your uploaded file.

## Local build (optional)

Requirements: Node.js 20+, Java 21, Android SDK, and Gradle-compatible Android tooling.

```bash
npm install
npx cap add android
npx cap sync android
cd android
./gradlew assembleDebug
```

APK path: `android/app/build/outputs/apk/debug/app-debug.apk`.

## Customize

Before distributing, review the app ID, app name, external CDN dependency, attribution/redirect behavior, and any data handling requirements.
