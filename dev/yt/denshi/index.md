## Teach me something!

> DenshiVideo on Youtube

### _ FFMPEG Video Editing _

```bash
$ ffmpeg -i {input} {output}
$ ffmpeg -i Cabin-Snow.mp4 Output.mkv

$ ffmpeg -c:v {vcodec} -c:a {acodec}
$ ffmpeg -i Cabin-Snow.mp4 -c:v libx265 -c:a aac Output.mkv

$ ffmpeg -encoders >> encoders.txt
# list all video audio codecs

$ ffmpeg -s {horz}x{vert}
$ ffmpeg -i Some.mkv -s 1280x720 Outro.mkv

# audio rate
$ ffmpeg -r:a 44100 -i {} {}.{}

# video & audio bit-rate
$ ffmpeg -b:v 1M -b:a 192k -i Intro.mkv Outro.mkv

# use CRF for video bit rate (even better)
# lower the number - higher the quality and the file size too
$ ffmpeg -crf 24 

# start and end where?
$ ffmpeg -ss 00:00:00.0 00:00:05.0 

# mix AUDIO & IMAGE
$ ffmpeg -i MyPick.mp3 -i Image.png -c:v libx265 -crf 20 -b:a 192k Final.mp4
```

**Sum UP?**
-i input
-c:[a/v] for codecs
-r:[a/v] for rates | -crf for video-bit rate
-s {h}x{v} for screen-size
-encoders to list

<< Change duration?
-ss {hrs}:{mins}:{secs}.{msecs} as start time
-t 00:00:10.0 as end time

**Specify** an output file as well.
