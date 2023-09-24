---
layout: post
title:  "Nautilus scripts"
author: "rusty-snake"
#tags:
---

Nautilus (GNOME File Manager) supports custom script to take actions on files.
These scripts are placed in `~/.local/share/nautilus/scripts`.

## pngquant

~~~ bash
#!/bin/bash
for file in "$@"; do
    if [[ -e $file && $(file --mime-type --brief "$file") == "image/png" ]]; then
        pngquant --skip-if-larger --quality 50-100 --strip "$file"
        exit_code=$?
        if [[ $exit_code -eq 99 ]]; then
            zenity --error --title=pngquant --text="Too much quality loss. Image can not be converted."
        elif [[ $exit_code -eq 98 ]]; then
            zenity --error --title=pngquant --text="Too little size gain. Image can not be converted."
        fi
    fi
done
~~~

## Run in firejail

~~~ bash
#!/bin/bash
if [[ $# -gt 1 ]]; then
    zenity --error --title="Run in firejail" --text="Too many arguments.\n\nYou can only run one program in firejail."
    exit 2
fi
exec firejail "$1"
~~~
