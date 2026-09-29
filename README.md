# Clock — mobile edition

Separate mobile copy of your working clock, with all 450 original font files bundled locally. No build step or external dependencies.

## GitHub Pages deployment

1. Unzip Clock-Mobile.zip.
2. On GitHub, choose New repository. Name it `my-clock`, select Public and Add a README file, then Create repository.
3. Choose Add file → Upload files. Upload the CONTENTS of Clock-Mobile (not the ZIP or enclosing folder), keeping `index.html` at the repository root alongside `sw.js`, `manifest.webmanifest`, `icons/` and `fonts/`. Commit changes to `main`.
4. The font collection contains 450 files. If the browser uploader rejects a large batch, upload fewer than 100 fonts at a time inside a repository folder named `fonts`. Alternatively, clone the repository in GitHub Desktop, copy all Clock-Mobile contents into that local repository, then Commit to main and Push origin.
5. Include `.nojekyll` if your upload method shows hidden files. None of the required paths start with underscores, so this package also works without it.
6. Open Settings → Pages. Under Build and deployment choose Source: Deploy from a branch, Branch: main, Folder: / (root), then Save.
7. Wait for deployment, then open the published address shown there, normally `https://YOUR-USERNAME.github.io/my-clock/`.

All links, start URL, service-worker scope and cache paths are relative. Hosting under a repository subdirectory needs no edits.

Official instructions: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## Add to iPhone Home Screen

1. Open the published HTTPS address in Safari.
2. Tap Share (square with an upward arrow). In some Safari layouts, tap More (…) → Share first.
3. Scroll down and tap Add to Home Screen. If missing, use Edit Actions to add it.
4. Leave Open as Web App enabled if shown. Name it Clock and tap Add.
5. Launch Clock from the Home Screen while online. Tap the clock to reveal controls and wait for “Ready offline · all fonts saved”. Then try reopening in Airplane Mode.

Official instructions: https://support.apple.com/guide/iphone/iphea86e5236/ios

## Controls and offline use

Tap, move the pointer or press a key to reveal controls. They fade after 2.5 seconds; keyboard focus keeps them visible. Choose any font; the choice is saved in localStorage. Safari and the installed app may have separate storage, and clearing site data resets preferences.

Rotate to use portrait or landscape (disable system rotation lock if needed). Safe-area padding protects the clock and controls from notches and the Home Indicator. The black background extends to the screen edges; iOS controls status-bar and Home Indicator visibility. The Home Screen version removes Safari's toolbar. Desktop Brave retains its fullscreen button; that button is hidden when fullscreen is unsupported.

Each tick reads current device time, with immediate refresh after returning from the background. The app follows normal device auto-lock behavior.

The first online load caches the app and all fonts. Keep it open until “Ready offline” appears. Offline setup requires HTTPS or localhost. OS storage cleanup can remove cached files; revisit online to restore them. Opening index.html directly on a Mac works with local fonts, but service-worker installation is unavailable on file URLs.

## Updating

Replace changed files and change VERSION near the top of sw.js whenever app/font assets change. Update ASSETS if adding or removing files. Reopen online to download the update, then close all clock tabs/windows and reopen to activate it. Font preferences remain saved.

## Verification

Passed automated checks of every HTML/manifest relative path under `/my-clock/`, all 456 cached assets (including 450 fonts), simulated offline service-worker responses, and midnight/noon/single-digit-hour/PM formatting. Original font files were verified byte-for-byte. Brave could not launch in the execution environment, so visual portrait/landscape, fullscreen and physical iPhone Home Screen/status-bar behavior remain unverified. After hosting, check portrait and landscape, choose a font, reopen to confirm persistence, and test Airplane Mode after the offline-ready message appears.
