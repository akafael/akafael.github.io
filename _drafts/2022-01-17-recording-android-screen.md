---
layout: post
title:  ""
date:   2022-01-17 18:00:00
categories: wiki
tags: [android,linux]
lang: en
ref: recording-android-screen
img:
---


You can record the Android screen using [adb](https://developer.android.com/studio/command-line/adb). 


1. `adb shell screenrecord /sdcard/video.mp4`
2. Hit `Ctrl` + `C` to stop recording
3. `adb pull /sdcard/video.mp4`
4. `adb shell rm /sdcard/video.mp4`

