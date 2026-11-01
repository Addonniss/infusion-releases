# INFUSION

INFUSION is a personal-media player for Android TV: your own Jellyfin server, the
Stremio-compatible add-ons you install yourself, your watch history and your artwork in one
TV-first app. No account, no telemetry, no catalog of its own.

**This repository holds release metadata and signed installers, not the application source
code.** INFUSION's development source repository is private. Downloading an installer here does
not make that source public and does not grant permission to modify or redistribute INFUSION.
See [Copyright and permissions](#copyright-and-permissions).

## Download

Installers are published only on the Releases page of this repository:

**<https://github.com/Addonniss/infusion-releases/releases>**

Open the newest release and download both files attached to it:

- `infusion-tv-<version>-<versionCode>.apk` — the installer;
- `SHA256SUMS` — the checksums for it.

Use that address — not a mirror, a re-upload, a "modded" build or a link someone sent you.

## Install (Android TV, sideloaded)

INFUSION is not distributed through an app store. Installing it is a normal sideload on a TV
you own.

### With Downloader (easiest)

**7197071**

That is INFUSION's permanent Downloader code. It opens
<https://infusionplayer.stream/download/>, the project's own download page.

1. Install Downloader by AFTVnews on your Android TV, from the Google Play store listing at
   <https://play.google.com/store/apps/details?id=com.esaba.downloader>.
2. Open Downloader, enter the code above, and choose the newest version on the page it opens.
3. Let Downloader download and install the APK. If Android asks, allow it to install unknown
   apps — that is Android's own protection, not an INFUSION setting.
4. Open INFUSION and complete first-run setup. Add a Jellyfin connection and/or an add-on only
   if you want one.

### With adb (a computer on the same network)

1. On the TV, enable **Developer options** (Settings → System → About → tap *Build* seven
   times), then enable **USB debugging** and/or **Network debugging**.
2. From the computer, connect with `adb connect <tv-ip>:5555` and then run
   `adb install -r infusion-tv-<version>-<versionCode>.apk`.
3. Open INFUSION and complete first-run setup.

Upgrades install over the top with the same command (`-r`). Updates are installed by hand at
this stage; no app store will notify you.

## What INFUSION is

- **Home is yours** — Continue Watching, Up Next, Recently Watched, a Spotlight hero you can
  switch off, and rows you can show, hide, reorder and rename.
- **Discover and Search** across the metadata add-ons you install, with per-row control of
  what appears where.
- **Jellyfin** — browse your own server's libraries, films, shows, episodes and music, with
  your own watch state.
- **Playback** — resume across sources, seek/FF/REW, audio and subtitle selection, HDR and
  Dolby Vision aware presentation, and Next Episode continuation.
- **Add-ons** — install, enable, disable, remove, restore and rename Stremio-compatible
  add-ons from the TV.
- **Optional extras** — Trakt, Simkl and MDBList tracking, community ratings with your own
  OMDb key, profiles, and a local-network page for entering credentials from a phone.
- **Quiet by design** — no account, no analytics, no advertising identifier, and HTTPS by
  default.

**It is not a content service.** INFUSION hosts, indexes and supplies nothing: no catalog, no
index, no bundled media. It is not affiliated with, or endorsed by, Jellyfin, Stremio, TMDB,
OMDb, Simkl, Trakt, MDBList, TheIntroDB or any add-on author.

Published builds are **public alpha** builds: early, subject to change, and capable of
breaking. Back up anything you would mind losing.

## Requirements

- An Android TV device running **Android 8.0 (API 26) or newer**. The primary qualification
  target is the NVIDIA Shield.
- No account is needed. There is no INFUSION sign-in.
- Optional, and entirely up to you: a Jellyfin server (yours) and/or the add-ons you choose
  to install. You can install and run INFUSION without either, but there will be nothing to
  play until at least one source is connected.

There is a mobile build in the same codebase, but **no mobile installer is published**. Do not
install the TV build on a phone.

## Verify before you install

```sh
sha256sum infusion-tv-<version>-<versionCode>.apk      # must equal the line in SHA256SUMS
apksigner verify --print-certs infusion-tv-<version>-<versionCode>.apk
```

The first digest identifies the file you downloaded; the certificate digest the second command
prints identifies who signed it. Both are stated in that release's notes. A file whose checksum
differs, or whose signer differs, is not an INFUSION build, whatever it claims.

## Support and privacy

- **Support:** <https://infusionplayer.stream/support/>
- **Privacy:** <https://infusionplayer.stream/privacy/>
- **Security:** report a vulnerability privately, never in a public Issue — the scope and the
  reporting channel are in [`SECURITY.md`](SECURITY.md).

## Copyright and permissions

Copyright © 2026 INFUSION. All rights reserved.

INFUSION is distributed as a proprietary application and the application source repository
remains private. No permission to copy, modify, redistribute or create derivative works of
INFUSION is granted by this repository, except as expressly authorized by the rights holder or
applicable law. Installing and using an official APK does not grant rights to its source. The
full notice is [`COPYRIGHT.md`](COPYRIGHT.md).

## Third-party notices

The bundled components keep their own licences — the Apache License 2.0 and the JSON License —
and the services INFUSION talks to keep their attribution terms. The full texts are in
[`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) and are also shown inside the app.
