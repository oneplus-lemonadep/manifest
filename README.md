mkdir PixelOS && cd PixelOS

repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fifteen --git-lfs

mkdir .repo/local_manifests && wget https://raw.githubusercontent.com/oneplus-lemonadep/manifest/fifteen/lemonadep.xml -O .repo/local_manifests/lemonadep.xml

repo sync -c --force-sync --optimized-fetch --no-tags --no-clone-bundle --prune -j$(nproc --all)

#To build for OnePlus 9 Pro aka lemonadep

lunch aosp_lemonadep-bp1a-user

#start Compilation
mka bacon  -j$(nproc --all)
