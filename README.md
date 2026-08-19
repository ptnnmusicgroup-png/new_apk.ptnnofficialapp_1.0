# PTNN Android

Native Android companion for the PTNN website. It uses Kotlin + Jetpack Compose, targets API 36, and currently implements the phone-optimized **Home screen only**. It reads the same public Firestore collections:

- `ptnn_updates`
- `ptnn_music_releases`

## Open and run

1. Open `android-app` in Android Studio.
2. Install Android SDK Platform 36 and sync Gradle.
3. In Firebase Console, register the Android package `com.ptnn.music` in the existing project `my-website-62bef`.
4. Download its `google-services.json` and place it at `android-app/app/google-services.json`.
5. Add `id("com.google.gms.google-services") version "4.4.3" apply false` to the root plugins block, then add `id("com.google.gms.google-services")` in `app/build.gradle.kts`.
6. Enable Email/Password authentication if it is not already enabled.

Without `google-services.json`, the application still builds and shows the same fallback post/release used by the website; Firebase sign-in and live content intentionally remain unavailable.

## Current scope

The current build intentionally contains no release list screen, updates screen, store screen, profile screen, or bottom navigation. Home renders the hero, recent release artwork rail, latest updates, and social actions. Those routes will be added in later work.

## Security and store boundary

The web repository's local, hard-coded administrator credential is deliberately not copied. Use Firebase Auth with a server-issued custom claim for an admin workflow.

The Store remains visually locked (`UPDATING`) because this repository has no actual J&T server function. Do not place J&T secrets in the app; create an authenticated backend endpoint before enabling cart/checkout.
