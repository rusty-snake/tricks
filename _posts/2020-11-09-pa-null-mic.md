---
layout: post
title:  "Create a dummy microphone with pulseaudio"
author: "rusty-snake"
#tags:
---

```
$ pactl load-module module-null-source && pactl set-default-source source.null
```

This is useful if, for example, a program does not work without a microphone even though none is required.
And you have no microphone hardware connected.

**Update Oct 2021**: In the meantime Fedora has switched to PipeWire. Unfortunately does
pipewire-pulse not support `module-null-source`. The [Migrate-PulseAudio wikipage] has a
note to do the same with `pw-cli`, but this did not worked for me.
Fortunately the [Virtual-Devices wikipage] has a working solution:

```
$ pactl load-module module-null-sink media.class=Audio/Source/Virtual sink_name="Null Source"
```

[Migrate-PulseAudio wikipage]: https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Migrate-PulseAudio#module-null-source
[Virtual-Devices wikipage]: https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Virtual-Devices#create-a-source
