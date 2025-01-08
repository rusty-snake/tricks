---
layout: post
title: "Extract apks from Factory Images"
author: "rusty-snake"
#tags:
---

A short note how you can extract an apk from Factory Images.

Factory Images for Pixel Devices can be found and downloaded
[here](https://developers.google.com/android/images).

~~~ bash
unzip oriole-sq3a.220705.003-factory-4ec7503a.zip
cd oriole-sq3a.220705.003
unzip image-oriole-sq3a.220705.003.zip
# simg2img is no longer required for Android 13 and later
simg2img product.img 00_product.img
gnome-disk-image-mounter 00_product.img
gio mount -d /dev/loop0
cd $XDG_RUNTIME_DIR/product
cp app/PixelWallpapers2021/PixelWallpapers2021.apk ~/Downloads
cp app/Photos/Photos.apk ~/Downloads
cp priv-app/GoogleCamera/GoogleCamera.apk ~/Downloads
cd
gio mount -u $XDG_RUNTIME_DIR/product
~~~

