---
layout: post
title: "Create a Games app-folder in GNOME"
author: "rusty-snake"
tags: GNOME
---

Create the folder:

~~~ bash
gsettings set org.gnome.desktop.app-folders.folder:/org/gnome/desktop/app-folders/folders/Game/ name "Game.directory"
gsettings set org.gnome.desktop.app-folders.folder:/org/gnome/desktop/app-folders/folders/Game/ translate true
gsettings set org.gnome.desktop.app-folders.folder:/org/gnome/desktop/app-folders/folders/Game/ categories "['Game']"
~~~

Then add `'Game'` to `org.gnome.desktop.app-folders folder-children`.
