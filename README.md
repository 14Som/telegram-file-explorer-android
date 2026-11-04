# Telegram File Explorer for Android

A read-only viewer for a personal file library kept in a **private Telegram channel**.
The phone app streams, opens and downloads those files, and keeps the desktop app's
folders, tags, collections, stars and PIN. Uploads are disabled by design — use the
[desktop app](https://github.com/14Som/telegram-file-bot-v2) to add files.

The same Python backend that runs on the PC runs inside the APK (Chaquopy), so there
is no server to host: the phone talks to Telegram directly over your own account.

## Download

Get the APK from [Releases](../../releases/latest):
**`TelegramFileExplorer-Android-3.11.3.apk`**

- Android 7.0 (API 24) or newer, **arm64** phone (an x86_64 emulator build is included
  in the same APK).
- The APK is signed with a release key, but it is not distributed through Google Play,
  so Android shows an unknown-app warning: allow *Install unknown apps* for your
  browser/file manager and continue.
- Updates install over the old version without uninstalling, as long as they are
  signed with the same key. Your session, library and connections are kept.

## First run

1. Open the app and sign in to **your own Telegram account** — *QR code* (Telegram →
   Settings → Devices → *Link Desktop Device*) or the *Phone code* tab.
2. Pick the **storage vault** — the private channel that holds your files.
3. Tap sync. The first sync indexes the channel on the phone.
4. Set or enter the **4-digit PIN**. It is stored with the library, so the same PIN
   also unlocks the desktop app.

## What it does

- **Browse** — files and folders with All / Images / Videos / Audio / Docs filters,
  search, sort, breadcrumbs, and the detail sheet for every file.
- **Organize** — tags, collections, stars, hidden files, and saved folder assignments
  come from the desktop app and travel in vault snapshots.
- **Read documents** — EPUB/EPUB3, FB2, PDF, DOC/DOCX, HTML/XML, Markdown and TXT with
  contents, search, bookmarks, highlights and notes, themes and read-aloud.
- **Play video and audio** — libVLC plays MKV, HEVC and everything else natively, with
  embedded and sidecar subtitles (including a `Subs` folder), audio-track switching,
  playback speed, online subtitle search, PiP, screen lock and fit-to-screen.
- **3D models** — STL, OBJ, PLY and 3MF in an orbit/zoom viewer.
- **Images** — zoom, pan and slideshow.
- **Downloads** — saved to **Downloads/Telegram Files** through Android's download
  manager. Split part files are joined automatically. A downloads bar above the tabs
  shows speed, size and progress, and can pause, resume, cancel, clear or open a
  transfer. Multi-select downloads several files as one ZIP.
- **Top bar** — search, sync, select and a one-tap lock (shown when a PIN is set).
- **More** — storage vault, sort, tags, collections, stars, hidden files, sync now,
  full re-scan, **clear cache**, **lock now**, remove/set PIN, About and sign out.

## Privacy and security

- Sign-in uses your own Telegram session; the app never asks for, reads or stores a bot
  token. The Telegram session stays in the app's private storage on the phone.
- The local API server used by the interface listens on `127.0.0.1` only.
- The PIN is hashed and stored with the library. **Forgot PIN?** can reset it with a
  6-digit code sent to your own Saved Messages.
- The app is read-only: there are no upload controls, and the backend rejects uploads
  when running on Android.
- Downloads are only written when you ask for them. **Clear cache** removes streaming
  and preview files and never touches your Telegram files, library or downloads.

## Where data lives

| Location | Contents |
|---|---|
| App-private storage | Telegram session, library index, settings, PIN, thumbnails, cache |
| `Downloads/Telegram Files` | Completed downloads |
| Your Telegram channel | The files themselves and the library snapshot |

## Version history

- **3.11.3** — top bar: the duplicate hamburger is now a one-tap lock button;
  More → **Clear cache**.
- **3.11.2** — downloads bar with pause, resume and cancel.
- **3.11.0** — multi-select and ZIP downloads.
- **3.10.0** — libVLC player with subtitles and audio tracks, 3D viewer, IMDb details.
- **3.7.1** — desktop folder sync, read-only vault snapshots, long-name fixes.

## Build from source

The Android app lives in the main repository:
[`android/` in telegram-file-bot-v2](https://github.com/14Som/telegram-file-bot-v2/tree/main/android).
You need JDK 17, Android SDK 35 and Python 3.13:

```bat
set TFE_BUILD_PYTHON=C:\Path\To\Python313\python.exe
cd android
gradlew.bat assembleRelease
```

The signed APK is written to
`android\app\build\outputs\apk\release\app-release.apk`. Signing reads
`android/app/keystore.properties`, which is not published — a debug build works for
testing but cannot replace the release APK without uninstalling it first.

## Related

- [Desktop app and storage bot](https://github.com/14Som/telegram-file-bot-v2) —
  Windows Explorer, uploads, folders, stars and the bot on your server.
- [Older v1 repository](https://github.com/14Som/telegram-file-explorer) — archived
  version 1 builds.
