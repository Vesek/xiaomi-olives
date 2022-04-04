# Ubuntu Touch device tree for the Xiaomi Redmi 8/8A/8A Pro (olive/olivelite/olivewood)

This is based on Halium 11.0, and uses the mechanism described in [this
page](https://github.com/ubports/porting-notes/wiki/GitLab-CI-builds-for-devices-based-on-halium_arm64-(Halium-10)).

This project can be built manually (see the instructions below) or you can
download the ready-made artifacts from gitlab: take the [latest
archive](https://gitlab.com/ubports/community-ports/android10/xiaomi-redmi-8/xiaomi-olives/-/jobs/artifacts/master/download?job=devel-flashable),
unpack the `artifacts.zip` file (make sure that all files are created inside a
directory called `out/`, then follow the instructions in the
[Install](#install) section.


## How to build

To manually build this project, follow these steps:

```bash
./build.sh -b bd  # bd is the name of the build directory
./build/prepare-fake-ota.sh out/device_olives.tar.xz ota
./build/system-image-from-ota.sh ota/ubuntu_command out
```


## Install

After the build process has successfully completed, run

```bash
fastboot flash boot out/boot.img
fastboot flash system out/system.img
```

## Splash screen

If you'd like to change the splash screen, run

```
./splash/generate.sh out
fastboot flash splash out/splash.img
```
