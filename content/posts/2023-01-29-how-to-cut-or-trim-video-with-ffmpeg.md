---
title: How to cut (or trim) video with FFmpeg
date: 2023-01-29T07:11:00+08:00
---

The browser history tells me I've visted [this FFmpeg HOWTO page](1) many times as I get handy with the tool:

1. My brain works on absolute, not relative, time so I'd much rather be able to directly indicate when to start cutting `-ss`, and when to stop `-to`;
1. I also want to only copy the original video/audio, without any re-encoding, hence the `-c:v copy -c:a copy` part.

Putting it all together: we take some input file `foo.webm`, cut from the 10-second mark onwards, copy its video/audio, resulting in a 59-second long output file `bar.webm`:

```text
ffmpeg -i foo.webm \
  -ss 00:00:10 -to 01:09 \
  -c:v copy -c:a copy \
  bar.webm
```

[1]: https://shotstack.io/learn/use-ffmpeg-to-trim-video/
