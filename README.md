# MetaTana open-source component sources

This repository holds the source code for the third-party open-source components that ship inside MetaTana, a media manager made by Watari Labs Pty Ltd. Some of these components are licensed under the GNU General Public License (GPL) or the GNU Lesser General Public License (LGPL). Those licences give everyone who receives MetaTana the right to get the complete corresponding source code of those components. This repository is where we provide it.

MetaTana's own code is proprietary. It is not in this repository and is not covered by these licences. The components listed here are separate programs and libraries written by their own authors. Watari Labs does not own them, and their copyright belongs to their authors.

## Where the source is

Each MetaTana release that ships these components has a matching GitHub release in this repository. The large source archives are attached to that release as downloads. Each archive has a `.sha256` file next to it.

| MetaTana release | Source release |
|---|---|
| 2.0.0 | [metatana-2.0.0](https://github.com/metatana/oss-sources/releases/tag/metatana-2.0.0) |

The `metatana-2.0.0/` folder in this repository holds the small reference files for that release: the list of every library in the FFmpeg builds, the libvips library versions, Electron's FFmpeg patch and build settings, and `SHA256SUMS` for the release archives.

The `licenses/` folder holds the licence texts: GPL 2.0, GPL 3.0, LGPL 2.1 and LGPL 3.0.

## MetaTana 2.0.0

### Components per MetaTana artifact

| MetaTana artifact | Component | Licence | Upstream version and commit | Upstream binary asset | Asset sha256 |
|---|---|---|---|---|---|
| Windows desktop, x64 | FFmpeg and FFprobe (`resources/media-tools/ffmpeg.exe`, `ffprobe.exe`), from the BtbN FFmpeg Builds `win64-gpl-8.1` build | GPL 3.0 (built with `--enable-gpl --enable-version3`) | FFmpeg `n8.1.2-34-g9b6c8969e0` (commit `9b6c8969e05b4f0b29f0f85cd501be6b3e582e6b`, branch `release/8.1`); BtbN build scripts tag `autobuild-2026-07-31-14-10` (commit `a99e8230eae00d1cee38f23076a7a1f55cd984e2`) | `ffmpeg-n8.1.2-34-g9b6c8969e0-win64-gpl-8.1.zip` | `cc4156d51387566ea8ba653fc3a04897bdf812fddf652428d9030bbf7ae24835` |
| Windows desktop, ARM64 | FFmpeg and FFprobe, BtbN `winarm64-gpl-8.1` build | GPL 3.0 | Same FFmpeg commit and BtbN tag as above | `ffmpeg-n8.1.2-34-g9b6c8969e0-winarm64-gpl-8.1.zip` | `abf3b41c200ce5346b9bb5be6fe634c4720d891778d8921f7b36b76d002b3c96` |
| Docker image, amd64 | FFmpeg and FFprobe (`/usr/local/bin/ffmpeg`, `/usr/local/bin/ffprobe`), BtbN `linux64-gpl-8.1` build | GPL 3.0 | Same FFmpeg commit and BtbN tag as above | `ffmpeg-n8.1.2-34-g9b6c8969e0-linux64-gpl-8.1.tar.xz` | `09fc77be269c7053e438b7e96548e4af97604faf96a42c4a3c56a1ad74c22c0a` |
| Docker image, arm64 | FFmpeg and FFprobe, BtbN `linuxarm64-gpl-8.1` build | GPL 3.0 | Same FFmpeg commit and BtbN tag as above | `ffmpeg-n8.1.2-34-g9b6c8969e0-linuxarm64-gpl-8.1.tar.xz` | `177e40c91564dec3840096f3bf1ffe696b94330585972462cfc739fa29fe0e1a` |
| Desktop (macOS, Linux) and Docker image | libvips and the libraries built into it, through sharp 0.35.5 (`@img/sharp-libvips-*` 1.3.4) | libvips: LGPL 2.1 or later, used under LGPL 3.0. Other bundled libraries: see below | libvips 8.18.7; lovell/sharp-libvips tag `v1.3.4` (commit `ebb95f8add54eee8bed840e3fb587e4cbec857d7`) | npm `@img/sharp-libvips-<platform>@1.3.4` | See npm |
| Windows desktop | libvips and the libraries built into it, through sharp 0.35.5 (`@img/sharp-win32-x64`, `@img/sharp-win32-arm64`) | As above | libvips 8.18.7; libvips/build-win64-mxe tag `v8.18.7` (commit `ef19ca09af2453d127453d677c849ccb37cf5694`) | `vips-dev-x64-web-8.18.7-static.zip`, `vips-dev-arm64-web-8.18.7-static.zip` | x64 `a736af61d3b46499760efa606e469cb14e060445b1f6fd36a1fa2e75009e1197`, arm64 `701d49f773fca3995d39215643d72b9e0495e02bf60980dd40ca1af59581f575` |
| Desktop (Windows, macOS, Linux) | Chromium's FFmpeg library inside Electron 41.10.7 (`ffmpeg.dll`, `libffmpeg.dylib`, `libffmpeg.so`) | LGPL 2.1 or later | Electron `v41.10.7` (commit `435871a3d6548767986da8caeaf35b14cb3ee28c`); Chromium `146.0.7680.216`; `chromium/third_party/ffmpeg` commit `ae11d2ba5c835b822a61d6a99eeb853ca30d41d8`, with Electron's patch in `metatana-2.0.0/electron-41.10.7/patches/ffmpeg/` | Part of the Electron 41.10.7 runtime | n/a |

The FFmpeg files in MetaTana are the upstream files from the archives above, unchanged. MetaTana copies only `ffmpeg` and `ffprobe` out of each archive. The same GPL 3.0 text ships next to them in MetaTana (`LICENSE.txt` on Windows, `/licenses/GPL-3.0.txt` in the Docker image, sha256 `8ceb4b9ee5adedde47b31e975c1d90c73ad27b6b165a1dcd80c7c545eb65b903`).

macOS and Linux desktop builds do not include FFmpeg or FFprobe programs. They use the copy the user installs.

### Source archives in the metatana-2.0.0 release

| Archive | What it holds | Size (bytes) | sha256 |
|---|---|---|---|
| `ffmpeg-n8.1.2-34-g9b6c8969e0-source.tar.gz` | FFmpeg source at commit `9b6c8969e05b4f0b29f0f85cd501be6b3e582e6b` | 16903934 | `7e779215eae16ad7e93ddad59bd82822bd3d34e4dc61f9996f9481b2c0605bc3` |
| `FFmpeg-Builds-autobuild-2026-07-31-14-10.tar.gz` | BtbN FFmpeg Builds scripts at tag `autobuild-2026-07-31-14-10`. They pin the exact repository and commit of every library and give the configure options | 101671 | `7deac4a5190b2be84d4d548db2885d05152f9e3d77069d0e34841a46efd95e2b` |
| `ffmpeg-builds-autobuild-2026-07-31-14-10-library-sources.tar.xz` | The source of every library those scripts build into the win64, winarm64, linux64 and linuxarm64 gpl 8.1 builds, at the pinned commits, including submodules and rav1e's Rust crates. `SOURCES.md` inside lists each one | 574337160 | `6016a3ed63d959190077af8b093f637ca87c53e6699470a2ea62aa7c54f4e5d4` |
| `sharp-libvips-v1.3.4.tar.gz` | lovell/sharp-libvips build scripts at tag `v1.3.4` | 24490 | `65fdb633c2d97626352a3771b7a0ce30b6a89af03d2a1238491c8b068e6b8dad` |
| `vips-8.18.7.tar.xz` | libvips 8.18.7 source release, unchanged from upstream | 25425084 | `5baaead3b0bb20ffdb9e9ff09aa9fda08620923df77b63b436654cb5e0b3bf94` |
| `sharp-libvips-v1.3.4-dependency-sources.tar.xz` | Every source archive and patch the sharp-libvips v1.3.4 build downloads, plus the Rust crates librsvg builds with | 183824336 | `a7b241b403c945a6e9b081e9356eba54757912b4ab14b12ebf68d8b14627af79` |
| `build-win64-mxe-v8.18.7.tar.gz` | libvips/build-win64-mxe build recipes at tag `v8.18.7`, used for the Windows libvips | 65766 | `f52864572e6df6e549016369fdb2705aa195a837bd7bc8c52e45f42b59ef97a7` |
| `chromium-third_party-ffmpeg-ae11d2ba5c835b822a61d6a99eeb853ca30d41d8.tar.xz` | Chromium's FFmpeg at the commit Electron 41.10.7 uses, including Chromium's build files and configuration | 11527704 | `7ed6ec517dff66590713881416a4a6efeaa1921b58a1e0809b74f945d8338bce` |

### Libraries in the FFmpeg builds

The BtbN gpl builds link many libraries into FFmpeg statically, for example x264, x265, libvpx, dav1d, aom, SVT-AV1, libass, freetype, harfbuzz, libxml2, OpenSSL and zlib. Some are only in some targets. [`metatana-2.0.0/ffmpeg-library-sources.md`](metatana-2.0.0/ffmpeg-library-sources.md) lists every library with its repository, commit and targets. The library-sources archive holds each one.

The Windows builds also include the mingw-w64 runtime, which is in the library-sources archive. The GCC runtime libraries linked into the builds are covered by the GCC Runtime Library Exception. The Linux builds link the C library (glibc) dynamically from the Docker image.

### Libraries in libvips

`@img/sharp-libvips-*` 1.3.4 contains libvips 8.18.7 and these libraries, built into one shared library (versions from [`metatana-2.0.0/sharp-libvips-1.3.4-versions.properties`](metatana-2.0.0/sharp-libvips-1.3.4-versions.properties)):

aom 3.15.1, libarchive 3.8.9, cairo 1.18.6, cgif 0.5.4, libexif 0.6.26, expat 2.8.5, libffi 3.8.0, fontconfig 2.18.3, freetype 2.14.3, fribidi 1.0.17, glib 2.90.0, harfbuzz 14.5.0, libheif 1.23.5, highway 1.4.0, libimagequant 2.4.1, lcms 2.19.1, mozjpeg 0826579, pango 1.58.2, pixman 0.46.4, libpng 1.6.58, proxy-libintl 0.5, librsvg 2.63.2, libtiff 4.7.2, libultrahdr 2.0.2, libwebp 1.6.0, libxml2 2.15.4 and zlib-ng 2.3.3.

The LGPL libraries among them are libvips, glib, pango, librsvg, libheif, libexif, fribidi and proxy-libintl. Each npm package's `THIRD-PARTY-NOTICES.md` lists every library's licence. MetaTana loads libvips as a shared library, so you can replace it with your own build.

### Still to add

The Windows libvips build gets its libraries through build-win64-mxe and MXE. Their source archives are not attached to the release yet. They are the same libraries as above, at the versions pinned in build-win64-mxe `v8.18.7`. Until they are attached, email support@watari.dev and we will send them under the written offer below.

## How to rebuild

These steps are a short guide. Each upstream project's README has the full details.

**FFmpeg (Windows and Docker).** Unpack `FFmpeg-Builds-autobuild-2026-07-31-14-10.tar.gz` on a Linux machine with Docker. Run `./makeimage.sh <target> gpl 8.1` and then `./build.sh <target> gpl 8.1`, where `<target>` is `win64`, `winarm64`, `linux64` or `linuxarm64`. The scripts download each library from its upstream repository at the pinned commit. If an upstream repository has moved, use the same tree from the library-sources archive. The FFmpeg source in the release is the same commit the build uses from the `release/8.1` branch.

**libvips (macOS, Linux, Docker).** Unpack `sharp-libvips-v1.3.4.tar.gz` and run `./build.sh <platform>`, for example `linux-x64`, `linux-arm64v8` or `darwin-arm64v8`. The build downloads the files saved in the dependency-sources archive. Replace the built library in MetaTana's `node_modules/@img/sharp-libvips-<platform>/lib/` folder.

**libvips (Windows).** Unpack `build-win64-mxe-v8.18.7.tar.gz` and run `./build.sh --help` for the options. The Windows packages use the `web` static build for x64 and arm64.

**Chromium's FFmpeg (Electron).** Check out Electron `v41.10.7` with its build tools, following Electron's build instructions. That checks out Chromium `146.0.7680.216` and `third_party/ffmpeg` at commit `ae11d2ba5c835b822a61d6a99eeb853ca30d41d8`, the same tree as the archive in the release, and applies the patch in `metatana-2.0.0/electron-41.10.7/patches/ffmpeg/`. Electron builds it as a separate shared library with `is_component_ffmpeg = true`, `ffmpeg_branding = "Chrome"` and `proprietary_codecs = true` (see `metatana-2.0.0/electron-41.10.7/build/args/`). Replace the FFmpeg library in the MetaTana app folder with your build.

## Docker image base packages

The MetaTana Docker image is based on the official Node.js Debian slim image. It contains Debian packages (105 in MetaTana 2.0.0). The copyright and licence file for each package is in the image under `/usr/share/doc/<package>/copyright`. Debian publishes the source of every package version at [snapshot.debian.org](https://snapshot.debian.org) and [sources.debian.org](https://sources.debian.org). You can also ask us for the source of the exact package versions in an image under the written offer below.

## Written offer

MetaTana includes software licensed under the GNU GPL and the GNU LGPL. For at least three years after we last distribute a MetaTana release, Watari Labs Pty Ltd will give anyone who has a copy of that release the complete corresponding source code of the GPL and LGPL components in it, including the Debian packages in the Docker image. We will provide it either as a download at no charge or on a physical medium for no more than our cost of making and sending it.

To ask for it, email support@watari.dev and name the MetaTana version and platform (Windows, macOS, Linux or Docker).

## Contact

Questions about this repository or about open-source licences in MetaTana: support@watari.dev
