# SongBook for SungHub — Android APK project

## Build the APK
1. Upload the contents of this project to your GitHub repository (keep the `.github` folder).
2. Open **Actions** and run **Build SongBook Android APK**, or push to `main`.
3. When the workflow succeeds, open its run and download the `songbook-debug-apk` artifact.

## Custom app icon
The `assets/icon.png` file is the custom launcher icon source. The workflow runs `npx capacitor-assets generate --android` before syncing and building, so the installed Android app uses the SongBook music-book icon. The complete supplied logo is also included as `assets/songbook-logo.png`.

## Notes
- This is the project source ZIP, not a precompiled APK.
- The app's XLS/XLSX import uses the SheetJS CDN in the supplied HTML, so importing spreadsheets requires internet access unless that dependency is bundled locally.
- A debug APK is intended for testing and can be installed manually on an Android phone. A release APK/AAB should be signed separately for Play Store distribution.
