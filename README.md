# aosp_build_guides_sweet


## 1. Installing dependencies and Repo:
```bash
sudo apt install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git git-lfs gnupg gperf imagemagick lib32ncurses-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses libncurses-dev libsdl1.2-dev libssl-dev libwxgtk3.0-gtk3-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev
```

## 2. Install Repo tool:
```bash
mkdir /media/tbs96/D/bin
PATH=/media/tbs96/D/bin:$PATH
```
```bash
curl https://storage.googleapis.com/git-repo-downloads/repo > /media/tbs96/D/bin/repo
chmod a+x /media/tbs96/D/bin/repo
```

## 3. Initializing Repo:
```bash
mkdir RomFolderName && cd RomFolderName
```
```bash
repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fourteen --git-lfs
```
```bash
repo sync
```

## 4. Sync `Device Trees`(common if needed), `Vendor`(common if needed), `Hardware`, `Kernel`:

```bash
git clone https://github.com/PixelOS-Devices/device_xiaomi_sweet.git device/xiaomi/sweet
```
```bash
git clone https://github.com/PixelOS-Devices/device_xiaomi_sm6150-common.git device/xiaomi/sm6150-common
```
```bash
git clone https://github.com/PixelOS-Devices/vendor_xiaomi_sweet.git vendor/xiaomi/sweet
```
```bash
git clone https://github.com/PixelOS-Devices/vendor_xiaomi_sm6150-common.git vendor/xiaomi/sm-6150-common
```
```bash
git clone https://github.com/PixelOS-AOSP/hardware_xiaomi.git hardware/xiaomi
```
```bash
git clone https://github.com/PixelOS-Devices/kernel_xiaomi_sm6150.git kernel/xiaomi/sm6150
```
### 4.1. Delete `lineage.dependencies` from `/hardware` if present (This file is for if we build on servers)

### 4.2. Things to remember, and check whether source uses common trees or not. Also helpful for beginners to see file structure, aosp or lineage:
<div align="center">
  <img src="https://github.com/TBS96/aosp_build_guides_sweet/blob/main/AndroidProducts.mk-pixelos_device_xiaomi_sweet.png">
  <img src="https://github.com/TBS96/aosp_build_guides_sweet/blob/main/Android.bp-vendor_xiaomi_sweet.png">
</div>

### `optional:`
```bash
repo sync
```

## 5. Initialize the ROM environment with the envsetup.sh script:
```bash
. build/envsetup.sh
```

## 6. Lunch your device after cloning all device sources if needed:
```bash
lunch aosp_sweet-ap2a-buildtype
```

## 7. Start compilation:
```bash
mka bacon
```
