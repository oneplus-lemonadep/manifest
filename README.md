mkdir PixelOS && cd PixelOS

repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fifteen --git-lfs

mkdir .repo/local_manifests && wget https://raw.githubusercontent.com/pixelos-oneplus9-series/manifest/main/OnePlus9Series.xml -O .repo/local_manifests/OnePlus9Series.xml

repo sync -c --force-sync --optimized-fetch --no-tags --no-clone-bundle --prune -j$(nproc --all)

#To build for OnePlus 9 Pro aka lemonadep

lunch aosp_lemonadep-bp1a-user

#To build for OnePlus 9 aka lemonade

lunch aosp_lemonade-bp1a-user

#start Compilation
mka bacon  -j$(nproc --all)
