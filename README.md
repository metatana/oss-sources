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
| Linux desktop, x64 | FFmpeg and FFprobe (`ffmpeg`, `ffprobe`), MetaTana's own build without DVD support | GPL 3.0 (built with `--enable-gpl --enable-version3`) | Same FFmpeg commit, built in `ghcr.io/btbn/ffmpeg-builds/linux64-gpl-8.1@sha256:1a82e5045a79cd997d54f6753c432068fec38f10255e7c4a6e938f268b4ae722` (image created 2026-10-17T18:56:00Z) | `metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-linux64-gpl-nodvd.tar.xz` (attached to this release) | `d1e716495e525859bfbfa86d4516a496978fd891112627e22b113dc77773dbcd` |
| Linux desktop, ARM64 | FFmpeg and FFprobe, MetaTana's own build without DVD support | GPL 3.0 | Same FFmpeg commit, built in `ghcr.io/btbn/ffmpeg-builds/linuxarm64-gpl-8.1@sha256:44154241edbd83dba37e6f152de72277d34382bfe0b76863c0801a6ed9a38771` (image created 2026-10-17T18:35:17Z) | `metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-linuxarm64-gpl-nodvd.tar.xz` (attached to this release) | `27e3b2b7eea25c666b6437ce1ff2df007a94d33a931499030ccff81a1a4c8672` |
| macOS desktop, Apple silicon (arm64) | FFmpeg and FFprobe (`MetaTana.app/Contents/Resources/media-tools/ffmpeg`, `ffprobe`), MetaTana's own build without DVD support | GPL 3.0 (built with `--enable-gpl --enable-version3`) | Same FFmpeg commit, built on macOS with Martin Riedl's FFmpeg build script ([gitlab.com/martinr92/ffmpeg](https://gitlab.com/martinr92/ffmpeg), Apache 2.0) at commit `8ba9125bd30d13e3b01103e2145abd0e74250032`; minimum macOS 12.0 | `metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-macosarm64-gpl-nodvd.tar.xz` (attached to this release) | `a972f28ef6242d0a2c834b2142da9b10673b504a9d6a247764a1396a0ab0cc13` |
| Docker image, amd64 and arm64 | FFmpeg and FFprobe and their libraries, from Debian 12's own packages: `ffmpeg`, `libavcodec59`, `libavdevice59`, `libavfilter8`, `libavformat59`, `libavutil57`, `libpostproc56`, `libswresample4`, `libswscale6`, all `7:5.1.9-0+deb12u1` | GPL 2.0 or later (Debian's build) | Debian source package `ffmpeg` `7:5.1.9-0+deb12u1` (upstream FFmpeg 5.1.9), also on [snapshot.debian.org](https://snapshot.debian.org/package/ffmpeg/7%3A5.1.9-0%2Bdeb12u1/) | Source attached here: `ffmpeg_5.1.9-0+deb12u1.dsc`, `ffmpeg_5.1.9.orig.tar.xz` (+ `.asc`), `ffmpeg_5.1.9-0+deb12u1.debian.tar.xz` | orig `d9b593bb2ba93d4b50f74177e0cdcd41747e708596367deed0c30348a71dd176`, debian `71b20472ecd2764bc98e3229d34c0f7c8dcfe4a6cbacc23fd5604c23bac04632` |
| Desktop (macOS, Linux) and Docker image | libvips and the libraries built into it, through sharp 0.35.5 (`@img/sharp-libvips-*` 1.3.4) | libvips: LGPL 2.1 or later, used under LGPL 3.0. Other bundled libraries: see below | libvips 8.18.7; lovell/sharp-libvips tag `v1.3.4` (commit `ebb95f8add54eee8bed840e3fb587e4cbec857d7`) | npm `@img/sharp-libvips-<platform>@1.3.4` | See npm |
| Windows desktop | libvips and the libraries built into it, through sharp 0.35.5 (`@img/sharp-win32-x64`, `@img/sharp-win32-arm64`) | As above | libvips 8.18.7; libvips/build-win64-mxe tag `v8.18.7` (commit `ef19ca09af2453d127453d677c849ccb37cf5694`) | `vips-dev-x64-web-8.18.7-static.zip`, `vips-dev-arm64-web-8.18.7-static.zip` | x64 `a736af61d3b46499760efa606e469cb14e060445b1f6fd36a1fa2e75009e1197`, arm64 `701d49f773fca3995d39215643d72b9e0495e02bf60980dd40ca1af59581f575` |
| Desktop (Windows, macOS, Linux) | Chromium's FFmpeg library inside Electron 41.10.7 (`ffmpeg.dll`, `libffmpeg.dylib`, `libffmpeg.so`) | LGPL 2.1 or later | Electron `v41.10.7` (commit `435871a3d6548767986da8caeaf35b14cb3ee28c`); Chromium `146.0.7680.216`; `chromium/third_party/ffmpeg` commit `ae11d2ba5c835b822a61d6a99eeb853ca30d41d8`, with Electron's patch in `metatana-2.0.0/electron-41.10.7/patches/ffmpeg/` | Part of the Electron 41.10.7 runtime | n/a |

**Windows FFmpeg build.** MetaTana builds FFmpeg for Windows itself. The build runs FFmpeg's `configure` and `make` inside BtbN's prebuilt dependency images (pinned by digest above), which contain every library already compiled. It uses the image's own configure options plus `--disable-libdvdread --disable-libdvdnav --disable-liboapv`. The exact steps are in `metatana-ffmpeg-nodvd-build.sh` (run inside the image as `/build.sh`), `metatana-ffmpeg-nodvd-driver.sh` and `metatana-btbn-build-sh-nodvd.patch`. The full configure lines read from the built programs are in `configure-line-win64.txt` and `configure-line-winarm64.txt`. MetaTana ships only `ffmpeg.exe` and `ffprobe.exe` from the zip, with the GPL 3.0 text next to them as `LICENSE.txt` (sha256 `8ceb4b9ee5adedde47b31e975c1d90c73ad27b6b165a1dcd80c7c545eb65b903`).

**Linux FFmpeg build.** The Linux build uses the same method in BtbN's Linux images (pinned by digest above), with the same three extra options. The steps are in `metatana-ffmpeg-nodvd-build-linux.sh` (the Windows build script with one optional switch, `NOBLURAY`, left off for 2.0.0) and `metatana-ffmpeg-nodvd-driver-linux.sh`. The configure lines are in `configure-line-linux64.txt` and `configure-line-linuxarm64.txt`. Each tar.xz holds `bin/ffmpeg`, `bin/ffprobe`, `LICENSE.txt` (the same GPL 3.0 text) and `SOURCE.txt`. The programs link every library statically except glibc and `libgcc_s`, which they load from the system, and need glibc 2.28 or later.

**macOS FFmpeg build.** MetaTana builds FFmpeg for macOS on Apple silicon with Martin Riedl's FFmpeg build script, pinned to commit `8ba9125bd30d`. The script downloads each library's source release and builds it from source as a static library, then builds FFmpeg against them. MetaTana's patch to the script (`metatana-riedl-build-script-macos.patch`) builds the same FFmpeg commit as the other platforms, adds `--enable-version3 --disable-libdvdread --disable-libdvdnav --disable-liboapv`, pins x264 to commit `0480cb05fa18`, builds libbluray 1.5.0, and fixes two download and linker problems. `metatana-ffmpeg-nodvd-build-macos.sh` runs the whole build in a clean environment, so nothing from Homebrew or `/usr/local` is linked. rav1e is skipped and Decklink stays off. The configure line is in `configure-line-macosarm64.txt`. The tar.xz holds `bin/ffmpeg`, `bin/ffprobe`, `LICENSE.txt` (the same GPL 3.0 text) and `SOURCE.txt`. The programs load only macOS system libraries and frameworks, and need macOS 12.0 or later (the minimum of Electron 41). The MetaTana app build signs them with the app's Developer ID.

**DVD libraries are not included.** MetaTana's FFmpeg does not contain libdvdcss, libdvdread or libdvdnav, and has no DVD-Video reader (dvdvideo demuxer). `proof-win64.txt`, `proof-winarm64.txt`, `proof-linux64.txt`, `proof-linuxarm64.txt` and `proof-macosarm64.txt` record the check: no libdvdcss or dvdcss strings in any of the programs, and `CONFIG_DVDVIDEO_DEMUXER` is 0. OpenAPV is also not linked (`--disable-liboapv`).

**BtbN revision.** The images do not record which BtbN FFmpeg-Builds commit built them. The sources here follow BtbN commit `9acad4a9ef1583096af7836cc1e9c8cbcb4d3950` (2026-10-03T13:35:22Z), the last commit on BtbN's master branch before the images were created. That revision is inferred from the dates, not read from the images. Every library version in the images' pkg-config files was checked against the source trees at that revision (details in `image-checks/` inside the library-sources archive).

The Linux images were built on 2026-10-17, when BtbN's master branch was at commit `63ac3265b0789ea16c7b1f8351cd2ad195a28722`. Its `scripts.d` folder, which pins every library's repository and commit, is identical to the one at `9acad4a9ef15`; the only changes add a loongarch64 target. So the libraries the Linux images share with the Windows images are at the same commits and are covered by the Windows library-sources archive. The Linux-only libraries (X11 and XCB, libglvnd, PulseAudio, libdrm and libpciaccess) are in `metatana-ffmpeg-nodvd-linux-library-sources-btbn-63ac3265b078.tar.xz`, with its own `image-checks/`.

The Docker image installs Debian's ffmpeg packages unchanged from Debian's archive. Its `/licenses/SOURCE.txt` names the source package and version; Debian's copyright file is at `/usr/share/doc/ffmpeg/copyright` and the licence texts are in `/usr/share/common-licenses`. Debian's ffmpeg links to other Debian library packages; their source is covered by the Debian section below.

### Source archives in the metatana-2.0.0 release

| Archive | What it holds | Size (bytes) | sha256 |
|---|---|---|---|
| `ffmpeg-n8.1.2-34-g9b6c8969e0-source.tar.gz` | FFmpeg source for the Windows, Linux and macOS builds, at commit `9b6c8969e05b4f0b29f0f85cd501be6b3e582e6b` | 16903934 | `7e779215eae16ad7e93ddad59bd82822bd3d34e4dc61f9996f9481b2c0605bc3` |
| `FFmpeg-Builds-9acad4a9ef1583096af7836cc1e9c8cbcb4d3950.tar.gz` | BtbN FFmpeg-Builds scripts at commit `9acad4a9ef15` (inferred revision of the build images). They pin the exact repository and commit of every library and give the configure options | 108488 | `27dca8db7b2466b6f5145168721264de91dc9b56f50bebc441249f92e4acf548` |
| `metatana-ffmpeg-nodvd-windows-library-sources-btbn-9acad4a9ef15.tar.xz` | The source of every library in the win64 and winarm64 build images at that revision, at the pinned commits, including submodules, glib's proxy-libintl, the Opus model data and the Rust crates for rav1e and librsvg. It leaves out libdvdcss, libdvdread and libdvdnav. `SOURCES.md` inside lists each one | 792748368 | `34ccf4ab864b9b7be07c675bb023d12128d7db4624ebc047728acfbd7a297888` |
| `metatana-ffmpeg-nodvd-build.sh`, `metatana-ffmpeg-nodvd-driver.sh`, `metatana-btbn-build-sh-nodvd.patch` | MetaTana's build steps for the Windows FFmpeg | 1711, 787, 798 | `9cc048791656c7e8cdff41566c901bd91873036bfe100c6f093d95f58b2121b8`, `14a603823009740c0a01890b92628480868d74260a19626e2f91e933ccaa9d37`, `2c5468298d30ea2d3b4801ffc8165c57c998a4dce8052223416f5662d7bd1c14` |
| `configure-line-win64.txt`, `configure-line-winarm64.txt` | FFmpeg configure lines read from the built programs | 2020, 2066 | `a8f604cc6baea9cb85dc9d6430759e7e49949147cccaa27509877dcdece5dd86`, `ced399d2faa40e3b52b3923bdfe66301f38e4aa6c20007c7914ffcbf1524f93d` |
| `proof-win64.txt`, `proof-winarm64.txt` | Build record: image digest, FFmpeg commit and the DVD check | 2927, 2940 | `6b5571e40ea03cb61f125f3e0a33fc94af6b6e6eb6f049eec188a9f16bb6c477`, `54b12814af3778865bb7bfd3e669c1c297a8941221cca4d23c53c87b9bc0e173` |
| `FFmpeg-Builds-63ac3265b0789ea16c7b1f8351cd2ad195a28722.tar.gz` | BtbN FFmpeg-Builds scripts at commit `63ac3265b078` (inferred revision of the Linux build images; same `scripts.d` as `9acad4a9ef15`) | 116749 | `4fd8856d5b207fce5c870a690aefc9a72b9a1943cfc79df8d5d327ec4612c9d2` |
| `metatana-ffmpeg-nodvd-linux-library-sources-btbn-63ac3265b078.tar.xz` | The source of the libraries that only the linux64 and linuxarm64 images contain (X11 and XCB, libglvnd, PulseAudio, libdrm, libpciaccess, xorg-macros), at the pinned commits. The other libraries are in the Windows library-sources archive. `SOURCES.md` inside lists each one | 5054028 | `cc88f02f31ec865a717168332a4935928559945d71607544cc77ea8204aaf30b` |
| `metatana-ffmpeg-nodvd-build-linux.sh`, `metatana-ffmpeg-nodvd-driver-linux.sh` | MetaTana's build steps for the Linux FFmpeg | 1781, 1823 | `39a08d03beb8f27cbc0c241a5679fdac1e8a24e4e7ca0e8c0917ab2eb97a127f`, `8dbf7e5378996300d94191e091b6f3ba2a947460eb1cca624e71922ef03ca8f2` |
| `configure-line-linux64.txt`, `configure-line-linuxarm64.txt` | FFmpeg configure lines read from the built Linux programs | 2036, 2060 | `c3a914889e43db4be4e80d30bb42c71fc1db6159085c64d708b0c6976ed0ab53`, `fcf89ce0a020e90b45f557a46a87f8636d1ab0db526172250bf2470bc202d792` |
| `proof-linux64.txt`, `proof-linuxarm64.txt` | Linux build record: image digest, FFmpeg commit, the DVD check, linked libraries and glibc version | 7494, 4827 | `ba8c250a04e269ee812268911a40b1bee126c9c3951d12b3257849ebce9bb233`, `c7e3c05b02aa0117775f7a94e8e4c47020795a8e69f2cb95ba23833a3d485ee1` |
| `martinr92-ffmpeg-build-script-8ba9125bd30d13e3b01103e2145abd0e74250032.tar.gz` | Martin Riedl's FFmpeg build script at commit `8ba9125bd30d`, used for the macOS build. It gives every library's version and download address and the configure options | 2609618 | `1f7cbe1bf13b63c05b74131fd366d6e0e13229bd5de762543a29c376d111d3b8` |
| `metatana-ffmpeg-nodvd-macos-library-sources-riedl-8ba9125bd30d.tar.xz` | Every source archive the macOS build downloaded, unchanged: the 31 libraries linked into FFmpeg and the nasm, ninja and pkg-config build tools. It leaves out libdvdcss, libdvdread and libdvdnav, which the build never downloads. `SOURCES.md` inside lists each file with its download address and sha256 | 277568512 | `61d5f122fa4eba260a2d854ab0e2af702b8e9bcfb899e287bdd46a8e801cc3b6` |
| `metatana-ffmpeg-nodvd-build-macos.sh`, `metatana-riedl-build-script-macos.patch` | MetaTana's build steps for the macOS FFmpeg | 8138, 5705 | `433ab9a244c71c152a587bbf0cdc2bf5759ba7034a6986f7a8cb3dd429af3510`, `1aab1300187ad014a7f754cf620f0612ff4913b11b8fe3cec0ec371a4408a9c6` |
| `configure-line-macosarm64.txt` | FFmpeg configure line read from the built macOS programs | 685 | `8dfbe5551c375da7ba1e7fbd68b81895b9efaeb12fe382b5b09185bc4a14c735` |
| `proof-macosarm64.txt` | macOS build record: build host and compiler, FFmpeg commit, library versions, the DVD check, linked libraries, minimum macOS and a test encode | 11821 | `297c91d1b94b26c96d7aa1ef2bce28d49e22a5ba87dc8da2ce0b124762ac596c` |
| `ffmpeg_5.1.9-0+deb12u1.dsc`, `ffmpeg_5.1.9.orig.tar.xz` (+ `.asc`), `ffmpeg_5.1.9-0+deb12u1.debian.tar.xz` | Debian source package for the Docker image's ffmpeg | 5323, 10034840 (520), 53444 | `055f82fca9a92f1d47216be2c2488d09373c7ca154806fbc36b0127c191d5104`, `d9b593bb2ba93d4b50f74177e0cdcd41747e708596367deed0c30348a71dd176` (`443e6cdfe1560aab22f90ec40a967866ee04d5bbea32bc32625bd6e514d589f4`), `71b20472ecd2764bc98e3229d34c0f7c8dcfe4a6cbacc23fd5604c23bac04632` |
| `sharp-libvips-v1.3.4.tar.gz` | lovell/sharp-libvips build scripts at tag `v1.3.4` | 24490 | `65fdb633c2d97626352a3771b7a0ce30b6a89af03d2a1238491c8b068e6b8dad` |
| `vips-8.18.7.tar.xz` | libvips 8.18.7 source release, unchanged from upstream | 25425084 | `5baaead3b0bb20ffdb9e9ff09aa9fda08620923df77b63b436654cb5e0b3bf94` |
| `sharp-libvips-v1.3.4-dependency-sources.tar.xz` | Every source archive and patch the sharp-libvips v1.3.4 build downloads, plus the Rust crates librsvg builds with | 183824336 | `a7b241b403c945a6e9b081e9356eba54757912b4ab14b12ebf68d8b14627af79` |
| `build-win64-mxe-v8.18.7.tar.gz` | libvips/build-win64-mxe build recipes at tag `v8.18.7`, used for the Windows libvips | 65766 | `f52864572e6df6e549016369fdb2705aa195a837bd7bc8c52e45f42b59ef97a7` |
| `chromium-third_party-ffmpeg-ae11d2ba5c835b822a61d6a99eeb853ca30d41d8.tar.xz` | Chromium's FFmpeg at the commit Electron 41.10.7 uses, including Chromium's build files and configuration | 11527704 | `7ed6ec517dff66590713881416a4a6efeaa1921b58a1e0809b74f945d8338bce` |

### Libraries in the Windows, Linux and macOS FFmpeg builds

The Windows build links many libraries into FFmpeg statically, for example x264, x265, libvpx, dav1d, aom, SVT-AV1, libass, freetype, harfbuzz, libxml2, OpenSSL and zlib. Some are only in one of the two targets. [`metatana-2.0.0/ffmpeg-library-sources.md`](metatana-2.0.0/ffmpeg-library-sources.md) lists every library with its repository, commit and targets. The library-sources archive holds each one.

The Linux builds link the same libraries plus X11 and XCB, libglvnd, PulseAudio, libdrm and libpciaccess, and leave out the Windows-only ones. They link glibc dynamically, so MetaTana does not distribute it. GCC's libstdc++ and libgcc are under the GCC Runtime Library Exception.

The macOS build links a smaller set, each built from its source release as a static library: aom, dav1d, fontconfig, freetype, fribidi, harfbuzz, lame, libass, libbluray (with libudfread), libklvanc, libogg, libtheora, libvmaf, libvorbis, libwebp, libxml2, openh264, OpenJPEG, OpenSSL (libcrypto, for SRT), Opus, SDL 2, snappy, SRT, SVT-AV1, libvpx, vvenc, x264, x265, zimg, zlib and zvbi. The versions are in [`metatana-2.0.0/ffmpeg-library-sources.md`](metatana-2.0.0/ffmpeg-library-sources.md). The programs load only macOS system libraries and frameworks (libSystem, libc++, libiconv, libbz2, libobjc and Apple frameworks), which MetaTana does not distribute.

The Windows build also includes the mingw-w64 runtime, which is in the library-sources archive. The compiler runtime libraries (GCC's libgcc and libstdc++ for x64, LLVM's libc++, libunwind and compiler-rt for ARM64) are under licences with runtime exceptions.

### Libraries in libvips

`@img/sharp-libvips-*` 1.3.4 contains libvips 8.18.7 and these libraries, built into one shared library (versions from [`metatana-2.0.0/sharp-libvips-1.3.4-versions.properties`](metatana-2.0.0/sharp-libvips-1.3.4-versions.properties)):

aom 3.15.1, libarchive 3.8.9, cairo 1.18.6, cgif 0.5.4, libexif 0.6.26, expat 2.8.5, libffi 3.8.0, fontconfig 2.18.3, freetype 2.14.3, fribidi 1.0.17, glib 2.90.0, harfbuzz 14.5.0, libheif 1.23.5, highway 1.4.0, libimagequant 2.4.1, lcms 2.19.1, mozjpeg 0826579, pango 1.58.2, pixman 0.46.4, libpng 1.6.58, proxy-libintl 0.5, librsvg 2.63.2, libtiff 4.7.2, libultrahdr 2.0.2, libwebp 1.6.0, libxml2 2.15.4 and zlib-ng 2.3.3.

The LGPL libraries among them are libvips, glib, pango, librsvg, libheif, libexif, fribidi and proxy-libintl. Each npm package's `THIRD-PARTY-NOTICES.md` lists every library's licence. MetaTana loads libvips as a shared library, so you can replace it with your own build.

### Still to add

The Windows libvips build gets its libraries through build-win64-mxe and MXE. Their source archives are not attached to the release yet. They are the same libraries as above, at the versions pinned in build-win64-mxe `v8.18.7`. Until they are attached, email support@watari.dev and we will send them under the written offer below.

## How to rebuild

These steps are a short guide. Each upstream project's README has the full details.

**FFmpeg (Windows).** On a Linux machine with Docker, pull the image for your target by the digest in the table above. Run `metatana-ffmpeg-nodvd-build.sh` inside it as `/build.sh` with a writable `/ffbuild` folder mounted, as `metatana-ffmpeg-nodvd-driver.sh` does. The script checks out FFmpeg commit `9b6c8969e0` (the same tree as `ffmpeg-n8.1.2-34-g9b6c8969e0-source.tar.gz`) and builds it against the libraries in the image. To rebuild the libraries too, unpack `FFmpeg-Builds-9acad4a9ef1583096af7836cc1e9c8cbcb4d3950.tar.gz`, apply `metatana-btbn-build-sh-nodvd.patch`, and run `./makeimage.sh <target> gpl 8.1` and then `./build.sh <target> gpl 8.1`, where `<target>` is `win64` or `winarm64`. The scripts download each library from its upstream repository at the pinned commit. If an upstream repository has moved, use the same tree from the library-sources archive.

**FFmpeg (Linux).** The same steps as for Windows, with `metatana-ffmpeg-nodvd-build-linux.sh` and `metatana-ffmpeg-nodvd-driver-linux.sh` and the image digests for `linux64` and `linuxarm64` above. To rebuild the libraries, use `FFmpeg-Builds-63ac3265b0789ea16c7b1f8351cd2ad195a28722.tar.gz` with `<target>` `linux64` or `linuxarm64`.

**FFmpeg (macOS).** On a Mac with Apple silicon, the Xcode Command Line Tools and GNU autoconf, automake and libtool, run `bash metatana-ffmpeg-nodvd-build-macos.sh <work-folder> ffmpeg-n8.1.2-34-g9b6c8969e0-source.tar.gz metatana-riedl-build-script-macos.patch`. It checks out the build script at commit `8ba9125bd30d` (the same tree as `martinr92-ffmpeg-build-script-8ba9125bd30d13e3b01103e2145abd0e74250032.tar.gz`), applies the patch and builds every library and FFmpeg. The script downloads each library from its upstream address; if one has moved, use the same file from the macOS library-sources archive. The result is the same tar.xz layout as the one attached. Replace `ffmpeg` and `ffprobe` in `MetaTana.app/Contents/Resources/media-tools/` with your build. Changing files inside the app breaks its code signature, so sign the app again afterwards, for example with `codesign --force --deep --sign - MetaTana.app`.

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
