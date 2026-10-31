# INFUSION — releases

Official downloads for **INFUSION**, a personal-media player for Android TV.

**This repository contains no source code.** INFUSION is free software under the **GNU
General Public License, version 3 (GPL-3.0)**, and its source repository is private for now.
What lives here is release metadata only: the release notes and the signed installer attached
to each GitHub Release. There is nothing to build or fork here; how the corresponding source is
made available to whoever receives a build is described in
[Licence and source availability](#licence-and-source-availability).

## Release status

**No INFUSION build has been published yet.** The first public alpha is still being prepared,
so this repository currently holds no releases, no tags and no assets. Nothing here announces a
date for that.

When the first build is published, it appears on the Releases page as a prerelease, and the
product site at <https://infusionplayer.stream> reads its version, file name and checksum from
the release itself rather than transcribing them.

## Download

Installers are published only on the Releases page of this repository:

**<https://github.com/Addonniss/infusion-releases/releases>**

Once a release exists:

- open the newest release on that page;
- download the asset named `infusion-tv-<version>-<versionCode>.apk`;
- download `SHA256SUMS` from the same release.

Use the address above — not a mirror, a re-upload, a "modded" build or a link someone sent
you. The checksum and the signing certificate below are what actually prove an installer is
ours; the page you got it from does not.

## Verify before you install

```sh
sha256sum infusion-tv-<version>-<versionCode>.apk      # must match the line in SHA256SUMS
```

Optionally check the signer with the Android SDK:

```sh
apksigner verify --print-certs infusion-tv-<version>-<versionCode>.apk
```

The certificate SHA-256 digest printed by that command must match the one stated in the
release notes. A build with a different signer is not an INFUSION build, whatever it
claims.

## Requirements

- An Android TV device running **Android 8.0 (API 26) or newer**. The primary qualification
  target is the NVIDIA Shield.
- No account is needed. There is no INFUSION sign-in.
- Optional, and entirely up to you: a Jellyfin server (yours) and/or the add-ons you choose
  to install. You can install and run INFUSION without either, but there will be nothing to
  play until at least one source is connected.

There is a mobile build in the same codebase, but **no mobile installer is published** for
the first release. Do not install the TV build on a phone.

## Install (Android TV, sideloaded)

INFUSION is not distributed through an app store. Installing it is a normal sideload:

1. On the TV, enable **Developer options** (Settings → System → About → tap *Build* seven
   times), then enable **USB debugging** and/or **Network debugging**.
2. Either:
   - **on the device:** install a file downloader from the store (for example *Downloader*),
     open the Releases page in it, and download the `.apk`; or
   - **from a computer on the same network:** `adb connect <tv-ip>:5555`, then
     `adb install -r infusion-tv-<version>-<versionCode>.apk`.
3. When Android asks, grant the file manager permission to install unknown apps. This is
   Android's own protection; it is not an INFUSION setting.
4. Open INFUSION and complete first-run setup. Add a Jellyfin connection and/or an add-on
   only if you want one.

Upgrades install over the top with the same command (`-r`). Do **not** expect app stores to
notify you: updates are installed manually at this stage.

## What INFUSION is, and what it is not

**It is** a TV-native player and browser for media you are entitled to: your own Jellyfin
server, and the add-ons you install yourself.

**It is not** a content service. It hosts, indexes and supplies nothing — no catalog, no
index, no bundled media. There is no INFUSION account, no telemetry and no analytics, and
it is not affiliated with, or endorsed by, Jellyfin, Stremio, TMDB, OMDb, Simkl, Trakt,
MDBList, TheIntroDB or any add-on author.

Published builds are **public alpha** builds: early, subject to change, and capable of
breaking. Back up anything you would mind losing.

## Licence and source availability

The INFUSION application is **free software** under the **GNU General Public License, version
3 (GPL-3.0)**. The full text travels with every release as [`LICENSE`](LICENSE). Under it you
may run the program for any purpose, study and change it, and redistribute copies — including
modified builds — provided the GPL-3.0 conditions are met.

**The source repository is private for now.** That is a hosting choice, not a licence
restriction: GPL-3.0 does not require a public repository, but it does require that anyone who
receives a distributed binary can obtain the **corresponding source for that build**. Before
the first installer is published, the mechanism used to satisfy GPL-3.0 §6 for that build —
for example publishing the corresponding source, or a written offer to supply it — is recorded
in the release notes for that build. A published build whose notes do not identify its
corresponding source is not a compliant INFUSION release.

The application licence does **not** automatically cover everything else: the website, the
wordmark and artwork, the marketing text in this repository, and the INFUSION name are
separate materials. No licence is granted for those beyond what is quoted here from
third-party licences, and third-party components keep their own terms.

## Third-party notices

The bundled components keep their own licences (the Apache License 2.0 and the JSON License)
and the services INFUSION talks to keep their attribution terms. The full texts are in
[`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) and are also shown inside the app.

## Security

Report a vulnerability **privately**, never in a public Issue — the reporting channel and
scope are in [`SECURITY.md`](SECURITY.md).
