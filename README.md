
<p align="center">
  <img src="![genplay-app-logo-1793455346872.avif](https://user49814.na.imgto.link/public/20261031/7e67c563038d49bcf3c08957-genplay-app-logo-1793455346872.avif)" alt="GenPlay Logo" width="160" style="border-radius: 28px;" />
</p>

<h1 align="center">GenPlay — Next-Gen Home Media Server &amp; Instant Beam Player</h1>

<p align="center">
  <b>A high-performance, self-hosted media streaming server and client for Android Mobile, Web Browsers, and Android TV.</b>
</p>

<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#ui-screenshots">Screenshots</a> •
  <a href="#gen-air-instant-beam">Gen Air Beam</a> •
  <a href="#architecture">Architecture</a> •
  <a href="#design-inspiration">Inspiration</a> •
  <a href="#getting-started">Getting Started</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%20%7C%20Android%20TV-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Platform" />
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white" alt="Language" />
  <img src="https://img.shields.io/badge/UI-Jetpack%20Compose-4285F4?style=for-the-badge&logo=jetpackcompose&logoColor=white" alt="UI" />
  <img src="https://img.shields.io/badge/Media-ExoPlayer%20Media3-FF6F00?style=for-the-badge" alt="Media" />
</p>

---
## 🔥 Key Features

### 📡 Gen Air Instant Beam (Cast to TV / Web)
- **Instant Beam Action**: Tap the **Gen Air** button on any mobile player or detail screen to cast live video streams onto connected Android TVs or Web Browsers on your local Wi-Fi.
- **Millisecond Timestamp Sync**: Beam payloads transmit exact playback timestamps (`positionMs`) so the target TV or web tab opens and streams without losing a second.
- **Ergonomic Hand-Off**: Teleports playback to the big screen while automatically closing local mobile playback to return the phone user to the media details view.

### ⚙️ Dual Operational Modes (Server vs. Connect)
- **Server Mode**: Hosts local media folders on the device via an embedded high-speed Java NIO HTTP Server (`GenPlayHttpServer` on port `8471`).
- **Connect Mode**: Discovers local GenPlay servers over LAN and streams 4K video seamlessly.
- **First-Run Setup Wizard**: Mobile onboarding dialog helps users configure their preferred device role on first launch with instant setting persistence.

### 🎮 100% Remote DPAD Navigation for Android TV
- **Top Glass Dock Bar**: Translucent floating navigation bar fixed at `TopCenter` on Android TV screens.
- **Tactile Focus Feedback**: Y-axis and X-axis remote navigation triggers a glowing sapphire border and a responsive `1.08x` spring-loaded lens zoom (`FluidMotion.LensSpring`).
- **Leanback Launcher Integration**: Android TV home screen launcher support (`LEANBACK_LAUNCHER`).

### ⚡ Non-Blocking Java NIO Byte-Channel Streaming
- Custom embedded HTTP server utilizes `FileChannel.transferTo` in 256KB chunked byte allocations.
- Zero CPU spikes or device heating during prolonged 4K HDR playback.
- Full `CORS`, `Accept-Ranges`, and `Range` byte-seeking support for desktop HTML5 browser playback.

### 🌐 System-Responsive Localization (EN / TR)
- Automatic locale matching between English (`res/values/strings.xml`) and Turkish (`res/values-tr/strings.xml`).

---

## 🛠️ Tech Stack & Architecture

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
- **Video Engine**: AndroidX Media3 ExoPlayer with gesture HUDs (brightness/volume drags).
- **I/O Engine**: Java NIO `FileChannel.transferTo` socket streaming.

---

## 🎨 Inspiration & Design Credits

GenPlay draws design and architectural inspiration from industry leaders:

- **Plex & Jellyfin**: Decoupled media server/client architecture, REST session management, and local Wi-Fi pairing.
- **Apple TV & visionOS**: Spatial glassmorphism, floating translucent docks, and spring-loaded lens micro-interactions.
- **Fluid AI Design System**: Soft glowing ambient halos (`#6C9BFF` Soft Sapphire), dark space gradients (`#0B101D`), and tactile DPAD TV navigation.

---

## 🚀 Getting Started

### Prerequisites
- Android Studio Ladybug or newer
- JDK 17+
- Android SDK 34 (`minSdk = 24`, `targetSdk = 34`)

### Build Debug APK
```bash
# Clone the repository
git clone https://github.com/example/genplay.git
cd genplay

# Assemble Debug APK
gradle assembleDebug
```

The output APK will be generated at:
`app/build/outputs/apk/debug/app-debug.apk`

---

<p align="center">
  Crafted with ❤️ for seamless home media streaming across Android Mobile, Web, and Android TV.
</p>
