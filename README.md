[README.md](https://github.com/user-attachments/files/34218385/README.md)
# GenPlay — Modern Home Media Server & Instant Cast System

[![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20Android%20TV-3DDC84?logo=android&logoColor=white)](https://developer.android.com/)
[![Language](https://img.shields.io/badge/Language-Kotlin-7F52FF?logo=kotlin&logoColor=white)](https://kotlinlang.org/)
[![UI Framework](https://img.shields.io/badge/UI-Jetpack%20Compose-4285F4?logo=jetpackcompose&logoColor=white)](https://developer.android.com/jetpack/compose)
[![Media Engine](https://img.shields.io/badge/Media3-ExoPlayer-FF6F00)](https://developer.android.com/media/media3)
[![Design](https://img.shields.io/badge/Design-Fluid%20Glass%20M3-6C9BFF)](https://m3.material.io/)

**GenPlay** is a high-performance, self-hosted local media server and streaming client application designed for mobile devices, web browsers, and Android TVs. Built with **Kotlin Jetpack Compose** and **Media3 ExoPlayer**, GenPlay combines the raw streaming power of home media servers with an ultra-sleek, glassmorphic spatial user interface.

---

## Key Features

### 🚀 Dual Operational Modes (Server vs. Connect Player)
- **Server Mode**: Hosts local storage media folders via a high-performance embedded Java NIO HTTP server (`GenPlayHttpServer` on port `8471`).
- **Connect Mode (Client)**: Instantly discovers and connects to GenPlay servers on the local Wi-Fi network for remote media browsing and playback.
- **First-Run Onboarding Wizard**: Guides new mobile users to choose their operational role on initial startup with full re-configuration flexibility in Settings.

### ⚡ Gen Air Instant Beam (Cast to TV / Web)
- **Real-Time Stream Casting**: Tap the **Gen Air** button on any mobile video or detail screen to instantly beam playback onto connected Android TVs or active Web Browser clients.
- **Timestamp Synchronized**: Teleports the stream to the target device at the exact millisecond timestamp.
- **Seamless Local Hand-Off**: As requested by mobile ergonomics, local playback on the phone gracefully pauses and returns to the media detail view while the target TV/Web device takes over.

### 📺 100% Remote DPAD Compatibility for Android TV
- **Translucent Top Dock**: Floating glass navigation bar positioned at `TopCenter` on Android TV interfaces.
- **Tactile Focus Rings**: DPAD remote focus triggers a glowing sapphire border and a responsive `1.08x` spring-loaded lens zoom (`FluidMotion.LensSpring`).
- **Native Android TV Launcher**: Includes `LEANBACK_LAUNCHER` manifest support for home screen shortcuts.

### 🌐 Embedded Web Portal & Server Engine
- Built-in responsive HTML5 web portal hosted directly from assets at `http://<ip>:8471`.
- Web player includes auto-polling for incoming **Gen Air** beam commands to open and stream videos inside browser tabs.
- Non-blocking NIO `FileChannel.transferTo` streaming delivers 256KB chunked byte transfers with zero device heating or CPU bottlenecks.

### 🔄 Cross-Device Auto Resume
- Progress is synced to Room persistence (`ProgressEntity`) every 1.5 seconds.
- Pre-seek decoding before ExoPlayer `prepare()` ensures zero timestamp jumps or freezing when resuming movies.

### 🌐 System Localization (Multi-Language)
- Automatic locale adaptation supporting both **English** (`values/strings.xml`) and **Turkish** (`values-tr/strings.xml`).

---

## Inspiration & Design Philosophy

GenPlay synthesizes the best principles from leading media and spatial design systems:

- **Plex & Jellyfin Architecture**: Decoupled media server/client architecture, REST API session states, and zero-trust local pairing protocol.
- **Apple TV & visionOS Spatial UI**: Translucent floating glass docks, soft depth gradients, spring-loaded tactile micro-interactions, and spatial hierarchy.
- **Fluid AI Design System**: Soft glowing ambient halos (`#6C9BFF` Soft Sapphire), zero harsh neon tones, and smooth state transitions.

---

## Technical Stack & Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│                          GenPlay Application                           │
├───────────────────────────────────┬────────────────────────────────────┤
│         Jetpack Compose UI        │        Core Engine & Persistence   │
│ - FloatingGlassDock (TV Top Dock) │ - GenPlayDatabase (Room SQLite)    │
│ - GenAirSheet (Cast Target Picker)│ - GenPlayHttpServer (NIO Channel)  │
│ - CustomPlayerScreen (ExoPlayer)  │ - MediaRepository & DeviceRepo     │
└───────────────────────────────────┴────────────────────────────────────┘
```

- **Language**: 100% Kotlin with Coroutines & Flow API.
- **UI Framework**: Jetpack Compose with Material Design 3 (M3).
- **Database**: Room SQLite Database with KSP annotation processing.
- **Video Engine**: AndroidX Media3 ExoPlayer with immersive OSD controls and gesture HUDs.
- **I/O Engine**: Java NIO `FileChannel.transferTo` socket streaming with CORS support.

---

## Getting Started & Building

### Prerequisites
- Android Studio Ladybug or newer
- JDK 17+
- Android SDK 34 (`minSdk = 24`, `targetSdk = 34`)

### Build Debug APK
```bash
# Clone the repository
git clone https://github.com/example/genplay.git
cd genplay

# Build debug APK
gradle assembleDebug
```

The compiled APK will be located at:
`app/build/outputs/apk/debug/app-debug.apk`

---

## License & Credits

Created as a next-generation Android media server and client applet. Built with passion using Kotlin, Jetpack Compose, and Material Design 3.
