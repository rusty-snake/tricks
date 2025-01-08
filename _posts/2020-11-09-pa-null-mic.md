---
layout: post
title: "Create a dummy microphone with pulseaudio"
author: "rusty-snake"
#tags:
---

~~~ console
$ pactl load-module module-null-source && pactl set-default-source source.null
~~~

This is helpful in situations where a program fails to function properly without a microphone,
even though one isn't actually needed, and you don't have any microphone hardware connected.

**Update Oct 2021**: In the meantime Fedora has switched to PipeWire. Unfortunately, pipewire-pulse
does not support `module-null-source`. The [Migrate-PulseAudio wikipage] has a
note to do the same with `pw-cli`, but this did not worked for me.
Fortunately the [Virtual-Devices wikipage] has a working solution:

~~~ console
$ pactl load-module module-null-sink media.class=Audio/Source/Virtual sink_name="Null Source"
~~~

[Migrate-PulseAudio wikipage]: https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Migrate-PulseAudio#module-null-source
[Virtual-Devices wikipage]: https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Virtual-Devices#create-a-source
