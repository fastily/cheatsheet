# Useful 'nix commands
## nmap
```bash
# Scan all ports, no ping (-Pn), no DNS resolution (-n, helps reduce scan time)
nmap -n -Pn -p 0-65535 127.0.0.1

# Scan specific ports, no ping
nmap -Pn -p 80,443,555 127.0.0.1

# Scan all ports, be aggressive, probe for OS/app versions
nmap -p 1-65535 -T4 -A -v 127.0.0.1
```

#### other options
* `-A` - enables OS/version detection, script scanning, and traceroute
* `--allports` - enables scanning on 9100, a printer port.  Caveat: some printers print anything sent to this port.
* `-T4`/`-T5` - use an aggressive/insane timing template

## dd
Write an ISO to a USB.  Be sure to unmount any mounted partitions before attempting.
```bash
dd bs=4M if=<PATH_TO_ISO> of=<PATH_TO_USB_BLOCK_DEVICE> && sync
```

## smb
To create a new SMB user, or to change the password of an existing user:
```bash
smbpasswd -a USERNAME_TO_CREATE_OR_CHANGE
```

Different ways to get status/information about sambad:
```bash
smbstatus
pdbedit -L -v
net usershare info --long
smbtree
```

## VirtualBox
To allow shared folders in Virtualbox with an Ubuntu guest, run
```bash
sudo adduser $( whoami ) vboxsf
```
on the Ubuntu guest.

## ssh-keygen
Generate a new rsa private/public key pair.

```bash
ssh-keygen -t rsa -b 8192 -C "DESCRIPTION_HERE"
```

## ffmpeg
#### Audio
```bash
# Convert audio to mp3
ffmpeg -i <INPUT_FILE> -vn -c:a libmp3lame -b:a 320k out.mp3

# Convert audio to flac
ffmpeg -i <INPUT_FILE> -vn -c:a flac out.flac

# Convert audio to wav
ffmpeg -i <INPUT_FILE> -vn -c:a pcm_s16le out.wav

# Convert audio to oga
ffmpeg -i <INPUT_FILE> -vn -c:a libvorbis -q:a 10 out.oga

# Convert every flac file in the current directory to mp3
for f in *.flac; do ffmpeg -i  "$f" -vn -c:a libmp3lame -b:a 320k "${f%.flac}.mp3"; done;
```

#### Video
```bash
# Convert video to ogv
ffmpeg -i <INPUT_FILE> -c:v libtheora -q:v 10 -c:a libvorbis -q:a 10 out.ogv

# Convert video to webm
ffmpeg -i <INPUT_FILE> -c:v libvpx-vp9 -b:v 0 -crf 24 -threads 4 -speed 0 -c:a libvorbis -q:a 8 -f webm out.webm

# Convert every MOV file in the current directory to audioless webm
for f in *.MOV; do ffmpeg -i  "$f" -an -c:v libvpx-vp9 -b:v 0 -crf 24 -threads 4 -speed 0 -f webm "${f%.MOV}.webm"; done;
```

##### Effects
###### Rotation
* 0 = 90° CounterCLockwise and Vertical Flip (default)
* 1 = 90° Clockwise
* 2 = 90° Counter-Clockwise
* 3 = 90° Clockwise and Vertical Flip

`-vf "transpose=2,transpose=2"` or `-vf "hflip"` for 180 degrees.

Example:
```bash
# Rotate video 90° Clockwise
ffmpeg -i <INPUT_FILE> -vf "transpose=1" -c:v libtheora -q:v 10 -c:a libvorbis -q:a 10 out.ogv
```
* [Rotate Guide](https://stackoverflow.com/a/9570992/5987787)
* [How to rotate a video 180° with FFmpeg?](https://superuser.com/questions/578321/how-to-rotate-a-video-180-with-ffmpeg)

##### Slow-Motion/Timelapse
```bash
# Timelapse - 16x slowdown, forced 60fps
ffmpeg -i <INPUT_FILE> -an -r 60 -vf "setpts=0.0625*PTS" -c:v libtheora -q:v 10 out.ogv

# Slow-Motion - 8x speedup, forced 30fps
ffmpeg -i <INPUT_FILE> -an -r 30 -vf "setpts=8*PTS" -c:v libtheora -q:v 10 out.ogv

# Convert every MOV file in the current directory to audioless webm, slowed down 8x
for f in *.MOV; do ffmpeg -i  "$f" -an -r 30 -vf "setpts=8*PTS" -c:v libvpx-vp9 -b:v 0 -crf 24 -threads 4 -speed 0 -f webm "${f%.MOV}.webm"; done;
```

## imagemagick
```bash
# Remove a white background from an image
convert <INPUT_FILE> -fuzz 20% -transparent white out.png

# Make a GIF from JPG files in a directory
convert -dispose none -loop 0 -delay 100 *.JPG -resize 20% out.gif
```

## php
```bash
# Initalize a dev php server at localhost:8080 rooted at ./public_html
php -S localhost:8080 -t public_html/
```

## tar
```bash
# Extract a .tar.gz archive
tar -xvzf <PATH_TO_TARBALL>
```