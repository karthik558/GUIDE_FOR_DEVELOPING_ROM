# DEPENDENCIES (This for setting-up your desktop environment)

- `sudo apt install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev`

- `bash <(curl -s https://raw.githubusercontent.com/akhilnarang/scripts/master/setup/android_build_env.sh)`

This for setting-up your desktop environment

# Adding Git Credentials

- `git config --global user.email "you@example.com"`
- `git config --global user.name "Your Name"`

Replace "you@example.com" with your acutal git email id and "Your Name" with your Name.

# CLONING ROM SOURCE (Moving onto clonning source this needs around 50-100 GB diskspace and internet)

- `repo init -u https://github.com/Project-ROM/manifest.git -b ROM-10`

- `repo sync --force-sync --no-tags --no-clone-bundle -j$(nproc --all)` 

- `repo sync --no-tags --no-clone-bundle --force-sync -c` (For upstream rom source )

# CLONNING DEVICE NEEDS (Now cloning device needed files)(Note:- included my device files repos change it according to device)

- `git clone https://github.com/CherishOS-Devices/device_xiaomi_6150-common device/xiaomi/sm6150-common`

- `git clone https://github.com/CherishOS-Devices/device_xiaomi_violet device/xiaomi/violet`

- `git clone https://github.com/karthik558/kernel_xiaomi_sm6150 kernel/xiaomi/sm6150`

- `git clone https://gitlab.com/karthik5581/proprietary_vendor_xiaomi vendor/xiaomi`

# CLONNING HALS (Same as i said on device needs but before clonning new hals remove old hals)

- `rm -rf hardware/qcom-caf/sm8150/display`

- `rm -rf hardware/qcom-caf/sm8150/audio`

- `rm -rf hardware/qcom-caf/sm8150/media`

- `git clone https://github.com/LineageOS/android_hardware_qcom_display -b lineage-17.1-caf-sm8150 hardware/qcom-caf/sm8150/display`

- git clone https://github.com/LineageOS/android_hardware_qcom_audio.git -b lineage-17.1-caf-sm8150 hardware/qcom-caf/sm8150/audio

- git clone https://github.com/LineageOS/android_hardware_qcom_media -b lineage-17.1-caf-sm8150 hardware/qcom-caf/sm8150/media

# CONFIGURING TO BUILD ROM

- `cd device/xiaomi/violet` 

- `nano AndroidProducts.mk` (Change according to rom)

- `nano rom_violet.mk` (Change according to rom)

# NOW STARTING BUILD

- `. build/envsetup.sh`

- `mka bacon | tee log`  ( According to source support )

- `export USE_CCACHE=1`

- `export CCACHE_EXEC=/usr/bin/ccache`

- `ccache -M 100G`

- `export CCACHE_COMPRESS=1`

- `breakfast violet` or `brunch violet` ( According to source support )

# UPLOADING FILES TO SOURCEFORGE

- `sftp username@frs.sourceforge.net`

- `cd /home/frs/project/"folder"`

# UPLOADING FILES TO GDRIVE

- `wget https://www.dropbox.com/s/w65lffvkkqvvj93/gdrive?dl=1`

- `mv gdrive?dl=1 gdrive` 

- `chmod +x gdrive`

- `./gdrive list`

- `./gdrive upload filename`

# Giving authorship for commits (When u pick a commit keep authorship)

- Open the patch on GitHub by adding .patch to the end of the commit's URL

- Type the following (supplying the name and date from the patch):
- `git commit --amend --author="Name <email>" --date="date"` 

eg:- git commit --amend --author="Karthik-SP <karthik.lal558@gmail.com>" --date="Sat, 3 Oct 2020 09:50:58 +0530"

# USING ADB TO TAKE LOGS

^ if your getting "unauthorized" msg, unlock device and type: ^

- `adb kill-server`

- `adb start-server`

^ Capture ADB logs using ADB commands ^

- Connect the device to pc

- Enable developer mode in your phone

- Turn on USB debbugging 

- Open cmd

- Type adb devices

- To capture ADB logs : `adb logcat`

- To stop capturing : ctrl + c

- To save logs : `adb logcat > V:/test.txt` (don't use C because c is protected)
