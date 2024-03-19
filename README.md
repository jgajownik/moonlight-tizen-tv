# Moonlight for Tizen TV

According to description from official Moonlight website:

> You can stream your collection of PC games from your GameStream-compatible PC to any supported device and play them remotely. Moonlight is perfect for gaming on the go without sacrificing the graphics and game selection available on PC.

This specific repository contains implementation of Moonlight clieant for Tizen TV devices using WebAssembly and Tizen TV-specific extensions.

## Used Tizen specific features
- [Tizen WASM Player](https://developer.samsung.com/smarttv/develop/extension-libraries/webassembly/tizen-wasm-player/overview.html) - video/audio playback
- [Tizen Sockets Extension](https://developer.samsung.com/smarttv/develop/extension-libraries/webassembly/api-reference/tizen-sockets-extension.html) - networking

## Checking out required submodules
Since some of the dependencies used are provided as git submodules,
after cloning this repository (if you did not provide the `--recurse-submodules`
option while cloning) you need to issue the below command:

```bash
git submodule update --init --recursive
```

## Building

### Required software
- [Samsung Emscripten fork](https://developer.samsung.com/smarttv/develop/extension-libraries/webassembly/getting-started/downloading-and-installing.html)
- cmake (at least 3.10 - tested using CMake 3.10 and CMake 3.18)
- ninja (at least 1.8.2- recommended for Windows)

### Build procedure

```bash
mkdir build
cd build/
cmake -DCMAKE_TOOLCHAIN_FILE=<YOUR EMSCRIPTEN INSTALLATION_DIR>/cmake/Modules/Platform/Emscripten.cmake -G Ninja ..
ninja

# CMake 3.10 (and above):
cmake -DCMAKE_INSTALL_PREFIX=. -P cmake_install.cmake

# CMake 3.15 (and above):
cmake --install . --prefix .
```

*Note:* On Linux and MacOS you can also use Makefile cmake generators.

After that you can pack widget as described in
[Sample cURL application built using CLI tools](https://developer.samsung.com/smarttv/develop/extension-libraries/webassembly/tizen-sockets-extension/sample-curl-application-built-using-cli-tools.html)
tutorial.

## Credits
* Original Moonlight for ChromeOS [https://github.com/moonlight-stream/moonlight-chrome]
* Original Tizen TV port [https://github.com/SamsungDForum/moonlight-chrome]
