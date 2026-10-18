# Library sources for MetaTana's Windows FFmpeg build without DVD support

MetaTana 2.0.0 ships its own FFmpeg build for Windows (`metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-win64-gpl-nodvd.zip` and `metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-winarm64-gpl-nodvd.zip`). It was built inside BtbN's prebuilt dependency images:

- win64: `ghcr.io/btbn/ffmpeg-builds/win64-gpl-8.1@sha256:79ffe8aa0a517bb5a4fbeb718c798b88033b1d853e82b0e936ee4edd95a0f2be` (created 2026-10-04T18:52:58Z)
- winarm64: `ghcr.io/btbn/ffmpeg-builds/winarm64-gpl-8.1@sha256:d971707f2d695ab57314bd5107da8eeb4206ffdbc51a6a82a8fa55751ff1ed8d` (created 2026-10-04T17:22:47Z)

The images do not record which BtbN FFmpeg-Builds commit built them. This archive follows BtbN commit `9acad4a9ef1583096af7836cc1e9c8cbcb4d3950` (2026-10-03T13:35:22Z), the last commit on BtbN's master branch before the images were created. That revision is inferred from the dates.

Each folder matches a script in `scripts.d` of the BtbN scripts at that commit. `srcN` is the Nth repository the script pins, checked out at the pinned commit with git metadata removed. Submodules, shaderc's DEPS checkouts, glib's proxy-libintl subproject (`subprojects/packagecache`), the Opus model data file, and the Rust crates for rav1e and librsvg (`cargo-vendor`) are included the way the build scripts fetch them.

Not included, because MetaTana's FFmpeg does not contain them:

- libdvdcss, libdvdread and libdvdnav. MetaTana's build configures FFmpeg with `--disable-libdvdread --disable-libdvdnav`, so FFmpeg links none of the DVD libraries. The images still contain them, but they are not part of MetaTana's FFmpeg.
- curl and its helper libraries, and zstd. BtbN disables curl for FFmpeg 8.1, and the images do not contain these libraries.

OpenAPV is included because it is in the images, but MetaTana's build also uses `--disable-liboapv`, so FFmpeg does not link it.

`image-checks/` holds the FFmpeg configure lines read from the two built programs, and a check of every pkg-config version in each image against these source trees. 130 of 147 (win64) and 124 of 137 (winarm64) versions appear as text in the pinned sources. The others are versions the build computes from git history or libtool numbers (for example x264 `0.165.x`, freetype `26.6.20`). They were checked by hand against the same trees.

The toolchains come from BtbN's base images: GCC with mingw-w64 for win64 and llvm-mingw for winarm64. The mingw-w64 runtime is rebuilt by `10-mingw` and is included here. The compiler runtime libraries (GCC's libgcc and libstdc++, LLVM's libc++, libunwind and compiler-rt) are under licences with runtime exceptions.

