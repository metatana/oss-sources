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
| Windows desktop, x64 | FFmpeg and FFprobe (`resources/media-tools/ffmpeg.exe`, `ffprobe.exe`), MetaTana's own build without DVD support | GPL 3.0 (built with `--enable-gpl --enable-version3`) | FFmpeg `n8.1.2-34-g9b6c8969e0` (commit `9b6c8969e05b4f0b29f0f85cd501be6b3e582e6b`, branch `release/8.1`), built in `ghcr.io/btbn/ffmpeg-builds/win64-gpl-8.1@sha256:79ffe8aa0a517bb5a4fbeb718c798b88033b1d853e82b0e936ee4edd95a0f2be` (image created 2026-10-04T18:52:58Z) | `metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-win64-gpl-nodvd.zip` (attached to this release) | `9c638d5bf2bf929073baae650275c53d2a1520952c6a7708698ce2179a2412e5` |
| Windows desktop, ARM64 | FFmpeg and FFprobe, MetaTana's own build without DVD support | GPL 3.0 | Same FFmpeg commit, built in `ghcr.io/btbn/ffmpeg-builds/winarm64-gpl-8.1@sha256:d971707f2d695ab57314bd5107da8eeb4206ffdbc51a6a82a8fa55751ff1ed8d` (image created 2026-10-04T17:22:47Z) | `metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-winarm64-gpl-nodvd.zip` (attached to this release) | `2d1e707dd2a822e3faa2ea913fd0fbe2db6c37a7ce439717c70313c9b6f93777` |
| Docker image, amd64 and arm64 | FFmpeg and FFprobe and their libraries, from Debian 12's own packages: `ffmpeg`, `libavcodec59`, `libavdevice59`, `libavfilter8`, `libavformat59`, `libavutil57`, `libpostproc56`, `libswresample4`, `libswscale6`, all `7:5.1.9-0+deb12u1` | GPL 2.0 or later (Debian's build) | Debian source package `ffmpeg` `7:5.1.9-0+deb12u1` (upstream FFmpeg 5.1.9), also on [snapshot.debian.org](https://snapshot.debian.org/package/ffmpeg/7%3A5.1.9-0%2Bdeb12u1/) | Source attached here: `ffmpeg_5.1.9-0+deb12u1.dsc`, `ffmpeg_5.1.9.orig.tar.xz` (+ `.asc`), `ffmpeg_5.1.9-0+deb12u1.debian.tar.xz` | orig `d9b593bb2ba93d4b50f74177e0cdcd41747e708596367deed0c30348a71dd176`, debian `71b20472ecd2764bc98e3229d34c0f7c8dcfe4a6cbacc23fd5604c23bac04632` |
| Desktop (macOS, Linux) and Docker image | libvips and the libraries built into it, through sharp 0.35.5 (`@img/sharp-libvips-*` 1.3.4) | libvips: LGPL 2.1 or later, used under LGPL 3.0. Other bundled libraries: see below | libvips 8.18.7; lovell/sharp-libvips tag `v1.3.4` (commit `ebb95f8add54eee8bed840e3fb587e4cbec857d7`) | npm `@img/sharp-libvips-<platform>@1.3.4` | See npm |
| Windows desktop | libvips and the libraries built into it, through sharp 0.35.5 (`@img/sharp-win32-x64`, `@img/sharp-win32-arm64`) | As above | libvips 8.18.7; libvips/build-win64-mxe tag `v8.18.7` (commit `ef19ca09af2453d127453d677c849ccb37cf5694`) | `vips-dev-x64-web-8.18.7-static.zip`, `vips-dev-arm64-web-8.18.7-static.zip` | x64 `a736af61d3b46499760efa606e469cb14e060445b1f6fd36a1fa2e75009e1197`, arm64 `701d49f773fca3995d39215643d72b9e0495e02bf60980dd40ca1af59581f575` |
| Desktop (Windows, macOS, Linux) | Chromium's FFmpeg library inside Electron 41.10.7 (`ffmpeg.dll`, `libffmpeg.dylib`, `libffmpeg.so`) | LGPL 2.1 or later | Electron `v41.10.7` (commit `435871a3d6548767986da8caeaf35b14cb3ee28c`); Chromium `146.0.7680.216`; `chromium/third_party/ffmpeg` commit `ae11d2ba5c835b822a61d6a99eeb853ca30d41d8`, with Electron's patch in `metatana-2.0.0/electron-41.10.7/patches/ffmpeg/` | Part of the Electron 41.10.7 runtime | n/a |

**Windows FFmpeg build.** MetaTana builds FFmpeg for Windows itself. The build runs FFmpeg's `configure` and `make` inside BtbN's prebuilt dependency images (pinned by digest above), which contain every library already compiled. It uses the image's own configure options plus `--disable-libdvdread --disable-libdvdnav --disable-liboapv`. The exact steps are in `metatana-ffmpeg-nodvd-build.sh` (run inside the image as `/build.sh`), `metatana-ffmpeg-nodvd-driver.sh` and `metatana-btbn-build-sh-nodvd.patch`. The full configure lines read from the built programs are in `configure-line-win64.txt` and `configure-line-winarm64.txt`. MetaTana ships only `ffmpeg.exe` and `ffprobe.exe` from the zip, with the GPL 3.0 text next to them as `LICENSE.txt` (sha256 `8ceb4b9ee5adedde47b31e975c1d90c73ad27b6b165a1dcd80c7c545eb65b903`).

**DVD libraries are not included.** MetaTana's FFmpeg does not contain libdvdcss, libdvdread or libdvdnav, and has no DVD-Video reader (dvdvideo demuxer). `proof-win64.txt` and `proof-winarm64.txt` record the check: no libdvdcss or dvdcss strings in either program, and `CONFIG_DVDVIDEO_DEMUXER` is 0. OpenAPV is also not linked (`--disable-liboapv`).

**BtbN revision.** The images do not record which BtbN FFmpeg-Builds commit built them. The sources here follow BtbN commit `9acad4a9ef1583096af7836cc1e9c8cbcb4d3950` (2026-10-03T13:35:22Z), the last commit on BtbN's master branch before the images were created. That revision is inferred from the dates, not read from the images. Every library version in the images' pkg-config files was checked against the source trees at that revision (details in `image-checks/` inside the library-sources archive).

The Docker image installs Debian's ffmpeg packages unchanged from Debian's archive. Its `/licenses/SOURCE.txt` names the source package and version; Debian's copyright file is at `/usr/share/doc/ffmpeg/copyright` and the licence texts are in `/usr/share/common-licenses`. Debian's ffmpeg links to other Debian library packages; their source is covered by the Debian section below.

macOS and Linux desktop builds do not include FFmpeg or FFprobe programs. They use the copy the user installs.

### Source archives in the metatana-2.0.0 release

| Archive | What it holds | Size (bytes) | sha256 |
|---|---|---|---|
| `ffmpeg-n8.1.2-34-g9b6c8969e0-source.tar.gz` | FFmpeg source for the Windows build, at commit `9b6c8969e05b4f0b29f0f85cd501be6b3e582e6b` | 16903934 | `7e779215eae16ad7e93ddad59bd82822bd3d34e4dc61f9996f9481b2c0605bc3` |
| `FFmpeg-Builds-9acad4a9ef1583096af7836cc1e9c8cbcb4d3950.tar.gz` | BtbN FFmpeg-Builds scripts at commit `9acad4a9ef15` (inferred revision of the build images). They pin the exact repository and commit of every library and give the configure options | 108488 | `27dca8db7b2466b6f5145168721264de91dc9b56f50bebc441249f92e4acf548` |
| `metatana-ffmpeg-nodvd-windows-library-sources-btbn-9acad4a9ef15.tar.xz` | The source of every library in the win64 and winarm64 build images at that revision, at the pinned commits, including submodules, glib's proxy-libintl, the Opus model data and the Rust crates for rav1e and librsvg. It leaves out libdvdcss, libdvdread and libdvdnav. `SOURCES.md` inside lists each one | 792748368 | `34ccf4ab864b9b7be07c675bb023d12128d7db4624ebc047728acfbd7a297888` |
| `metatana-ffmpeg-nodvd-build.sh`, `metatana-ffmpeg-nodvd-driver.sh`, `metatana-btbn-build-sh-nodvd.patch` | MetaTana's build steps for the Windows FFmpeg | 1711, 787, 798 | `9cc048791656c7e8cdff41566c901bd91873036bfe100c6f093d95f58b2121b8`, `14a603823009740c0a01890b92628480868d74260a19626e2f91e933ccaa9d37`, `2c5468298d30ea2d3b4801ffc8165c57c998a4dce8052223416f5662d7bd1c14` |
| `configure-line-win64.txt`, `configure-line-winarm64.txt` | FFmpeg configure lines read from the built programs | 2020, 2066 | `a8f604cc6baea9cb85dc9d6430759e7e49949147cccaa27509877dcdece5dd86`, `ced399d2faa40e3b52b3923bdfe66301f38e4aa6c20007c7914ffcbf1524f93d` |
| `proof-win64.txt`, `proof-winarm64.txt` | Build record: image digest, FFmpeg commit and the DVD check | 2927, 2940 | `6b5571e40ea03cb61f125f3e0a33fc94af6b6e6eb6f049eec188a9f16bb6c477`, `54b12814af3778865bb7bfd3e669c1c297a8941221cca4d23c53c87b9bc0e173` |
| `ffmpeg_5.1.9-0+deb12u1.dsc`, `ffmpeg_5.1.9.orig.tar.xz` (+ `.asc`), `ffmpeg_5.1.9-0+deb12u1.debian.tar.xz` | Debian source package for the Docker image's ffmpeg | 5323, 10034840 (520), 53444 | `055f82fca9a92f1d47216be2c2488d09373c7ca154806fbc36b0127c191d5104`, `d9b593bb2ba93d4b50f74177e0cdcd41747e708596367deed0c30348a71dd176` (`443e6cdfe1560aab22f90ec40a967866ee04d5bbea32bc32625bd6e514d589f4`), `71b20472ecd2764bc98e3229d34c0f7c8dcfe4a6cbacc23fd5604c23bac04632` |
| `sharp-libvips-v1.3.4.tar.gz` | lovell/sharp-libvips build scripts at tag `v1.3.4` | 24490 | `65fdb633c2d97626352a3771b7a0ce30b6a89af03d2a1238491c8b068e6b8dad` |
| `vips-8.18.7.tar.xz` | libvips 8.18.7 source release, unchanged from upstream | 25425084 | `5baaead3b0bb20ffdb9e9ff09aa9fda08620923df77b63b436654cb5e0b3bf94` |
| `sharp-libvips-v1.3.4-dependency-sources.tar.xz` | Every source archive and patch the sharp-libvips v1.3.4 build downloads, plus the Rust crates librsvg builds with | 183824336 | `a7b241b403c945a6e9b081e9356eba54757912b4ab14b12ebf68d8b14627af79` |
| `build-win64-mxe-v8.18.7.tar.gz` | libvips/build-win64-mxe build recipes at tag `v8.18.7`, used for the Windows libvips | 65766 | `f52864572e6df6e549016369fdb2705aa195a837bd7bc8c52e45f42b59ef97a7` |
| `chromium-third_party-ffmpeg-ae11d2ba5c835b822a61d6a99eeb853ca30d41d8.tar.xz` | Chromium's FFmpeg at the commit Electron 41.10.7 uses, including Chromium's build files and configuration | 11527704 | `7ed6ec517dff66590713881416a4a6efeaa1921b58a1e0809b74f945d8338bce` |

### Libraries in the Windows FFmpeg build

The Windows build links many libraries into FFmpeg statically, for example x264, x265, libvpx, dav1d, aom, SVT-AV1, libass, freetype, harfbuzz, libxml2, OpenSSL and zlib. Some are only in one of the two targets. [`metatana-2.0.0/ffmpeg-library-sources.md`](metatana-2.0.0/ffmpeg-library-sources.md) lists every library with its repository, commit and targets. The library-sources archive holds each one.

The build also includes the mingw-w64 runtime, which is in the library-sources archive. The compiler runtime libraries (GCC's libgcc and libstdc++ for x64, LLVM's libc++, libunwind and compiler-rt for ARM64) are under licences with runtime exceptions.

### Libraries in libvips

`@img/sharp-libvips-*` 1.3.4 contains libvips 8.18.7 and these libraries, built into one shared library (versions from [`metatana-2.0.0/sharp-libvips-1.3.4-versions.properties`](metatana-2.0.0/sharp-libvips-1.3.4-versions.properties)):

aom 3.15.1, libarchive 3.8.9, cairo 1.18.6, cgif 0.5.4, libexif 0.6.26, expat 2.8.5, libffi 3.8.0, fontconfig 2.18.3, freetype 2.14.3, fribidi 1.0.17, glib 2.90.0, harfbuzz 14.5.0, libheif 1.23.5, highway 1.4.0, libimagequant 2.4.1, lcms 2.19.1, mozjpeg 0826579, pango 1.58.2, pixman 0.46.4, libpng 1.6.58, proxy-libintl 0.5, librsvg 2.63.2, libtiff 4.7.2, libultrahdr 2.0.2, libwebp 1.6.0, libxml2 2.15.4 and zlib-ng 2.3.3.

The LGPL libraries among them are libvips, glib, pango, librsvg, libheif, libexif, fribidi and proxy-libintl. Each npm package's `THIRD-PARTY-NOTICES.md` lists every library's licence. MetaTana loads libvips as a shared library, so you can replace it with your own build.

### Still to add

The Windows libvips build gets its libraries through build-win64-mxe and MXE. Their source archives are not attached to the release yet. They are the same libraries as above, at the versions pinned in build-win64-mxe `v8.18.7`. Until they are attached, email support@watari.dev and we will send them under the written offer below.

## How to rebuild

These steps are a short guide. Each upstream project's README has the full details.

**FFmpeg (Windows).** On a Linux machine with Docker, pull the image for your target by the digest in the table above. Run `metatana-ffmpeg-nodvd-build.sh` inside it as `/build.sh` with a writable `/ffbuild` folder mounted, as `metatana-ffmpeg-nodvd-driver.sh` does. The script checks out FFmpeg commit `9b6c8969e0` (the same tree as `ffmpeg-n8.1.2-34-g9b6c8969e0-source.tar.gz`) and builds it against the libraries in the image. To rebuild the libraries too, unpack `FFmpeg-Builds-9acad4a9ef1583096af7836cc1e9c8cbcb4d3950.tar.gz`, apply `metatana-btbn-build-sh-nodvd.patch`, and run `./makeimage.sh <target> gpl 8.1` and then `./build.sh <target> gpl 8.1`, where `<target>` is `win64` or `winarm64`. The scripts download each library from its upstream repository at the pinned commit. If an upstream repository has moved, use the same tree from the library-sources archive.

**FFmpeg (Docker).** Debian builds the `ffmpeg` package from the attached source package with `dpkg-buildpackage` on Debian 12.

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
