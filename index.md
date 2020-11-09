# Tips & Tricks

## Create a dummy microphone with pulseaudio

```
$ pactl load-module module-null-source && pactl set-default-source source.null
```

This is useful if, for example, a program does not work without a microphone even though none is required.
And you have no microphone hardware connected.