| Script | Repository | Commit or revision | Targets | Folder |
|---|---|---|---|---|
| 10-mingw-std-threads | https://github.com/meganz/mingw-std-threads.git | c931bac289dd431f1dd30fc4a5d1a7be36668073 | win64, winarm64 | 10-mingw-std-threads/src1 |
| 10-mingw | https://git.code.sf.net/p/mingw-w64/mingw-w64.git | 57b595039040eaa15bece85b7cc71d952281b269 | win64, winarm64 | 10-mingw/src1 |
| 20-libiconv | https://git.savannah.gnu.org/git/libiconv.git | 1df3087ba8110c7f3ed3eb5f8869b814dbbe00b0 | win64, winarm64 | 20-libiconv/src1 |
| 20-libiconv | https://git.savannah.gnu.org/git/gnulib.git | eb72eb6f75f5621c5d648acd11467fd124584617 | win64, winarm64 | 20-libiconv/src2 |
| 20-zlib | https://github.com/madler/zlib.git | 767c4c947852e143f582c85f14cf573411df1b35 | win64, winarm64 | 20-zlib/src1 |
| 25-fftw3 | https://github.com/FFTW/fftw3.git | 93ed4c786934aec9946f8dda4b4e3eb08f8be41c | win64, winarm64 | 25-fftw3/src1 |
| 25-fribidi | https://github.com/fribidi/fribidi.git | 4c914a92e94a9fe4f30ae83a1130099841566448 | win64, winarm64 | 25-fribidi/src1 |
| 25-gmp | https://github.com/BtbN/gmplib.git | 763b40df71c0f4d5f5d7b33dc55038c8c9377ecf | win64, winarm64 | 25-gmp/src1 |
| 25-libogg | https://github.com/xiph/ogg.git | 06a5e0262cdc28aa4ae6797627a783b5010440f0 | win64, winarm64 | 25-libogg/src1 |
| 25-libpng | https://github.com/glennrp/libpng.git | 964b4135949703b705fc760fc3fb546b86e5ab47 | win64, winarm64 | 25-libpng/src1 |
| 25-libxml2 | https://github.com/GNOME/libxml2.git | 91586dc6742ab335682235120363f6e126eea5e2 | win64, winarm64 | 25-libxml2/src1 |
| 25-openssl | https://github.com/openssl/openssl.git | d3c1b1169b3569ff3069e5b399f47b2b28e03d79 | win64, winarm64 | 25-openssl/src1 |
| 25-openssl (submodule cloudflare-quiche) | see .gitmodules | 7ab6a55cfe471267d61e4d28ba43d41defcd87e0 | win64, winarm64 | 25-openssl/src1/cloudflare-quiche |
| 25-openssl (submodule cloudflare-quiche/quiche/deps/boringssl) | see .gitmodules | f1c75347daa2ea81a941e953f2263e0a4d970c8d | win64, winarm64 | 25-openssl/src1/cloudflare-quiche/quiche/deps/boringssl |
| 25-openssl (submodule fuzz/corpora) | see .gitmodules | ce771805c094d098c25a218bc8e9f7344eccbc5a | win64, winarm64 | 25-openssl/src1/fuzz/corpora |
| 25-openssl (submodule gost-engine) | see .gitmodules | 74b1f4fddbc2d6de969815b1992ddc1ae7c643fe | win64, winarm64 | 25-openssl/src1/gost-engine |
| 25-openssl (submodule gost-engine/libprov) | see .gitmodules | 0b445c73ae1e87577430c6884cdeeca1afa36dbd | win64, winarm64 | 25-openssl/src1/gost-engine/libprov |
| 25-openssl (submodule krb5) | see .gitmodules | 784c38f50e70a739400cdd3f2620bac2e2788e6c | win64, winarm64 | 25-openssl/src1/krb5 |
| 25-openssl (submodule oqs-provider) | see .gitmodules | 7bc597c04b534ddea9b6654481deb31ded8e1bbc | win64, winarm64 | 25-openssl/src1/oqs-provider |
| 25-openssl (submodule pkcs11-provider) | see .gitmodules | 64fc325ac0f91d03d76b3546df2998d3a38c525b | win64, winarm64 | 25-openssl/src1/pkcs11-provider |
| 25-openssl (submodule pkcs11-provider/python-ecdsa) | see .gitmodules | ea9666903c109a8e88a37eb1c60d4e98f01f0299 | win64, winarm64 | 25-openssl/src1/pkcs11-provider/python-ecdsa |
| 25-openssl (submodule pkcs11-provider/tlsfuzzer) | see .gitmodules | 32fcb0d8e78fd9ffc4568d11ba5916936a46af8c | win64, winarm64 | 25-openssl/src1/pkcs11-provider/tlsfuzzer |
| 25-openssl (submodule pkcs11-provider/tlslite-ng) | see .gitmodules | 4e16574d7c52f17c81c3f5e0aa547776a67fdf8e | win64, winarm64 | 25-openssl/src1/pkcs11-provider/tlslite-ng |
| 25-openssl (submodule pyca-cryptography) | see .gitmodules | 0e855f952693c8b730abb2fc5a84dfc69562f210 | win64, winarm64 | 25-openssl/src1/pyca-cryptography |
| 25-openssl (submodule python-ecdsa) | see .gitmodules | 4096fa01715929e08b97e73f3173aee9d57f2a3f | win64, winarm64 | 25-openssl/src1/python-ecdsa |
| 25-openssl (submodule tlsfuzzer) | see .gitmodules | 61f45d9701294fd87ef92d2a7e3dfb076653a562 | win64, winarm64 | 25-openssl/src1/tlsfuzzer |
| 25-openssl (submodule tlslite-ng) | see .gitmodules | 77ef321dde1a9e6bcf94d73c80f8789a770d8031 | win64, winarm64 | 25-openssl/src1/tlslite-ng |
| 25-openssl (submodule wycheproof) | see .gitmodules | aca47066256c167f0ce04d611d718cc85654341e | win64, winarm64 | 25-openssl/src1/wycheproof |
| 25-xz | https://github.com/tukaani-project/xz.git | 3b1efb04d17c3a9ef7f473d73af13f1531428ffe | win64, winarm64 | 25-xz/src1 |
| 45-brotli | https://github.com/google/brotli.git | a3abcbee0d945e51dddeec81e647ffe0cde182c2 | win64, winarm64 | 45-brotli/src1 |
| 45-fonts/25-freetype | https://gitlab.freedesktop.org/freetype/freetype.git | d333439633039de426f943f28a2926c7f97b5ae5 | win64, winarm64 | 45-fonts/25-freetype/src1 |
| 45-fonts/35-fontconfig | https://gitlab.freedesktop.org/fontconfig/fontconfig.git | bd8f7b597de96761750d0365abb49b19d2f8d5c3 | win64, winarm64 | 45-fonts/35-fontconfig/src1 |
| 45-fonts/45-harfbuzz | https://github.com/harfbuzz/harfbuzz.git | b3bab62307017934dd7f532c52a696fefb12b3ad | win64, winarm64 | 45-fonts/45-harfbuzz/src1 |
| 45-fonts/50-freetype | https://gitlab.freedesktop.org/freetype/freetype.git | d333439633039de426f943f28a2926c7f97b5ae5 | win64, winarm64 | 45-fonts/50-freetype/src1 |
| 45-lcms2 | https://github.com/mm2/Little-CMS.git | 35cef8775e0ab46f0dda0b46aae1e69d27524432 | win64, winarm64 | 45-lcms2/src1 |
| 45-libffi | https://github.com/libffi/libffi.git | bc553867367246d140cd156f060bd0409f57f157 | win64, winarm64 | 45-libffi/src1 |
| 45-libsamplerate | https://github.com/libsndfile/libsamplerate.git | 0844c208f683527c08ea8a80acc13b398aa9c8bf | win64, winarm64 | 45-libsamplerate/src1 |
| 45-libudfread | https://code.videolan.org/videolan/libudfread.git | b0bc6957e7e07d5f35391f210596d9eb71cffdd9 | win64, winarm64 | 45-libudfread/src1 |
| 45-libunibreak | https://github.com/adah1972/libunibreak.git | 28a2756b864c343f438cd22537d49d394d4666a5 | win64, winarm64 | 45-libunibreak/src1 |
| 45-libvorbis | https://github.com/xiph/vorbis.git | 1b75110b5a2754ba1931d82dd83cb822b266a21d | win64, winarm64 | 45-libvorbis/src1 |
| 45-opencl | https://github.com/KhronosGroup/OpenCL-Headers.git | e6060189f4ebe8b52d885c37af71b9a50c272154 | win64, winarm64 | 45-opencl/src1 |
| 45-opencl | https://github.com/KhronosGroup/OpenCL-ICD-Loader.git | 5192c84f8059e5f703e5452929b613f9487f6e4c | win64, winarm64 | 45-opencl/src2 |
| 45-pcre2 | https://github.com/PCRE2Project/pcre2.git | 09eb19dc1102b34e7557408f33318364cb97d2b0 | win64, winarm64 | 45-pcre2/src1 |
| 45-pixman | https://gitlab.freedesktop.org/pixman/pixman.git | 96c04d1b87934dc4b9396197a2dff737698ab310 | win64, winarm64 | 45-pixman/src1 |
| 45-vmaf | https://github.com/Netflix/vmaf.git | 86da14d0306a138fd3f01319860b905169746516 | win64, winarm64 | 45-vmaf/src1 |
| 45-xxhash | https://github.com/Cyan4973/xxHash.git | 680bf463fa1ca0461b9a7c2dab7556e1f54cf4cf | win64, winarm64 | 45-xxhash/src1 |
| 47-vulkan/40-vulkan-headers | https://github.com/KhronosGroup/Vulkan-Headers.git | 6802bb4733b63ed5efd3adb308a6c885ef180ea1 | win64, winarm64 | 47-vulkan/40-vulkan-headers/src1 |
| 47-vulkan/45-vulkan-loader | https://github.com/BtbN/Vulkan-Shim-Loader.git | 65b3936528cd92eb4ea3de485d03f858a3850484 | win64, winarm64 | 47-vulkan/45-vulkan-loader/src1 |
| 47-vulkan/45-vulkan-loader | https://github.com/KhronosGroup/Vulkan-Headers.git | 6802bb4733b63ed5efd3adb308a6c885ef180ea1 | win64, winarm64 | 47-vulkan/45-vulkan-loader/src2 |
| 47-vulkan/50-shaderc | https://github.com/google/shaderc.git | a8abeb0b8a9d4b11e3d59ca9f4550b8213e733ab | win64, winarm64 | 47-vulkan/50-shaderc/src1 |
| 47-vulkan/50-shaderc (third_party/abseil_cpp) | https://github.com/abseil/abseil-cpp.git | dbf88f932096c7f7714356e919f04749eb87c3e9 | win64, winarm64 | 47-vulkan/50-shaderc/src1/third_party/abseil_cpp |
| 47-vulkan/50-shaderc (third_party/effcee) | https://github.com/google/effcee.git | f8e8a164822d4f65e757bff66bc00e1567959aa0 | win64, winarm64 | 47-vulkan/50-shaderc/src1/third_party/effcee |
| 47-vulkan/50-shaderc (third_party/googletest) | https://github.com/google/googletest.git | 52eb8108c5bdec04579160ae17225d66034bd723 | win64, winarm64 | 47-vulkan/50-shaderc/src1/third_party/googletest |
| 47-vulkan/50-shaderc (third_party/glslang) | https://github.com/KhronosGroup/glslang.git | e1b562a8bed273a02f30b59b66a5d499793cede5 | win64, winarm64 | 47-vulkan/50-shaderc/src1/third_party/glslang |
| 47-vulkan/50-shaderc (third_party/re2) | https://github.com/google/re2.git | 972a15cedd008d846f1a39b2e88ce48d7f166cbd | win64, winarm64 | 47-vulkan/50-shaderc/src1/third_party/re2 |
| 47-vulkan/50-shaderc (third_party/spirv-headers) | https://github.com/KhronosGroup/SPIRV-Headers.git | 04fd3caa1e8267e4d95c806cad901181728e1006 | win64, winarm64 | 47-vulkan/50-shaderc/src1/third_party/spirv-headers |
| 47-vulkan/50-shaderc (third_party/spirv-tools) | https://github.com/KhronosGroup/SPIRV-Tools.git | ef96ed763b43b59b33b31b362f09a02b729fa1c9 | win64, winarm64 | 47-vulkan/50-shaderc/src1/third_party/spirv-tools |
| 47-vulkan/55-spirv-cross | https://github.com/KhronosGroup/SPIRV-Cross.git | aa217aeb6c9f0ace7a0ab233b28807edf45eb165 | win64, winarm64 | 47-vulkan/55-spirv-cross/src1 |
| 47-vulkan/60-spirv-headers | https://github.com/KhronosGroup/SPIRV-Headers.git | 2b7475f6d664efbad4d4315c94ecec9640831e5b | win64, winarm64 | 47-vulkan/60-spirv-headers/src1 |
| 50-amf | https://github.com/GPUOpen-LibrariesAndSDKs/AMF.git | 6277e353fd625121a8f627b1d0540323ef372a49 | win64, winarm64 | 50-amf/src1 |
| 50-aom | https://aomedia.googlesource.com/aom | b4ce2cd097b00921b0327bfb5f07b5f8361ade99 | win64 | 50-aom/src1 |
| 50-avisynth | https://github.com/AviSynth/AviSynthPlus.git | 5c82777b374bdef16e13007a11e77d735ac1e4eb | win64, winarm64 | 50-avisynth/src1 |
| 50-chromaprint | https://github.com/acoustid/chromaprint.git | aed8eba2202dd9d7b3b0a56c77904cc805490d72 | win64, winarm64 | 50-chromaprint/src1 |
| 50-dav1d | https://code.videolan.org/videolan/dav1d.git | 9711965b60bb692ae24004659acf61f5c7d9ed61 | win64, winarm64 | 50-dav1d/src1 |
| 50-davs2 | https://github.com/pkuvcl/davs2.git | b41cf117452e2d73d827f02d3e30aa20f1c721ac | win64 | 50-davs2/src1 |
| 50-ffnvcodec | https://github.com/FFmpeg/nv-codec-headers.git | eddcea9e27f6b772057c9b3f87de2cc1737faffc | win64 | 50-ffnvcodec/src1 |
| 50-ffnvcodec | https://github.com/FFmpeg/nv-codec-headers.git | ced4f8eba3ba5dd431932cba17928f0dffdaeb2b | win64 | 50-ffnvcodec/src2 |
| 50-ffnvcodec | https://github.com/FFmpeg/nv-codec-headers.git | 833faee5f7b8d3f56444347c587f4aed11ee213f | win64 | 50-ffnvcodec/src3 |
| 50-frei0r | https://github.com/dyne/frei0r.git | 4c95b2a02b2d03c71d5f6d7980d16c99acfd5a5f | win64, winarm64 | 50-frei0r/src1 |
| 50-gme | https://github.com/libgme/game-music-emu.git | f68963b1de0633149b05732113d3c3113c6f63a1 | win64, winarm64 | 50-gme/src1 |
| 50-kvazaar | https://github.com/ultravideo/kvazaar.git | 2b06691bb5844404c0e703f12a5d7b0fee914ec7 | win64, winarm64 | 50-kvazaar/src1 |
| 50-lcevcdec | https://github.com/v-novaltd/LCEVCdec.git | 17804ac54db8fbb42717f3275b1e73f3c0b067d3 | win64 | 50-lcevcdec/src1 |
| 50-libaribb24 | https://github.com/nkoriyama/aribb24.git | 5e9be272f96e00f15a2f3c5f8ba7e124862aec38 | win64, winarm64 | 50-libaribb24/src1 |
| 50-libaribcaption | https://github.com/xqq/libaribcaption.git | c64c23b8905ba514b87c9789269e9f66f949ffe0 | win64, winarm64 | 50-libaribcaption/src1 |
| 50-libass | https://github.com/libass/libass.git | f61db567e6593df3470e91594bcd4ad2d0473aff | win64, winarm64 | 50-libass/src1 |
| 50-libbluray | https://code.videolan.org/videolan/libbluray.git | a24f4fad4d62893de647abc8671397747b2359dd | win64, winarm64 | 50-libbluray/src1 |
| 50-libjxl/50-libjxl | https://github.com/libjxl/libjxl.git | b87738951c1254cd8cccaa6d47712ba735da56d8 | win64, winarm64 | 50-libjxl/50-libjxl/src1 |
| 50-libjxl/50-libjxl (submodule testdata) | see .gitmodules | 73695d303670c90e4d506ea89d9901b081385089 | win64, winarm64 | 50-libjxl/50-libjxl/src1/testdata |
| 50-libjxl/50-libjxl (submodule third_party/brotli) | see .gitmodules | 028fb5a23661f123017c060daa546b55cf4bde29 | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/brotli |
| 50-libjxl/50-libjxl (submodule third_party/googletest) | see .gitmodules | 6910c9d9165801d8827d628cb72eb7ea9dd538c5 | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/googletest |
| 50-libjxl/50-libjxl (submodule third_party/highway) | see .gitmodules | 457c891775a7397bdb0376bb1031e6e027af1c48 | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/highway |
| 50-libjxl/50-libjxl (submodule third_party/lcms) | see .gitmodules | 5176347635785e53ee5cee92328f76fda766ecc6 | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/lcms |
| 50-libjxl/50-libjxl (submodule third_party/libjpeg-turbo) | see .gitmodules | 8ecba3647edb6dd940463fedf38ca33a8e2a73d1 | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/libjpeg-turbo |
| 50-libjxl/50-libjxl (submodule third_party/libpng) | see .gitmodules | 872555f4ba910252783af1507f9e7fe1653be252 | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/libpng |
| 50-libjxl/50-libjxl (submodule third_party/sjpeg) | see .gitmodules | 94e0df6d0f8b44228de5be0ff35efb9f946a13c9 | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/sjpeg |
| 50-libjxl/50-libjxl (submodule third_party/skcms) | see .gitmodules | 96d9171c94b937a1b5f0293de7309ac16311b722 | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/skcms |
| 50-libjxl/50-libjxl (submodule third_party/zlib) | see .gitmodules | 51b7f2abdade71cd9bb0e7a373ef2610ec6f9daf | win64, winarm64 | 50-libjxl/50-libjxl/src1/third_party/zlib |
| 50-libmp3lame | https://svn.code.sf.net/p/lame/svn/trunk/lame | r6835 | win64, winarm64 | 50-libmp3lame/src1 |
| 50-libopus | https://github.com/xiph/opus.git | 503d81b138d76621aae4b12786e90de48aa8db3a | win64, winarm64 | 50-libopus/src1 |
| 50-libplacebo | https://code.videolan.org/videolan/libplacebo.git | 1937beef3a2f508266c68efea1491e3fc4600e04 | win64, winarm64 | 50-libplacebo/src1 |
| 50-libplacebo (submodule 3rdparty/Vulkan-Headers) | see .gitmodules | 74d8a6cb930c68ef617b202c3ff3c59d919e086b | win64, winarm64 | 50-libplacebo/src1/3rdparty/Vulkan-Headers |
| 50-libplacebo (submodule 3rdparty/fast_float) | see .gitmodules | 97b54ca9e75f5303507699d27c6b4f4efe4641a1 | win64, winarm64 | 50-libplacebo/src1/3rdparty/fast_float |
| 50-libplacebo (submodule 3rdparty/glad) | see .gitmodules | 73db193f853e2ee079bf3ca8a64aa2eaf6459043 | win64, winarm64 | 50-libplacebo/src1/3rdparty/glad |
| 50-libplacebo (submodule 3rdparty/jinja) | see .gitmodules | 15206881c006c79667fe5154fe80c01c65410679 | win64, winarm64 | 50-libplacebo/src1/3rdparty/jinja |
| 50-libplacebo (submodule 3rdparty/markupsafe) | see .gitmodules | 297fc8e356e6836a62087949245d09a28e9f1b13 | win64, winarm64 | 50-libplacebo/src1/3rdparty/markupsafe |
| 50-libplacebo (submodule demos/3rdparty/nuklear) | see .gitmodules | 242f35efa067a46c595645eeda7b1771ea1f83b1 | win64, winarm64 | 50-libplacebo/src1/demos/3rdparty/nuklear |
| 50-librist/40-mbedtls | https://github.com/ARMmbed/mbedtls.git | ece41aa84d7879d7e55c59e955a5884b541f7f3b | win64, winarm64 | 50-librist/40-mbedtls/src1 |
| 50-librist/40-mbedtls (submodule framework) | see .gitmodules | dde0c4a0e448a0552f18817dcea633bb851fd288 | win64, winarm64 | 50-librist/40-mbedtls/src1/framework |
| 50-librist/40-mbedtls (submodule tf-psa-crypto) | see .gitmodules | 73c5da561c8e5253db7b1fb440eda86fde8d8024 | win64, winarm64 | 50-librist/40-mbedtls/src1/tf-psa-crypto |
| 50-librist/40-mbedtls (submodule tf-psa-crypto/drivers/pqcp/mldsa-native) | see .gitmodules | 5772b4f4a0105694b1203abb582273f78fa951b7 | win64, winarm64 | 50-librist/40-mbedtls/src1/tf-psa-crypto/drivers/pqcp/mldsa-native |
| 50-librist/40-mbedtls (submodule tf-psa-crypto/framework) | see .gitmodules | dde0c4a0e448a0552f18817dcea633bb851fd288 | win64, winarm64 | 50-librist/40-mbedtls/src1/tf-psa-crypto/framework |
| 50-librist/50-librist | https://code.videolan.org/rist/librist.git | 4f45ef8f78983892d52ccd52d9f675435b23738f | win64, winarm64 | 50-librist/50-librist/src1 |
| 50-librsvg/10-glib | https://github.com/GNOME/glib.git | 5a124d1e66a6c2dc56989303b4d6d4781c2952ed | win64, winarm64 | 50-librsvg/10-glib/src1 |
| 50-librsvg/10-glib (submodule subprojects/gvdb) | see .gitmodules | 2b42fc75f09dbe1cd1057580b5782b08f2dcb400 | win64, winarm64 | 50-librsvg/10-glib/src1/subprojects/gvdb |
| 50-librsvg/20-cairo | https://gitlab.freedesktop.org/cairo/cairo.git | 74755964edef651691d5cd36ff140108298e4e6e | win64, winarm64 | 50-librsvg/20-cairo/src1 |
| 50-librsvg/30-pango | https://github.com/GNOME/pango.git | 8e74c27c113c98664b77272d16b14bbce542c184 | win64, winarm64 | 50-librsvg/30-pango/src1 |
| 50-librsvg/99-librsvg | https://github.com/GNOME/librsvg.git | 7612431eb02dc009319094f8513d63c1faaecfb4 | win64, winarm64 | 50-librsvg/99-librsvg/src1 |
| 50-libssh | https://gitlab.com/libssh/libssh-mirror.git | 76e0a8639e61436c28d877586f65a7707edc6ee5 | win64, winarm64 | 50-libssh/src1 |
| 50-libtheora | https://github.com/xiph/theora.git | 28fd5ec77f0ad0e07a371cef1047828116f6bd8a | win64, winarm64 | 50-libtheora/src1 |
| 50-libvpx | https://chromium.googlesource.com/webm/libvpx | 5e680f30801d03c21078f8c4b772464752516211 | win64 | 50-libvpx/src1 |
| 50-libwebp | https://chromium.googlesource.com/webm/libwebp | 5c168cd23b1872969c38e34b01b04dcf29849288 | win64, winarm64 | 50-libwebp/src1 |
| 50-libzmq | https://github.com/zeromq/libzmq.git | 46493370217ac135246617fa2f6ac819d8b61bfc | win64, winarm64 | 50-libzmq/src1 |
| 50-lilv/96-lv2 | https://github.com/lv2/lv2.git | 3c57dae600a5ad8d05acd53ee3490f7d91cb7be6 | win64, winarm64 | 50-lilv/96-lv2/src1 |
| 50-lilv/96-serd | https://github.com/drobilla/serd.git | b6053bb2a4533e6a8e3821c1061f140d5e666938 | win64, winarm64 | 50-lilv/96-serd/src1 |
| 50-lilv/96-zix | https://github.com/drobilla/zix.git | 17d632393f5addb6fa24dda2927b96515407cca7 | win64, winarm64 | 50-lilv/96-zix/src1 |
| 50-lilv/97-sord | https://github.com/drobilla/sord.git | 4b5232bb91e7f2f1b84df384494d073fabbcd312 | win64, winarm64 | 50-lilv/97-sord/src1 |
| 50-lilv/98-sratom | https://github.com/lv2/sratom.git | 9e8ee84eed502e6030ce8bb49694fd28542b08fc | win64, winarm64 | 50-lilv/98-sratom/src1 |
| 50-lilv/99-lilv | https://github.com/lv2/lilv.git | 4b8f30055fa5cb4134a2eb45fc1555bc04289314 | win64, winarm64 | 50-lilv/99-lilv/src1 |
| 50-onevpl | https://github.com/intel/libvpl.git | 674d015bcb294bc39fa276e99a652ea045423e82 | win64 | 50-onevpl/src1 |
| 50-openal | https://github.com/kcat/openal-soft.git | c89b8cf7bba4822f230c69f0a6696a52e5322dca | win64, winarm64 | 50-openal/src1 |
| 50-openapv | https://github.com/AcademySoftwareFoundation/openapv.git | a58ce739be0dfb083643d929aee8f0e0ba9bdf63 | win64, winarm64 | 50-openapv/src1 |
| 50-opencore-amr | https://git.code.sf.net/p/opencore-amr/code | 7dba8c32238418ce0b316a852b2224df586ca896 | win64, winarm64 | 50-opencore-amr/src1 |
| 50-openh264 | https://github.com/cisco/openh264.git | 8b2d28faade10d74d99ac80e199aef664c9c5a3b | win64, winarm64 | 50-openh264/src1 |
| 50-openjpeg | https://github.com/uclouvain/openjpeg.git | 8314119b067c0fc77834731168daaebd379fdb12 | win64, winarm64 | 50-openjpeg/src1 |
| 50-openmpt | https://github.com/OpenMPT/openmpt.git | f83cedb0cd5446e4dfaa83ac97e3087107e26767 | win64 | 50-openmpt/src1 |
| 50-rav1e | https://github.com/xiph/rav1e.git | 31435de9d76fddd38f6dcc31d4014574cebb2092 | win64, winarm64 | 50-rav1e/src1 |
| 50-rubberband | https://github.com/breakfastquay/rubberband.git | e4296ac80b1170018a110bc326fd0d45a0eb27d6 | win64, winarm64 | 50-rubberband/src1 |
| 50-sdl | https://github.com/libsdl-org/SDL.git | b90ac95029d801c5abc59472ba8e2200dff31e1e | win64, winarm64 | 50-sdl/src1 |
| 50-snappy | https://github.com/google/snappy.git | 9c28114a38866f6deeaa826db918293bc28ae410 | win64, winarm64 | 50-snappy/src1 |
| 50-soxr | https://git.code.sf.net/p/soxr/code | 945b592b70470e29f917f4de89b4281fbbd540c0 | win64, winarm64 | 50-soxr/src1 |
| 50-srt | https://github.com/Haivision/srt.git | ff8ab25c57aece5b7351defe36dacc94fc28527f | win64, winarm64 | 50-srt/src1 |
| 50-svtav1 | https://gitlab.com/AOMediaCodec/SVT-AV1.git | 5ed9ffbcb5086da23f30fe9bc5b00145358462da | win64, winarm64 | 50-svtav1/src1 |
| 50-twolame | https://github.com/njh/twolame.git | 6fced852d4d5cfad58cf9dbe3ea619b08e87d398 | win64, winarm64 | 50-twolame/src1 |
| 50-uavs3d | https://github.com/uavs3/uavs3d.git | 0e20d2c291853f196c68922a264bcd8471d75b68 | win64 | 50-uavs3d/src1 |
| 50-vaapi/50-libva | https://github.com/intel/libva.git | 6b07f7100512817f736967e899b8c26313c20623 | win64, winarm64 | 50-vaapi/50-libva/src1 |
| 50-vapoursynth | https://github.com/vapoursynth/vapoursynth.git | 732845793a1caf5838d4f7b94f6ce668a19c908e | win64, winarm64 | 50-vapoursynth/src1 |
| 50-vidstab | https://github.com/georgmartius/vid.stab.git | e2445c4081658318223762a696eb1c645c2d7168 | win64, winarm64 | 50-vidstab/src1 |
| 50-vvenc | https://github.com/fraunhoferhhi/vvenc.git | b1cfb2ad495af6ae4cc214b7a060e8b4166c4629 | win64, winarm64 | 50-vvenc/src1 |
| 50-x264 | https://code.videolan.org/videolan/x264.git | 0480cb05fa188d37ae87e8f4fd8f1aea3711f7ee | win64, winarm64 | 50-x264/src1 |
| 50-x265 | https://github.com/Multicorewareinc/x265.git | 020d7054dbecfd3be8e62efe33ff8a305d41856e | win64, winarm64 | 50-x265/src1 |
| 50-xavs2 | https://github.com/pkuvcl/xavs2.git | eae1e8b9d12468059bdd7dee893508e470fa83d8 | win64 | 50-xavs2/src1 |
| 50-xvid | https://svn.xvid.org/trunk/xvidcore | r2204 | win64, winarm64 | 50-xvid/src1 |
| 50-zimg | https://github.com/sekrit-twc/zimg.git | 67e0603271c080e22c8429856dd4a8a56587e61e | win64, winarm64 | 50-zimg/src1 |
| 50-zimg (submodule graphengine) | see .gitmodules | cb5b2ce13384ec2491f0c37256ea210034799f69 | win64, winarm64 | 50-zimg/src1/graphengine |
| 50-zimg (submodule graphengine/test/googletest) | see .gitmodules | e2239ee6043f73722e7aa812a459f54a28552929 | win64, winarm64 | 50-zimg/src1/graphengine/test/googletest |
| 50-zimg (submodule test/extra/googletest) | see .gitmodules | 6910c9d9165801d8827d628cb72eb7ea9dd538c5 | win64, winarm64 | 50-zimg/src1/test/extra/googletest |
| 50-zvbi | https://github.com/zapping-vbi/zvbi | d3a5ee9f2b047bf16cd1ee5ccf6ec05ee75409d0 | win64, winarm64 | 50-zvbi/src1 |

