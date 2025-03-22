---
layout: post
title: "FFmpeg Commands"
author: "rusty-snake"
tags: ffmpeg
---

## Convert a Video DVD to mp4

~~~bash
ffmpeg -i "concat:VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" output.mp4
~~~

## Merger separated video and audio streams/files

~~~ bash
ffmpeg -i video.mp4 -i audio.mp4 -c copy video-with-audio.mp4
~~~

## Extract the audio track from a video

~~~ bash
ffmpeg -i input.mp4 -vn -c:a copy output.aac
~~~

## Fix XING VBR Header of a mp3 file

~~~bash
ffmpeg -i original-track.mp3 -c:a copy fixed-track.mp3
~~~

## Convert wav to mp3

~~~ bash
ffmpeg -i input.wav -c:a libmp3lame output.mp3
~~~

## Convert H.265/HEVC to H.264/MPEG-4

because OpenShot crashes when adding a h265 video to a project.

~~~bash
ffmpeg -i input.mp4 -c:v libx264 -c:a copy output.mp4
~~~

## Horizontally flip a video

~~~bash
ffmpeg -i input.mp4 -vf hflip -c:v libx264 -c:a copy output.mp4
~~~

TODO: VA-API accelerated de/encoding.

<details markdown="1"><summary>Python script for batch processing:</summary>

~~~python
#!/usr/bin/python3

import os
import os.path
import subprocess


for file in os.listdir():
    stem, ext = os.path.splitext(os.path.basename(file))
    if ext != "mp4" or stem.endswith(".hflip"):
        continue
    subprocess.run(
        [
            "ffmpeg",
            "-i",
            file,
            "-vf",
            "hflip",
            "-c:v",
            "libx264",
            "-c:a",
            "copy",
            stem + ".hflip" + ext,
        ],
        check=True,
    )
~~~

</details>
