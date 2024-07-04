---
layout: post
title: "FFmpeg Commands"
author: "rusty-snake"
#tags:
---

## Convert a Video DVD to mp4

~~~bash
ffmpeg -i "concat:VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" output.mp4
~~~

## Convert H.265/HEVC to H.264/MPEG-4

because OpenShot crashes when adding a h265 video to a project.

~~~bash
ffmpeg -i input.mp4 -c:v libx264 -c:a copy output.mp4
~~~

## Fix XING VBR Header of a mp3 file

~~~bash
ffmpeg -i original-track.mp3 -acodec copy fixed-track.mp3
~~~

## Horizontally flip a video

~~~bash
ffmpeg -i input.mp4 -vf hflip -c:a copy
~~~

Python script for batch processing:

~~~python
#!/usr/bin/python3

import os
import os.path
import subprocess


for file in os.listdir():
    stem, ext = os.path.splitext(os.path.basename(file))
    if stem.endswith(".hflip"):
        continue
    subprocess.run(
        [
            "ffmpeg",
            "-i",
            file,
            "-vf",
            "hflip",
            "-c:a",
            "copy",
            stem + ".hflip" + ext,
        ],
        check=True,
    )
~~~

## Extract the audio track from a video

~~~ bash
ffmpeg -i input.mp4 -vn -acodec copy output.aac
~~~

## Convert wav to mp3

~~~ bash
ffmpeg -i input.wav -acodec libmp3lame output.mp3
~~~
