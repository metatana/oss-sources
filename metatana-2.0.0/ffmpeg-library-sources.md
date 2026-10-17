# Library sources for BtbN FFmpeg-Builds autobuild-2026-07-31-14-10 (gpl, FFmpeg 8.1)

Each folder matches a script in scripts.d of the BtbN build scripts at that tag. srcN is the Nth repository the script pins, checked out at the pinned commit (git metadata removed). Submodules and shaderc's DEPS checkouts are included the way the build scripts fetch them. 50-rav1e/cargo-vendor holds the Rust crates from rav1e's Cargo.lock (the build also runs 'cargo update cc'; cc is a build-time helper and is not linked into FFmpeg).

| Script | Repository | Commit or revision | Targets | Folder |
|---|---|---|---|---|
| 10-mingw-std-threads | https://github.com/meganz/mingw-std-threads.git | c931bac289dd431f1dd30fc4a5d1a7be36668073 | win64, winarm64 | 10-mingw-std-threads/src1 |
| 10-mingw | https://git.code.sf.net/p/mingw-w64/mingw-w64.git | a556c6943c442465dc9a051bc6d3a6d452df4a1d | win64, winarm64 | 10-mingw/src1 |
| 10-xorg-macros | https://gitlab.freedesktop.org/xorg/util/macros.git | a9d71e3fd8e6758b70be31c586921bbbcd2a8449 | linux64, linuxarm64 | 10-xorg-macros/src1 |
| 20-libiconv | https://git.savannah.gnu.org/git/libiconv.git | 9d19c66d0a1768cffcf497b2db70bf4018b578d7 | win64, winarm64, linux64, linuxarm64 | 20-libiconv/src1 |
| 20-libiconv | https://git.savannah.gnu.org/git/gnulib.git | 103c922f47f8b0fb0503024783bdaff5016eea82 | win64, winarm64, linux64, linuxarm64 | 20-libiconv/src2 |
| 20-zlib | https://github.com/madler/zlib.git | e3dc0a85b7032e98380dec011bc8f2c2ee0d8fca | win64, winarm64, linux64, linuxarm64 | 20-zlib/src1 |
| 25-fftw3 | https://github.com/FFTW/fftw3.git | 93ed4c786934aec9946f8dda4b4e3eb08f8be41c | win64, winarm64, linux64, linuxarm64 | 25-fftw3/src1 |
| 25-fribidi | https://github.com/fribidi/fribidi.git | 069a7e3d31e6aa74f2068a8e0804106ce7906639 | win64, winarm64, linux64, linuxarm64 | 25-fribidi/src1 |
| 25-gmp | https://github.com/BtbN/gmplib.git | 9994908f090c694f8a152d660dc6852e0c48557a | win64, winarm64, linux64, linuxarm64 | 25-gmp/src1 |
| 25-libogg | https://github.com/xiph/ogg.git | 06a5e0262cdc28aa4ae6797627a783b5010440f0 | win64, winarm64, linux64, linuxarm64 | 25-libogg/src1 |
| 25-libxml2 | https://github.com/GNOME/libxml2.git | c8eaf2236ff16667970f96f3f01e119c99d38ab2 | win64, winarm64, linux64, linuxarm64 | 25-libxml2/src1 |
| 25-openssl | https://github.com/openssl/openssl.git | aae016bfd52fcad2bc9657c2c782cfdf73b1ed5f | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1 |
| 25-openssl (submodule cloudflare-quiche) | see .gitmodules | 7ab6a55cfe471267d61e4d28ba43d41defcd87e0 | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/cloudflare-quiche |
| 25-openssl (submodule cloudflare-quiche/quiche/deps/boringssl) | see .gitmodules | f1c75347daa2ea81a941e953f2263e0a4d970c8d | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/cloudflare-quiche/quiche/deps/boringssl |
| 25-openssl (submodule fuzz/corpora) | see .gitmodules | ce771805c094d098c25a218bc8e9f7344eccbc5a | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/fuzz/corpora |
| 25-openssl (submodule gost-engine) | see .gitmodules | 74b1f4fddbc2d6de969815b1992ddc1ae7c643fe | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/gost-engine |
| 25-openssl (submodule gost-engine/libprov) | see .gitmodules | 0b445c73ae1e87577430c6884cdeeca1afa36dbd | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/gost-engine/libprov |
| 25-openssl (submodule krb5) | see .gitmodules | 784c38f50e70a739400cdd3f2620bac2e2788e6c | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/krb5 |
| 25-openssl (submodule oqs-provider) | see .gitmodules | 7bc597c04b534ddea9b6654481deb31ded8e1bbc | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/oqs-provider |
| 25-openssl (submodule pkcs11-provider) | see .gitmodules | 663dea335c80bec7fd96d544ff875af08d6461a9 | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/pkcs11-provider |
| 25-openssl (submodule pkcs11-provider/python-ecdsa) | see .gitmodules | ea9666903c109a8e88a37eb1c60d4e98f01f0299 | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/pkcs11-provider/python-ecdsa |
| 25-openssl (submodule pkcs11-provider/tlsfuzzer) | see .gitmodules | 32fcb0d8e78fd9ffc4568d11ba5916936a46af8c | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/pkcs11-provider/tlsfuzzer |
| 25-openssl (submodule pkcs11-provider/tlslite-ng) | see .gitmodules | 4e16574d7c52f17c81c3f5e0aa547776a67fdf8e | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/pkcs11-provider/tlslite-ng |
| 25-openssl (submodule pyca-cryptography) | see .gitmodules | 0e855f952693c8b730abb2fc5a84dfc69562f210 | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/pyca-cryptography |
| 25-openssl (submodule python-ecdsa) | see .gitmodules | 4096fa01715929e08b97e73f3173aee9d57f2a3f | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/python-ecdsa |
| 25-openssl (submodule tlsfuzzer) | see .gitmodules | 61f45d9701294fd87ef92d2a7e3dfb076653a562 | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/tlsfuzzer |
| 25-openssl (submodule tlslite-ng) | see .gitmodules | 77ef321dde1a9e6bcf94d73c80f8789a770d8031 | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/tlslite-ng |
| 25-openssl (submodule wycheproof) | see .gitmodules | aca47066256c167f0ce04d611d718cc85654341e | win64, winarm64, linux64, linuxarm64 | 25-openssl/src1/wycheproof |
| 25-xz | https://github.com/tukaani-project/xz.git | f3b5688159c60495f48db3942a36509671dfce89 | win64, winarm64, linux64, linuxarm64 | 25-xz/src1 |
| 45-fonts/25-freetype | https://gitlab.freedesktop.org/freetype/freetype.git | 5336c0d4da22a13dab3389eb153b12672fdf841c | win64, winarm64, linux64, linuxarm64 | 45-fonts/25-freetype/src1 |
| 45-fonts/35-fontconfig | https://gitlab.freedesktop.org/fontconfig/fontconfig.git | 939e33ee473d70a790c89b624385c2c0a5875a51 | win64, winarm64, linux64, linuxarm64 | 45-fonts/35-fontconfig/src1 |
| 45-fonts/45-harfbuzz | https://github.com/harfbuzz/harfbuzz.git | fe9501b08d1bf40bf5c6285d336157aa82b29e40 | win64, winarm64, linux64, linuxarm64 | 45-fonts/45-harfbuzz/src1 |
| 45-fonts/50-freetype | https://gitlab.freedesktop.org/freetype/freetype.git | 5336c0d4da22a13dab3389eb153b12672fdf841c | win64, winarm64, linux64, linuxarm64 | 45-fonts/50-freetype/src1 |
| 45-libsamplerate | https://github.com/libsndfile/libsamplerate.git | 2ccde9568cca73c7b32c97fefca2e418c16ae5e3 | win64, winarm64, linux64, linuxarm64 | 45-libsamplerate/src1 |
| 45-libudfread | https://code.videolan.org/videolan/libudfread.git | 139a2194525f2745b98a98e4d8fa627d07440176 | win64, winarm64, linux64, linuxarm64 | 45-libudfread/src1 |
| 45-libunibreak | https://github.com/adah1972/libunibreak.git | 3ce4bfa3129ff3738046a44a6db533d2ce25af2b | win64, winarm64, linux64, linuxarm64 | 45-libunibreak/src1 |
| 45-libvorbis | https://github.com/xiph/vorbis.git | e3c9861ff096d52378e131ff8c334552e09cdffa | win64, winarm64, linux64, linuxarm64 | 45-libvorbis/src1 |
| 45-opencl | https://github.com/KhronosGroup/OpenCL-Headers.git | a98488062f50c77c3e2edaf9c4f8dca7c41781ec | win64, winarm64, linux64, linuxarm64 | 45-opencl/src1 |
| 45-opencl | https://github.com/KhronosGroup/OpenCL-ICD-Loader.git | 18fdcd58286376124f938948aa8ed156079c1c16 | win64, winarm64, linux64, linuxarm64 | 45-opencl/src2 |
| 45-pulseaudio | https://gitlab.freedesktop.org/pulseaudio/pulseaudio.git | b096704c0d42c5e784deb781a07b23cfb5286a82 | linux64, linuxarm64 | 45-pulseaudio/src1 |
| 45-vmaf | https://github.com/Netflix/vmaf.git | e9909adb89306a270d9c78207bd12acf730279ad | win64, winarm64, linux64, linuxarm64 | 45-vmaf/src1 |
| 45-x11/10-xcbproto | https://gitlab.freedesktop.org/xorg/proto/xcbproto.git | cf7e2581b613802f2f8ec2a4b50a6a20aad4bf52 | linux64, linuxarm64 | 45-x11/10-xcbproto/src1 |
| 45-x11/10-xproto | https://gitlab.freedesktop.org/xorg/proto/xorgproto.git | fcb7e9a1a0b593a44740d83b0babddd331fea830 | linux64, linuxarm64 | 45-x11/10-xproto/src1 |
| 45-x11/10-xtrans | https://gitlab.freedesktop.org/xorg/lib/libxtrans.git | 693d28a76024a2a0a28eef25037bcb7558b8bbfa | linux64, linuxarm64 | 45-x11/10-xtrans/src1 |
| 45-x11/20-libxau | https://gitlab.freedesktop.org/xorg/lib/libxau.git | 14ba0f63c4ba2229dd17574134332767bded9018 | linux64, linuxarm64 | 45-x11/20-libxau/src1 |
| 45-x11/30-libxcb | https://gitlab.freedesktop.org/xorg/lib/libxcb.git | 4d6e1c8fffaf811cf4d0e68ff3bc6f50e62c32c7 | linux64, linuxarm64 | 45-x11/30-libxcb/src1 |
| 45-x11/40-libx11 | https://gitlab.freedesktop.org/xorg/lib/libx11.git | b10abf6b99d5acf846c26f305f1a14a86360a96c | linux64, linuxarm64 | 45-x11/40-libx11/src1 |
| 45-x11/50-libxext | https://gitlab.freedesktop.org/xorg/lib/libxext.git | 2a694ba264ccdb205909909abfe8b136f9156ebe | linux64, linuxarm64 | 45-x11/50-libxext/src1 |
| 45-x11/50-libxfixes | https://gitlab.freedesktop.org/xorg/lib/libxfixes.git | 55bb2d1d57d43e0595ce45393f26eb433d75a7cc | linux64, linuxarm64 | 45-x11/50-libxfixes/src1 |
| 45-x11/50-libxi | https://gitlab.freedesktop.org/xorg/lib/libxi.git | f00f7e9140b4707775331950dd67851e55058c40 | linux64, linuxarm64 | 45-x11/50-libxi/src1 |
| 45-x11/50-libxinerama | https://gitlab.freedesktop.org/xorg/lib/libxinerama.git | d7162b962710bc724b41cabab4e7cea303c4b541 | linux64, linuxarm64 | 45-x11/50-libxinerama/src1 |
| 45-x11/50-libxrender | https://gitlab.freedesktop.org/xorg/lib/libxrender.git | f32afe9f877ae032c6bc9c27b17b7978b1b4c856 | linux64, linuxarm64 | 45-x11/50-libxrender/src1 |
| 45-x11/50-libxscrnsaver | https://gitlab.freedesktop.org/xorg/lib/libxscrnsaver.git | 3f753e7a4050db083474444ae91cc17a849eaa4d | linux64, linuxarm64 | 45-x11/50-libxscrnsaver/src1 |
| 45-x11/50-libxxf86vm | https://gitlab.freedesktop.org/xorg/lib/libxxf86vm.git | c76fde6bffcc87e5dd98d8196bb01a299bdc3236 | linux64, linuxarm64 | 45-x11/50-libxxf86vm/src1 |
| 45-x11/60-libglvnd | https://gitlab.freedesktop.org/glvnd/libglvnd.git | c046a760d845416e98ac4128757b2b356c47fdaa | linux64, linuxarm64 | 45-x11/60-libglvnd/src1 |
| 45-x11/60-libxcursor | https://gitlab.freedesktop.org/xorg/lib/libxcursor.git | 15efad7ccd035f5d1ddc8d437e047569d1775fa7 | linux64, linuxarm64 | 45-x11/60-libxcursor/src1 |
| 45-x11/60-libxrandr | https://gitlab.freedesktop.org/xorg/lib/libxrandr.git | 8a4ba1974bcf07057cf891128d86ae1ab5303574 | linux64, linuxarm64 | 45-x11/60-libxrandr/src1 |
| 45-x11/60-libxv | https://gitlab.freedesktop.org/xorg/lib/libxv.git | f315ec50fcad9bdbaed46c3e78dc5e7fe209f933 | linux64, linuxarm64 | 45-x11/60-libxv/src1 |
| 47-vulkan/40-vulkan-headers | https://github.com/KhronosGroup/Vulkan-Headers.git | 8d6039a455a7ecc7d2a592ff97f62db4e59b70bf | win64, winarm64, linux64, linuxarm64 | 47-vulkan/40-vulkan-headers/src1 |
| 47-vulkan/45-vulkan-loader | https://github.com/BtbN/Vulkan-Shim-Loader.git | 65b3936528cd92eb4ea3de485d03f858a3850484 | win64, winarm64, linux64, linuxarm64 | 47-vulkan/45-vulkan-loader/src1 |
| 47-vulkan/45-vulkan-loader | https://github.com/KhronosGroup/Vulkan-Headers.git | 8d6039a455a7ecc7d2a592ff97f62db4e59b70bf | win64, winarm64, linux64, linuxarm64 | 47-vulkan/45-vulkan-loader/src2 |
| 47-vulkan/50-shaderc | https://github.com/google/shaderc.git | 49a8724d561c13db22b52f99f2a0e2707a9a9e3c | win64, winarm64, linux64, linuxarm64 | 47-vulkan/50-shaderc/src1 |
| 47-vulkan/50-shaderc (third_party/abseil_cpp) | https://github.com/abseil/abseil-cpp.git | dbf88f932096c7f7714356e919f04749eb87c3e9 | win64, winarm64, linux64, linuxarm64 | 47-vulkan/50-shaderc/src1/third_party/abseil_cpp |
| 47-vulkan/50-shaderc (third_party/effcee) | https://github.com/google/effcee.git | 910ed15722d5d05c9d71ecf36c1a22243cb79b02 | win64, winarm64, linux64, linuxarm64 | 47-vulkan/50-shaderc/src1/third_party/effcee |
| 47-vulkan/50-shaderc (third_party/googletest) | https://github.com/google/googletest.git | 52eb8108c5bdec04579160ae17225d66034bd723 | win64, winarm64, linux64, linuxarm64 | 47-vulkan/50-shaderc/src1/third_party/googletest |
| 47-vulkan/50-shaderc (third_party/glslang) | https://github.com/KhronosGroup/glslang.git | ce138e2c2d6992b31ff4cd2e955904637785a881 | win64, winarm64, linux64, linuxarm64 | 47-vulkan/50-shaderc/src1/third_party/glslang |
| 47-vulkan/50-shaderc (third_party/re2) | https://github.com/google/re2.git | 927f5d53caf8111721e734cf24724686bb745f55 | win64, winarm64, linux64, linuxarm64 | 47-vulkan/50-shaderc/src1/third_party/re2 |
| 47-vulkan/50-shaderc (third_party/spirv-headers) | https://github.com/KhronosGroup/SPIRV-Headers.git | daa093dd29aab8cbb6562b808370562f56e399fb | win64, winarm64, linux64, linuxarm64 | 47-vulkan/50-shaderc/src1/third_party/spirv-headers |
| 47-vulkan/50-shaderc (third_party/spirv-tools) | https://github.com/KhronosGroup/SPIRV-Tools.git | d5bbf95d87dd6d2694fbf09acfb42a00c93575e8 | win64, winarm64, linux64, linuxarm64 | 47-vulkan/50-shaderc/src1/third_party/spirv-tools |
| 47-vulkan/55-spirv-cross | https://github.com/KhronosGroup/SPIRV-Cross.git | 81fc2ea76c2b8018d4427c380961a6886cb3ce7d | win64, winarm64, linux64, linuxarm64 | 47-vulkan/55-spirv-cross/src1 |
| 47-vulkan/60-spirv-headers | https://github.com/KhronosGroup/SPIRV-Headers.git | 02c0394e57af6dfdda7f68973df6aa20fc3f5def | win64, winarm64, linux64, linuxarm64 | 47-vulkan/60-spirv-headers/src1 |
| 50-amf | https://github.com/GPUOpen-LibrariesAndSDKs/AMF.git | 6ec029531e356102aafe1e236cfd0ddf739939da | win64, winarm64, linux64, linuxarm64 | 50-amf/src1 |
| 50-aom | https://aomedia.googlesource.com/aom | 43f2b6a99000057184332c8c2dd4bedc19fdec6f | win64, linux64, linuxarm64 | 50-aom/src1 |
| 50-aribb24/25-libpng | https://github.com/glennrp/libpng.git | d1d0abeffede1cc898ddc3d0e600839cf026d749 | win64, winarm64, linux64, linuxarm64 | 50-aribb24/25-libpng/src1 |
| 50-aribb24/50-libaribb24 | https://github.com/nkoriyama/aribb24.git | 5e9be272f96e00f15a2f3c5f8ba7e124862aec38 | win64, winarm64, linux64, linuxarm64 | 50-aribb24/50-libaribb24/src1 |
| 50-avisynth | https://github.com/AviSynth/AviSynthPlus.git | fcb9c8a205c1b01ee1ea491adba50e2217594598 | win64, winarm64, linux64, linuxarm64 | 50-avisynth/src1 |
| 50-chromaprint | https://github.com/acoustid/chromaprint.git | ab48115481c14873eb870e7a88334550c68d36c1 | win64, winarm64, linux64, linuxarm64 | 50-chromaprint/src1 |
| 50-dav1d | https://code.videolan.org/videolan/dav1d.git | c150ba6c9b9be0956330a9ddfee33ad88f2b1bc5 | win64, winarm64, linux64, linuxarm64 | 50-dav1d/src1 |
| 50-davs2 | https://github.com/pkuvcl/davs2.git | b41cf117452e2d73d827f02d3e30aa20f1c721ac | win64, linux64 | 50-davs2/src1 |
| 50-dvd/30-libdvdcss | https://code.videolan.org/videolan/libdvdcss.git | 891f8fb5c45baf70bfbd67d973d1d4f0b10fd0aa | win64, winarm64, linux64, linuxarm64 | 50-dvd/30-libdvdcss/src1 |
| 50-dvd/40-libdvdread | https://code.videolan.org/videolan/libdvdread.git | 8c1c65fbbb2944cd0201c404cd72859a18a3bbf8 | win64, winarm64, linux64, linuxarm64 | 50-dvd/40-libdvdread/src1 |
| 50-dvd/50-libdvdnav | https://code.videolan.org/videolan/libdvdnav.git | 9c5f2278eb5b23cdcd0575065f5d575c4e6602a4 | win64, winarm64, linux64, linuxarm64 | 50-dvd/50-libdvdnav/src1 |
| 50-ffnvcodec | https://github.com/FFmpeg/nv-codec-headers.git | 15ee32753c92faddbabbff11676779618fc6db7e | win64, linux64, linuxarm64 | 50-ffnvcodec/src1 |
| 50-ffnvcodec | https://github.com/FFmpeg/nv-codec-headers.git | 33a9ede8d9914299d9262539c576a15bd0a19621 | win64, linux64, linuxarm64 | 50-ffnvcodec/src2 |
| 50-ffnvcodec | https://github.com/FFmpeg/nv-codec-headers.git | afae1834257b919848c5deb21a17c7355616b1ee | win64, linux64, linuxarm64 | 50-ffnvcodec/src3 |
| 50-frei0r | https://github.com/dyne/frei0r.git | 253addfd4bea3c90b0bf765589ca28ea18f3ddc0 | win64, winarm64, linux64, linuxarm64 | 50-frei0r/src1 |
| 50-gme | https://github.com/libgme/game-music-emu.git | dd3182a8bdae3ff761438632aace418fbcaed439 | win64, winarm64, linux64, linuxarm64 | 50-gme/src1 |
| 50-kvazaar | https://github.com/ultravideo/kvazaar.git | d6815293f34a094e26ba6c50b8644660ddc13e09 | win64, winarm64, linux64, linuxarm64 | 50-kvazaar/src1 |
| 50-lcevcdec | https://github.com/v-novaltd/LCEVCdec.git | a254bd474649e5dcd8182689ac414420bfe8d8c3 | win64, linux64, linuxarm64 | 50-lcevcdec/src1 |
| 50-libaribcaption | https://github.com/xqq/libaribcaption.git | f9d8c50fe5e51c98d101f69d74591295cb568036 | win64, winarm64, linux64, linuxarm64 | 50-libaribcaption/src1 |
| 50-libass | https://github.com/libass/libass.git | 4a05d8127f525943ebf45fdc6497c9e665947f0d | win64, winarm64, linux64, linuxarm64 | 50-libass/src1 |
| 50-libbluray | https://code.videolan.org/videolan/libbluray.git | 8b4fb6e2562bb86601ea5a2c4140af6d8f3f1cf4 | win64, winarm64, linux64, linuxarm64 | 50-libbluray/src1 |
| 50-libjxl/45-brotli | https://github.com/google/brotli.git | 27cc9fe9a4aa8901be3b3ba29f2f09eaddb08f97 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/45-brotli/src1 |
| 50-libjxl/45-lcms2 | https://github.com/mm2/Little-CMS.git | 5cc0eec7ae8350dd0f6c4c07b077f78f18dfe970 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/45-lcms2/src1 |
| 50-libjxl/50-libjxl | https://github.com/libjxl/libjxl.git | f0a1c5ff9dbba51ffa932433ffb80e5e6b6e22a7 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1 |
| 50-libjxl/50-libjxl (submodule testdata) | see .gitmodules | 73695d303670c90e4d506ea89d9901b081385089 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/testdata |
| 50-libjxl/50-libjxl (submodule third_party/brotli) | see .gitmodules | 028fb5a23661f123017c060daa546b55cf4bde29 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/brotli |
| 50-libjxl/50-libjxl (submodule third_party/googletest) | see .gitmodules | 6910c9d9165801d8827d628cb72eb7ea9dd538c5 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/googletest |
| 50-libjxl/50-libjxl (submodule third_party/highway) | see .gitmodules | 457c891775a7397bdb0376bb1031e6e027af1c48 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/highway |
| 50-libjxl/50-libjxl (submodule third_party/lcms) | see .gitmodules | 5176347635785e53ee5cee92328f76fda766ecc6 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/lcms |
| 50-libjxl/50-libjxl (submodule third_party/libjpeg-turbo) | see .gitmodules | 8ecba3647edb6dd940463fedf38ca33a8e2a73d1 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/libjpeg-turbo |
| 50-libjxl/50-libjxl (submodule third_party/libpng) | see .gitmodules | 872555f4ba910252783af1507f9e7fe1653be252 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/libpng |
| 50-libjxl/50-libjxl (submodule third_party/sjpeg) | see .gitmodules | 94e0df6d0f8b44228de5be0ff35efb9f946a13c9 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/sjpeg |
| 50-libjxl/50-libjxl (submodule third_party/skcms) | see .gitmodules | 96d9171c94b937a1b5f0293de7309ac16311b722 | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/skcms |
| 50-libjxl/50-libjxl (submodule third_party/zlib) | see .gitmodules | 51b7f2abdade71cd9bb0e7a373ef2610ec6f9daf | win64, winarm64, linux64, linuxarm64 | 50-libjxl/50-libjxl/src1/third_party/zlib |
| 50-libmp3lame | https://svn.code.sf.net/p/lame/svn/trunk/lame | r6531 | win64, winarm64, linux64, linuxarm64 | 50-libmp3lame/src1 |
| 50-libopus | https://github.com/xiph/opus.git | 3da9f7a6db1c05c3996cb363a9d1931a978bf1be | win64, winarm64, linux64, linuxarm64 | 50-libopus/src1 |
| 50-libplacebo | https://code.videolan.org/videolan/libplacebo.git | 05ac2cca6571c04d06369a26825d207781b73f32 | win64, winarm64, linux64, linuxarm64 | 50-libplacebo/src1 |
| 50-libplacebo (submodule 3rdparty/Vulkan-Headers) | see .gitmodules | 74d8a6cb930c68ef617b202c3ff3c59d919e086b | win64, winarm64, linux64, linuxarm64 | 50-libplacebo/src1/3rdparty/Vulkan-Headers |
| 50-libplacebo (submodule 3rdparty/fast_float) | see .gitmodules | 97b54ca9e75f5303507699d27c6b4f4efe4641a1 | win64, winarm64, linux64, linuxarm64 | 50-libplacebo/src1/3rdparty/fast_float |
| 50-libplacebo (submodule 3rdparty/glad) | see .gitmodules | 73db193f853e2ee079bf3ca8a64aa2eaf6459043 | win64, winarm64, linux64, linuxarm64 | 50-libplacebo/src1/3rdparty/glad |
| 50-libplacebo (submodule 3rdparty/jinja) | see .gitmodules | 15206881c006c79667fe5154fe80c01c65410679 | win64, winarm64, linux64, linuxarm64 | 50-libplacebo/src1/3rdparty/jinja |
| 50-libplacebo (submodule 3rdparty/markupsafe) | see .gitmodules | 297fc8e356e6836a62087949245d09a28e9f1b13 | win64, winarm64, linux64, linuxarm64 | 50-libplacebo/src1/3rdparty/markupsafe |
| 50-libplacebo (submodule demos/3rdparty/nuklear) | see .gitmodules | 242f35efa067a46c595645eeda7b1771ea1f83b1 | win64, winarm64, linux64, linuxarm64 | 50-libplacebo/src1/demos/3rdparty/nuklear |
| 50-librist/40-mbedtls | https://github.com/ARMmbed/mbedtls.git | 0fe989b6b514192783c469039edd325fd0989806 | win64, winarm64, linux64, linuxarm64 | 50-librist/40-mbedtls/src1 |
| 50-librist/40-mbedtls (submodule framework) | see .gitmodules | dff9da04438d712f7647fd995bc90fadd0c0e2ce | win64, winarm64, linux64, linuxarm64 | 50-librist/40-mbedtls/src1/framework |
| 50-librist/40-mbedtls (submodule tf-psa-crypto) | see .gitmodules | 29160dd877d29658279fd683b2ae57b320ddcf09 | win64, winarm64, linux64, linuxarm64 | 50-librist/40-mbedtls/src1/tf-psa-crypto |
| 50-librist/40-mbedtls (submodule tf-psa-crypto/drivers/pqcp/mldsa-native) | see .gitmodules | 5772b4f4a0105694b1203abb582273f78fa951b7 | win64, winarm64, linux64, linuxarm64 | 50-librist/40-mbedtls/src1/tf-psa-crypto/drivers/pqcp/mldsa-native |
| 50-librist/40-mbedtls (submodule tf-psa-crypto/framework) | see .gitmodules | dff9da04438d712f7647fd995bc90fadd0c0e2ce | win64, winarm64, linux64, linuxarm64 | 50-librist/40-mbedtls/src1/tf-psa-crypto/framework |
| 50-librist/50-librist | https://code.videolan.org/rist/librist.git | 6e2a5e341bbdbe4ca283f3f79e42db8be0f2e027 | win64, winarm64, linux64, linuxarm64 | 50-librist/50-librist/src1 |
| 50-libssh | https://gitlab.com/libssh/libssh-mirror.git | 689d7320644bbf06f77911a58d41a68e3e68675b | win64, winarm64, linux64, linuxarm64 | 50-libssh/src1 |
| 50-libtheora | https://github.com/xiph/theora.git | 28fd5ec77f0ad0e07a371cef1047828116f6bd8a | win64, winarm64, linux64, linuxarm64 | 50-libtheora/src1 |
| 50-libvpx | https://chromium.googlesource.com/webm/libvpx | 8592391cdb3ef142c56d835788d71d6d4de36a63 | win64, linux64, linuxarm64 | 50-libvpx/src1 |
| 50-libwebp | https://chromium.googlesource.com/webm/libwebp | 733c91e461c18cf1127c9ed0a80dccbcfed599d3 | win64, winarm64, linux64, linuxarm64 | 50-libwebp/src1 |
| 50-libzmq | https://github.com/zeromq/libzmq.git | 2e8a6ccb414ca79636392604893c79c3b0d00dc4 | win64, winarm64, linux64, linuxarm64 | 50-libzmq/src1 |
| 50-lilv/96-lv2 | https://github.com/lv2/lv2.git | 3c57dae600a5ad8d05acd53ee3490f7d91cb7be6 | win64, winarm64, linux64, linuxarm64 | 50-lilv/96-lv2/src1 |
| 50-lilv/96-serd | https://github.com/drobilla/serd.git | b6053bb2a4533e6a8e3821c1061f140d5e666938 | win64, winarm64, linux64, linuxarm64 | 50-lilv/96-serd/src1 |
| 50-lilv/96-zix | https://github.com/drobilla/zix.git | 17d632393f5addb6fa24dda2927b96515407cca7 | win64, winarm64, linux64, linuxarm64 | 50-lilv/96-zix/src1 |
| 50-lilv/97-sord | https://github.com/drobilla/sord.git | 4b5232bb91e7f2f1b84df384494d073fabbcd312 | win64, winarm64, linux64, linuxarm64 | 50-lilv/97-sord/src1 |
| 50-lilv/98-sratom | https://github.com/lv2/sratom.git | 9e8ee84eed502e6030ce8bb49694fd28542b08fc | win64, winarm64, linux64, linuxarm64 | 50-lilv/98-sratom/src1 |
| 50-lilv/99-lilv | https://github.com/lv2/lilv.git | 4b8f30055fa5cb4134a2eb45fc1555bc04289314 | win64, winarm64, linux64, linuxarm64 | 50-lilv/99-lilv/src1 |
| 50-onevpl | https://github.com/intel/libvpl.git | d77f9195cf495b937631607333288fd917ae8939 | win64, linux64 | 50-onevpl/src1 |
| 50-openal | https://github.com/kcat/openal-soft.git | 93358135d92f3aa2672ed95f9c6bb04f8482d578 | win64, winarm64, linux64, linuxarm64 | 50-openal/src1 |
| 50-openapv | https://github.com/AcademySoftwareFoundation/openapv.git | 9f6fd2a7369db90acec67d99fc57724f1136fb84 | win64, winarm64, linux64, linuxarm64 | 50-openapv/src1 |
| 50-opencore-amr | https://git.code.sf.net/p/opencore-amr/code | 7dba8c32238418ce0b316a852b2224df586ca896 | win64, winarm64, linux64, linuxarm64 | 50-opencore-amr/src1 |
| 50-openh264 | https://github.com/cisco/openh264.git | a8e04adb69c79757da014007d4694684a64c7b74 | win64, winarm64, linux64, linuxarm64 | 50-openh264/src1 |
| 50-openjpeg | https://github.com/uclouvain/openjpeg.git | 9dd4b3c98a78f50a48fb08f27bf198d4ae1d8528 | win64, winarm64, linux64, linuxarm64 | 50-openjpeg/src1 |
| 50-openmpt | https://github.com/OpenMPT/openmpt.git | 4c3ba47c7977fe3016b474f8ed192e619ae85f7d | win64, linux64, linuxarm64 | 50-openmpt/src1 |
| 50-rav1e | https://github.com/xiph/rav1e.git | 564ae3b0007ae2b06893fd7166bf88c5a84c5b63 | win64, winarm64, linux64, linuxarm64 | 50-rav1e/src1 |
| 50-rubberband | https://github.com/breakfastquay/rubberband.git | e4296ac80b1170018a110bc326fd0d45a0eb27d6 | win64, winarm64, linux64, linuxarm64 | 50-rubberband/src1 |
| 50-sdl | https://github.com/libsdl-org/SDL.git | b8b3f5ef2001cbe7c11f62d41a9bf47d4a2d8b07 | win64, winarm64, linux64, linuxarm64 | 50-sdl/src1 |
| 50-snappy | https://github.com/google/snappy.git | 3ac3722e1bee4b99860a282fb779e8e72fa18163 | win64, winarm64, linux64, linuxarm64 | 50-snappy/src1 |
| 50-soxr | https://git.code.sf.net/p/soxr/code | 945b592b70470e29f917f4de89b4281fbbd540c0 | win64, winarm64, linux64, linuxarm64 | 50-soxr/src1 |
| 50-srt | https://github.com/Haivision/srt.git | c39196c9a568ae4e3289dd65cf54ba4154deb4a1 | win64, winarm64, linux64, linuxarm64 | 50-srt/src1 |
| 50-svtav1 | https://gitlab.com/AOMediaCodec/SVT-AV1.git | d3c4cb3947a8bfed0aa5a2be996b37bb117fa1bd | win64, winarm64, linux64, linuxarm64 | 50-svtav1/src1 |
| 50-twolame | https://github.com/njh/twolame.git | 6fced852d4d5cfad58cf9dbe3ea619b08e87d398 | win64, winarm64, linux64, linuxarm64 | 50-twolame/src1 |
| 50-uavs3d | https://github.com/uavs3/uavs3d.git | 0e20d2c291853f196c68922a264bcd8471d75b68 | win64, linux64, linuxarm64 | 50-uavs3d/src1 |
| 50-vaapi/30-libpciaccess | https://gitlab.freedesktop.org/xorg/lib/libpciaccess.git | 38e6f15f839fba2c49982e7ad61cde681fd5d4d6 | linux64, linuxarm64 | 50-vaapi/30-libpciaccess/src1 |
| 50-vaapi/40-libdrm | https://gitlab.freedesktop.org/mesa/drm.git | 35c7c536d5d1c0124a416a531df4432508d7d2f1 | linux64, linuxarm64 | 50-vaapi/40-libdrm/src1 |
| 50-vaapi/50-libva | https://github.com/intel/libva.git | 28388a091187e2ba9e99cb750ec7426f91f73cbb | win64, winarm64, linux64 | 50-vaapi/50-libva/src1 |
| 50-vidstab | https://github.com/georgmartius/vid.stab.git | 92bc0b0f369f2a88aaacf25eac3a10f8415308fc | win64, winarm64, linux64, linuxarm64 | 50-vidstab/src1 |
| 50-vvenc | https://github.com/fraunhoferhhi/vvenc.git | 7d60406c66fa1659b8df74dd8d62bc41d3c90157 | win64, winarm64, linux64, linuxarm64 | 50-vvenc/src1 |
| 50-x264 | https://code.videolan.org/videolan/x264.git | 0480cb05fa188d37ae87e8f4fd8f1aea3711f7ee | win64, winarm64, linux64, linuxarm64 | 50-x264/src1 |
| 50-x265 | https://bitbucket.org/multicoreware/x265_git.git | b81f650e21e8aacbe6a9ad04ce14aefc05b932c0 | win64, winarm64, linux64, linuxarm64 | 50-x265/src1 |
| 50-xavs2 | https://github.com/pkuvcl/xavs2.git | eae1e8b9d12468059bdd7dee893508e470fa83d8 | win64, linux64 | 50-xavs2/src1 |
| 50-xvid | https://svn.xvid.org/trunk/xvidcore | r2204 | win64, winarm64, linux64, linuxarm64 | 50-xvid/src1 |
| 50-zimg | https://github.com/sekrit-twc/zimg.git | b3647572a01927e2aa8d0b7aaa917207c9c1ae5d | win64, winarm64, linux64, linuxarm64 | 50-zimg/src1 |
| 50-zimg (submodule graphengine) | see .gitmodules | f06d7cb4d589ea4657f01b13613efb7437c8ecda | win64, winarm64, linux64, linuxarm64 | 50-zimg/src1/graphengine |
| 50-zimg (submodule graphengine/test/googletest) | see .gitmodules | e2239ee6043f73722e7aa812a459f54a28552929 | win64, winarm64, linux64, linuxarm64 | 50-zimg/src1/graphengine/test/googletest |
| 50-zimg (submodule test/extra/googletest) | see .gitmodules | 6910c9d9165801d8827d628cb72eb7ea9dd538c5 | win64, winarm64, linux64, linuxarm64 | 50-zimg/src1/test/extra/googletest |
| 50-zvbi | https://github.com/zapping-vbi/zvbi | 41477c97c8edf7a01f1594b2a95b94f0117eed21 | win64, winarm64, linux64, linuxarm64 | 50-zvbi/src1 |
