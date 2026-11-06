# 2in1 from xcauni

One Android app, two halves: **Spotify** (the Myspoti client) and **Vortex** (YouTube), with Arabic
first (فصحى, RTL) and the original English kept as the default.

| | |
|---|---|
| Package | `com.xcauni.twoinone`, `…stable`, debug `…dev` |
| Version | 2.5.0-beta / 2.4.0 (see Releases) |
| Android | 10+ (minSdk 29), targetSdk 36, compileSdk 37 |
| License | GPL-3.0-only, see [LICENSE](LICENSE) |

## What is in it

**The Spotify half** is the upstream Myspoti client (see Credits), renamed for this fork: the app
label is `2in1 from xcauni`, the package id is `com.xcauni.twoinone`, and the upstream updater is
turned off (no update prompts from another project's releases).

**Arabic.** Every user-facing string is translated into Modern Standard Arabic (1411 strings
across 21 resource files in `values-ar`), plurals included, and the app flips to RTL with the
system language: the bar, the player, the queue and the lyrics all follow the reading direction.

**The four sections** of the bottom bar: `Spotify | Vortex | Library | Downloads`. Each section
keeps its own page and its own search (the library has its field, the home header opens the Spotify
search), and one mini player, one player and one theme are shared by all of them.

**Vortex** is the YouTube half: search, playback and downloads.

- Search YouTube through NewPipeExtractor (no API key, no yt-dlp, no FFmpeg).
- Play the audio through the app's own player — the same one Live Radio uses — so the mini player,
the full player, the notification and the lock screen work with no second session.
- Download the audio into the app's private folder, one at a time, with progress, cancel and retry;
the queue survives restarts. A notification shows progress where Android allows it.

## Build

```bash
cd base
./gradlew assembleDebug -PappVersionName=2.5.0-beta -PappVersionCode=250
```

Needs JDK 21, the Android SDK (platform 37, build-tools 37.0.0) and about 8 GB of RAM for the
Kotlin compiler. The APKs land in `base/app/build/outputs/apk/debug/` (per-ABI and universal).

## Status

The app is built and installed from this machine (debug-signed, so it updates over a previous
debug install). The source push to this repository and the APK release were the last step.

## Credits

This project is a fork and would not exist without:

- **Myspoti** by kota-zo — https://github.com/kota-zo/myspoti (GPL-3.0): the base app.
- **Spotui**, **Metrolist**, **BitChord** — the clients and UI work Myspoti itself builds on.
- **NewPipeExtractor** by TeamNewPipe (GPL-3.0) — YouTube search and stream extraction.
- **FloatingTabBar** by Elyes Mansour (Apache-2.0), vendored through BitChord.
- AndroidX Media3, Jetpack Compose, Glide.

All changes made for 2in1 stay under GPL-3.0-only, and the credits above are kept in the app's
About screen as well.

## بالعربي

تطبيق واحد بقسمين: **Spotify** (عبر Myspoti) و**Vortex** (YouTube). الواجهة عربية فصحى بالكامل
وتنعكس مع اتجاه القراءة (RTL)، والشريط السفلي فيه أربعة أقسام: Spotify | Vortex | المكتبة | التحميلات.
قسم Vortex فيه بحث في YouTube وتشغيل للصوت بنفس مشغّل التطبيق، وتحميل للملفات في مساحة التطبيق
الخاصة مع طابور وتقدّم وإلغاء وإعادة محاولة.
