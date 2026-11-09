# Telegram File Explorer for Android

An app for a personal file library kept in a **private Telegram channel**. The phone
app browses, streams, opens, downloads and uploads those files, and keeps the desktop
app's folders, tags, collections, stars and PIN.

The same Python backend that runs on the PC runs inside the APK (Chaquopy), so there
is no server to host: the phone talks to Telegram directly over your own account.

## Download

Get the APK from [Releases](../../releases/latest):
**`TelegramFileExplorer-Android-3.13.34.apk`**

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
  playback speed, online subtitle search, PiP, screen lock and fit-to-screen. Playback
  starts before a download finishes.
- **3D models** — STL, OBJ, PLY and 3MF in an orbit/zoom viewer.
- **Images** — zoom, pan and slideshow.
- **Uploads** — pick one or more files; they are saved into the folder you are
  browsing (up to 2 GB per file). Larger files need the desktop app, which splits
  them into parts.
- **Downloads** — saved to **Downloads/Telegram Files** through Android's download
  manager. Split part files are joined automatically. The transfers bar above the tabs
  shows upload and download speed, size and progress, and can pause, resume, cancel,
  clear or open a download. Multi-select downloads several files as one ZIP.
- **Library index** — when the app opens it restores the vault's latest snapshot, and
  on close (Back) it saves a fresh one with "Saving the library to Telegram…". The
  archive is staged in app-private storage and overwritten with zeros, then deleted,
  right after it is unpacked or uploaded, so your Downloads folder never collects it.
- **Top bar** — search, sync, select and a one-tap lock (shown when a PIN is set).
- **More** — storage vault, sort, tags, collections, stars, hidden files, sync now,
  full re-scan, **clear cache**, **lock now**, remove/set PIN, About and sign out.

## Privacy and security

- Sign-in uses your own Telegram session; the app never asks for, reads or stores a bot
  token. The Telegram session stays in the app's private storage on the phone.
- The local API server used by the interface listens on `127.0.0.1` only.
- The PIN is hashed and stored with the library. **Forgot PIN?** can reset it with a
  6-digit code sent to your own Saved Messages.
- Uploads go straight into your own channel. The app never deletes files, and library
  snapshots are only managed from the desktop app.
- Downloads are only written when you ask for them. **Clear cache** removes streaming
  and preview files and never touches your Telegram files, library or downloads.

## Where data lives

| Location | Contents |
|---|---|
| App-private storage | Telegram session, library index, settings, PIN, thumbnails, cache, staging for the index archive |
| `Downloads/Telegram Files` | Completed downloads |
| Your Telegram channel | The files themselves and the library snapshot |

## Version history

- **3.13.34** — vault switching no longer stays blocked after a finished transfer;
  folder delete removes the folder and everything inside.
- **3.13.33** — deleting a folder removes the folder, every subfolder and all of
  their files from Telegram in one step, with a single Delete button.
- **3.13.31** — opens in seconds: the library restores from Telegram in the
  background; vault picker on the PIN screen, batch rename, bulk stars, tag
  manager, larger caches, VLC-style playback controls and PDF fixes.
- **3.13.8** — uploads, library index restored on open and saved on close, faster
  transfers, playback before the download finishes.
- **3.12.2** — star lookups use IAFD, then IMDb, then Wikipedia.
- **3.12.1** — star type tabs and portrait picker.
- **3.11.3** — one-tap lock button; More → **Clear cache**.
- **3.11.2** — downloads bar with pause, resume and cancel.
