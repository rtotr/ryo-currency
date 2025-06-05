# Ryo Build Notes 2025

The following notes are for setting up the development environment and may not be completely up to date.

The latest versions of build scripts are always in the [.github/workflows/](.github/workflows/) folder.

## Ryo Core - Ubuntu

After clean install of Ubuntu 24 and apt update/upgrade we have

```
$ cmake --version
cmake version 3.28.3
$ gcc --version
gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0
```

```bash
sudo apt install build-essential cmake pkg-config libssl-dev libzmq3-dev libunbound-dev libsodium-dev libminiupnpc-dev libunwind8-dev liblzma-dev libreadline6-dev libldns-dev libexpat1-dev doxygen graphviz libpcsclite-dev libfmt-dev libeasyloggingpp-dev libcurl4-openssl-dev libboost-all-dev

git clone --branch dev-github-actions https://github.com/rtotr/ryo-currency.git
cd ryo-currency
make -j4
```

## Ryo Core - Windows

Install MSYS2 (<https://www.msys2.org/#installation>) and launch MINGW64 environment.

```
pacman --noconfirm -Syuu --overwrite *
pacman --noconfirm -Syuu --overwrite *
pacman --noconfirm -S --needed --overwrite * mingw-w64-x86_64-toolchain make mingw-w64-x86_64-cmake mingw-w64-x86_64-zeromq mingw-w64-x86_64-cppzmq mingw-w64-x86_64-libsodium mingw-w64-x86_64-hidapi mingw-w64-x86_64-protobuf mingw-w64-x86_64-libusb git pkg-config
pacman -U --noconfirm https://repo.msys2.org/mingw/mingw64/mingw-w64-x86_64-boost-1.83.0-2-any.pkg.tar.zst
pacman -U --noconfirm https://repo.msys2.org/mingw/mingw64/mingw-w64-x86_64-icu-74.1-1-any.pkg.tar.zst
git clone --branch dev-github-actions https://github.com/rtotr/ryo-currency.git
cd ryo-currency
make release-static-win64 -j4
```
