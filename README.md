# Instagram Focus Mode

Android AccessibilityService prototype that adds a focus layer over Instagram.

## Important

This is a companion app; it does not modify Instagram. Instagram can change its accessibility labels and screen structure, so detection may need maintenance.

The overlay deliberately ends above Instagram's bottom navigation area, so the bottom taskbar remains visible and usable.

## GitHub build

1. Put the contents of this project in the **root of your GitHub repository**.
2. Open **Actions**.
3. Run **Build Android APK** (or push to `main`).
4. Open the completed workflow run.
5. Download the `instagram-focus-mode-debug` artifact.
6. Extract the APK and install it on Android.
7. Open the app and enable its Accessibility Service in Android Settings.

Workflow file:

`.github/workflows/build-apk.yml`

## If you upload the ZIP directly

Do not keep an extra `InstagramFocusMode/` folder inside the GitHub repository. The ZIP is already structured so `settings.gradle.kts` is at the repository root.

## Behavior

- Feed: movement is intercepted; taps are replayed.
- Stories: horizontal swipes are replayed; vertical swipes are blocked.
- Explore/Reels: content area is replaced by a motivational message.
- Other profiles: header remains visible while the lower posts/reels area is masked.
- Bottom Instagram navigation is never covered by the accessibility overlay.
- A recently detected shared-reel marker followed by a scroll opens Instagram Direct Messages.
- Accessibility event timeout is configured to 20 ms as a low-latency target; Android does not guarantee a true 20 ms end-to-end response.
