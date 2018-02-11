---
layout: post
title:  "Creating desktop shortcut on Linux"
date:   2016-12-03 18:00:00
categories: code
tags: [linux,tutorial]
lang: en
ref: linux-desktop-shortcut
---

Sometimes is just annoying to open terminal each time you need some program running. This is a basic tutorial to generate a link file using the [Desktop Entry Especification](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#introduction) format. It works for KDE, GNOME or Unity desktop enviromments.

## 1. Create a file with extention _.desktop_ whith the following content

```
$ gedit myProgram.desktop
```

Content:

<script src="https://gist.github.com/akafael/f7583856ba1e200264cbf3de5a42e9b2.js"></script>

For more details about the format check this [specifications](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#basic-format).

## 2. Copy your for the default Applications Link folder

Command for user only access

```
$ cp myProgram.desktop ~/.local/share/applications/myProgram.desktop
```

Command for all user access

```
sudo cp myProgram.desktop /usr/share/applications/myProgram.desktop
```

## Extra

### Changing Icon

 You may save your icon in system place amoung the others at _/usr/share/icons_ and set the path at your _.desktop_ file.

### UnityLaunchers

UnityLauchers are also _.desktop_ files and allow to create right-click menus for each application. You may check the details [here](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles) at Ubuntu Documentation.