## Linux build

The Linux FFmpeg build (`metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-linux64-gpl-nodvd.tar.xz`, `metatana-ffmpeg-n8.1.2-34-g9b6c8969e0-linuxarm64-gpl-nodvd.tar.xz`) was built in `ghcr.io/btbn/ffmpeg-builds/linux64-gpl-8.1@sha256:1a82e5045a79cd997d54f6753c432068fec38f10255e7c4a6e938f268b4ae722` and `ghcr.io/btbn/ffmpeg-builds/linuxarm64-gpl-8.1@sha256:44154241edbd83dba37e6f152de72277d34382bfe0b76863c0801a6ed9a38771` (both created 2026-10-17). BtbN's master was then at commit `63ac3265b0789ea16c7b1f8351cd2ad195a28722`, whose `scripts.d` is identical to the one at `9acad4a9ef15`. The libraries in the table above are at the same commits in the Linux images (linux64 has every win64 library; linuxarm64 has the arm64-capable ones). The libraries only the Linux images contain are in `metatana-ffmpeg-nodvd-linux-library-sources-btbn-63ac3265b078.tar.xz`:

| Script | Repository | Commit | Targets |
|---|---|---|---|
| 10-xorg-macros | https://gitlab.freedesktop.org/xorg/util/macros.git | ea1e15a4909ac8b03b2c5a08ac3810b385985157 | linux64, linuxarm64 |
| 45-pulseaudio | https://gitlab.freedesktop.org/pulseaudio/pulseaudio.git | 77d25a1e613095bdf87a1d13b65e7c330565077a | linux64, linuxarm64 |
| 45-x11/10-xcbproto | https://gitlab.freedesktop.org/xorg/proto/xcbproto.git | cf7e2581b613802f2f8ec2a4b50a6a20aad4bf52 | linux64, linuxarm64 |
| 45-x11/10-xproto | https://gitlab.freedesktop.org/xorg/proto/xorgproto.git | fd86fbff46eb7ab8e193c12b8a529e90bae31835 | linux64, linuxarm64 |
| 45-x11/10-xtrans | https://gitlab.freedesktop.org/xorg/lib/libxtrans.git | 79f6b0bfe2170496e8c37626043d009f4cd3f1e1 | linux64, linuxarm64 |
| 45-x11/20-libxau | https://gitlab.freedesktop.org/xorg/lib/libxau.git | be1daeb909f1d678e7859ac1555e90b4e768d5c4 | linux64, linuxarm64 |
| 45-x11/30-libxcb | https://gitlab.freedesktop.org/xorg/lib/libxcb.git | d4e07bab5729c7d7cc3d2b95568cd9a661a53c4f | linux64, linuxarm64 |
| 45-x11/40-libx11 | https://gitlab.freedesktop.org/xorg/lib/libx11.git | 13f9b8de400335f4b86bb0672da02f8166c0e796 | linux64, linuxarm64 |
| 45-x11/50-libxext | https://gitlab.freedesktop.org/xorg/lib/libxext.git | 508f8adca2540ff8926ac8456cb1c553a8caae76 | linux64, linuxarm64 |
| 45-x11/50-libxfixes | https://gitlab.freedesktop.org/xorg/lib/libxfixes.git | 55bb2d1d57d43e0595ce45393f26eb433d75a7cc | linux64, linuxarm64 |
| 45-x11/50-libxi | https://gitlab.freedesktop.org/xorg/lib/libxi.git | 3a0adabd16d8bf19c772061ad67f25c51281edf3 | linux64, linuxarm64 |
| 45-x11/50-libxinerama | https://gitlab.freedesktop.org/xorg/lib/libxinerama.git | d7162b962710bc724b41cabab4e7cea303c4b541 | linux64, linuxarm64 |
| 45-x11/50-libxrender | https://gitlab.freedesktop.org/xorg/lib/libxrender.git | f32afe9f877ae032c6bc9c27b17b7978b1b4c856 | linux64, linuxarm64 |
| 45-x11/50-libxscrnsaver | https://gitlab.freedesktop.org/xorg/lib/libxscrnsaver.git | 3f753e7a4050db083474444ae91cc17a849eaa4d | linux64, linuxarm64 |
| 45-x11/50-libxxf86vm | https://gitlab.freedesktop.org/xorg/lib/libxxf86vm.git | c76fde6bffcc87e5dd98d8196bb01a299bdc3236 | linux64, linuxarm64 |
| 45-x11/60-libglvnd | https://gitlab.freedesktop.org/glvnd/libglvnd.git | c046a760d845416e98ac4128757b2b356c47fdaa | linux64, linuxarm64 |
| 45-x11/60-libxcursor | https://gitlab.freedesktop.org/xorg/lib/libxcursor.git | 15efad7ccd035f5d1ddc8d437e047569d1775fa7 | linux64, linuxarm64 |
| 45-x11/60-libxrandr | https://gitlab.freedesktop.org/xorg/lib/libxrandr.git | 8a4ba1974bcf07057cf891128d86ae1ab5303574 | linux64, linuxarm64 |
| 45-x11/60-libxv | https://gitlab.freedesktop.org/xorg/lib/libxv.git | f315ec50fcad9bdbaed46c3e78dc5e7fe209f933 | linux64, linuxarm64 |
| 50-vaapi/30-libpciaccess | https://gitlab.freedesktop.org/xorg/lib/libpciaccess.git | 38e6f15f839fba2c49982e7ad61cde681fd5d4d6 | linux64, linuxarm64 |
| 50-vaapi/40-libdrm | https://gitlab.freedesktop.org/mesa/drm.git | b97cbde15c5c3abfe44d78e8f57139e50f612fec | linux64, linuxarm64 |

The Windows-only libraries (mingw-w64, mingw-std-threads) are not in the Linux builds. The Linux programs link glibc dynamically.
