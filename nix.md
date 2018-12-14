## nmap
```bash
# Scan all ports, no ping (-Pn), no DNS resolution (-n, helps reduce scan time)
nmap -n -Pn -p 0-65535 127.0.0.1

# Scan specific ports, no ping
nmap -Pn -p 80,443,555 127.0.0.1

# Scan all ports, be aggressive, probe for OS/app versions
nmap -p 1-65535 -T4 -A -v 127.0.0.1

# Host discovery on a CIDR range
nmap -sP 10.0.1.0/24
```

#### other options
* `-A` - enables OS/version detection, script scanning, and traceroute
* `--allports` - enables scanning on 9100, a printer port.  Caveat: some printers print anything sent to this port.
* `-T4`/`-T5` - use an aggressive/insane timing template

## dd
```bash
# Write ISO to a USB.  Be sure to unmount any mounted partitions before attempting.
sudo dd bs=4M if='<PATH_TO_ISO>' of='<PATH_TO_USB_BLOCK_DEVICE>' && sync
```

## smb
```bash
# create SMB user or change the password of an existing user
smbpasswd -a USERNAME_TO_CREATE_OR_CHANGE

# Various ways to get status/information about sambad:
smbstatus
pdbedit -L -v
net usershare info --long
smbtree
```

## virtualbox
```bash
# Allow shared folders in Virtualbox w/ Ubuntu guest.  Run command on ubuntu guest.
sudo adduser $( whoami ) vboxsf
```

## ssh-keygen
```bash
# Generate a new rsa private/public key pair.
ssh-keygen -t rsa -b 8192 -C '<DESCRIPTION>'
```

#### Both
```bash
# Trim audio/video (ex: start at 5 sec and go until 2 min)
ffmpeg -i '<INPUT_FILE>' -c:a copy -c:v copy -ss 5 -t 120 out.<EXT>
```

## imagemagick
```bash
# Remove a white background from an image
convert '<INPUT_FILE>' -fuzz 20% -transparent white out.png

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
tar -xvzf '<PATH_TO_TARBALL>'
```

## Get external-facing IP address
```bash
curl icanhazip.com
```

## sox
```bash
# Generate a spectrogram for an audio file
sox '<INPUT_FILE>' -n spectrogram -o out.png
```

## xxd
```bash
# view binary files
xxd -b '<THE_FILE>' | less
```

## screen
```bash
# Start a new screen
screen '<PROGRAM_TO_RUN>' '<PROGRAM_ARGUMENTS>'
```
* Enter command mode, use shortcut `Control` + `a` while running a screen.
 * To detach from the screen, press `d`.
 * To kill the current screen, press `k`.
 * To get documentation, press `?`.

```bash
# List screens from bash
screen -ls

# Reattach a screen
screen -r '<PID>' # pid comes from doing screen -ls
```

## python3
```bash
# start webserver in current working directory
python -m http.server 8000
```

## yotuube-dl
```bash
# Download embed-only vimeo videos
youtube-dl '<LINK_TO_VIDEO>' --referer '<LINK_TO_PAGE_VIDEO_IS_EMBEDED_ON>'
```

## find
```bash
# find all files in a directory older than 10 days and delete them
find '<PATH_TO_DIRECTORY>' -mtime +10 -name '*.pdf' -type f -delete


# Recursively delete music metadata files
find . -name '*.nfo' -type f -delete
find . -name '*.m3u' -type f -delete
find . -name '*.m3u8' -type f -delete

```

## django
```bash
# create new project
django-admin startproject '<PROJECT_NAME>'

# add sub-app to project
python3 manage.py startapp '<APP_NAME>'

# start server
python3 manage.py runserver

# create migration
python3 manage.py makemigrations

# migrate db
python3 manage.py migrate

# create superuser for admin panel
python3 manage.py createsuperuser

# collect static files into one folder
python3 manage.py collectstatic
```

## git
```bash
# remove a file from git index but don't delete the local copy.
git rm --cached '<PATH_TO_FILE>'

# squash the last 3 commits
git reset --soft HEAD~3 && git commit -m '<NEW_MESSAGE>' && git push -f

## add upstream to a GitHub fork
git remote add upstream 'https://github.com/<ORIGINAL_OWNER>/<ORIGINAL_REPOSITORY>.git'

## sync a GitHub fork with master.  Be sure to have added 'upstream' as a remote
git fetch upstream && git checkout master && git merge upstream/master
```

## eyeD3
```bash
eyeD3 -A '<ALBUM_NAME>' -b '<ALBUM_NAME>' --add-image '<PATH_TO_FILE>':FRONT_COVER '<INPUT_MP3>'
```

## pip
```bash
# generate requirements.txt
pip freeze > requirements.txt

# upgrade a package
pip install --upgrade '<PACKAGE_NAME>'

# list outdated packages
pip list --outdated
```

## wget
```bash
# download all media files on a page
wget -nd -r -l 1 -H -A png,gif,jpg,svg,jpeg,webm -e robots=off  '<WEBSITE_URL_HERE>'
```

## ufw
```bash
# see all registered firewall profiles
ufw app list

# allow a profile/rule
ufw allow '<PROFILE/PORT>'

# delete an allow rule
ufw delete allow '<PROFILE/PORT>'

# start firewall
ufw enable

# show status
ufw status
```

## nginx
```bash
# restart an nginx service
sudo nginx -t && sudo systemctl restart nginx
```

## gunicorn
```bash
# restart a gunicorn service
sudo systemctl restart gunicorn
```