mkdir PixelOS && cd PixelOS

repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fifteen --git-lfs

mkdir .repo/local_manifests && https://raw.githubusercontent.com/pixelos-oneplus9-series/manifest/main/OnePlus9Series.xml -O .repo/local_manifests/lemonadep.xml

repo sync -c --force-sync --optimized-fetch --no-tags --no-clone-bundle --prune -j$(nproc --all)

lunch aosp_lemonadep-bp1a-user

mka bacon  -j$(nproc --all)
