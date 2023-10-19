### Device specific configuration to build AOSP Android 13 for Raspberry Pi 4.

***

### How to build:

1. Establish [Android build environment](https://source.android.com/setup/initializing) and install [repo](https://source.android.com/docs/setup/develop#installing-repo).

2. Install additional packages:

```
sudo apt-get install bc coreutils dosfstools e2fsprogs fdisk kpartx mtools ninja-build pkg-config python3-pip
sudo pip3 install meson mako jinja2 ply pyyaml dataclasses
```

3. Initialize repo:

```
repo init -u https://android.googlesource.com/platform/manifest -b android-13.0.0_r67 --depth=1
curl --create-dirs -L -o .repo/local_manifests/manifest_brcm_rpi4.xml -O -L https://raw.githubusercontent.com/SpyroSoft-Synergy/roscar_local_manifest/android-13.0/manifest_brcm_rpi4.xml
curl --create-dirs -L -o .repo/local_manifests/remove_projects.xml -O -L https://raw.githubusercontent.com/SpyroSoft-Synergy/roscar_local_manifest/android-13.0/remove_projects.xml
```

4. Sync source code:

```
repo sync
```

5. Build the AOSP image:

```
./make_libmicroros.sh
```
```
./make_aosp_img.sh
```

6. Make flashable image:

```
./rpi4-mkimg.sh
```

***

### Issues:

- [Android](https://github.com/raspberry-vanilla/android_local_manifest/issues)
- [Linux kernel](https://github.com/raspberry-vanilla/android_kernel_manifest/issues)

***

### Wiki:

- [Audio](https://github.com/raspberry-vanilla/android_local_manifest/wiki/Audio)
- [DSI display](https://github.com/raspberry-vanilla/android_local_manifest/wiki/DSI-display)
- [HDMI display](https://github.com/raspberry-vanilla/android_local_manifest/wiki/HDMI-display)
- [HDMI-CEC](https://github.com/raspberry-vanilla/android_local_manifest/wiki/HDMI-CEC)
- [Interfaces](https://github.com/raspberry-vanilla/android_local_manifest/wiki/Interfaces)
- [USB boot](https://github.com/raspberry-vanilla/android_local_manifest/wiki/USB-boot)
- [Video decoding & encoding](https://github.com/raspberry-vanilla/android_local_manifest/wiki/Video-decoding-&-encoding)
