## Transcode Audio
```bash
# Convert audio to mp3
ffmpeg -i '<INPUT_FILE>' -vn -c:a libmp3lame -b:a 320k out.mp3

# Convert audio to flac
ffmpeg -i '<INPUT_FILE>' -vn -c:a flac out.flac

# Convert audio to wav
ffmpeg -i '<INPUT_FILE>' -vn -c:a pcm_s16le out.wav

# Convert audio to oga
ffmpeg -i '<INPUT_FILE>' -vn -c:a libvorbis -q:a 10 out.oga

# Convert every flac file in the current directory to mp3
for f in *.flac; do ffmpeg -i  "$f" -vn -c:a libmp3lame -b:a 320k "${f%.flac}.mp3"; done;
```

## Transcode Video
```bash
# Convert video to ogv
ffmpeg -i '<INPUT_FILE>' -c:v libtheora -q:v 10 -c:a libvorbis -q:a 10 out.ogv

# Convert video to webm
ffmpeg -i '<INPUT_FILE>' -c:v libvpx-vp9 -b:v 0 -crf 24 -threads 4 -speed 0 -c:a libvorbis -q:a 8 -f webm out.webm

# Convert every MOV file in the current directory to audioless webm
for f in *.MOV; do ffmpeg -i "$f" -an -c:v libvpx-vp9 -b:v 0 -crf 24 -threads 4 -speed 0 -f webm "${f%.MOV}.webm"; done;
```

## Video Effects
### Rotation
* 0 = 90° CounterCLockwise and Vertical Flip (default)
* 1 = 90° Clockwise
* 2 = 90° Counter-Clockwise
* 3 = 90° Clockwise and Vertical Flip

`-vf "transpose=2,transpose=2"` or `-vf "hflip"` for 180 degrees.

```bash
# Rotate video 90° Clockwise
ffmpeg -i '<INPUT_FILE>' -vf "transpose=1" -c:v libtheora -q:v 10 -c:a libvorbis -q:a 10 '<OUTPUT_FILE>'

# Rotate using metadata (no transcode needed)
ffmpeg -i '<INPUT_FILE>' -c copy -metadata:s:v rotate="90" '<OUTPUT_FILE>'
```
* [Rotate Guide](https://stackoverflow.com/a/9570992/5987787)
* [How to rotate a video 180° with FFmpeg?](https://superuser.com/questions/578321/how-to-rotate-a-video-180-with-ffmpeg)


### Slow-Motion/Timelapse
```bash
# Timelapse - 16x slowdown, forced 60fps
ffmpeg -i '<INPUT_FILE>' -an -r 60 -vf "setpts=0.0625*PTS" -c:v libtheora -q:v 10 out.ogv

# Slow-Motion - 8x speedup, forced 30fps
ffmpeg -i '<INPUT_FILE>' -an -r 30 -vf "setpts=8*PTS" -c:v libtheora -q:v 10 out.ogv

# Convert every MOV file in the current directory to audioless webm, slowed down 8x
for f in *.MOV; do ffmpeg -i "$f" -an -r 30 -vf "setpts=8*PTS" -c:v libvpx-vp9 -b:v 0 -crf 24 -threads 4 -speed 0 -f webm "${f%.MOV}.webm"; done;
```


## Join MP4s
```bash
# Convert all files to ts, then concatenate them
for f in *.mp4; do ffmpeg -i "$f" -c copy -bsf:v h264_mp4toannexb -f mpegts "${f%.mp4}.ts"; done;
ffmpeg -i "concat:FILE1.ts|FILE2.ts|FILE3.ts" -c copy -bsf:a aac_adtstoasc '<OUTPUT_FILE>'
```

* [Concat Guide](https://trac.ffmpeg.org/wiki/Concatenate#protocol)