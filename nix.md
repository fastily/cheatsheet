## adduser
```bash
# add a new user interactively
sudo adduser '<NEW_USERNAME>'

# add a new service account interactively
sudo adduser --disabled-password '<NEW_USERNAME>'
```

## dd
```bash
# Write ISO to a USB.  Be sure to unmount any mounted partitions before attempting.
sudo dd bs=4M if='<PATH_TO_ISO>' of='<PATH_TO_USB_BLOCK_DEVICE>' && sync
```

## diff
```bash
# recursively compare two directories and list differences
diff -rq directory1/ directory2/
```

## dig
```bash
# get everything
dig example.com

# return MX records only
dig example.com MX
```

## eyeD3
```bash
eyeD3 -A '<ALBUM_NAME>' -b '<ALBUM_NAME>' --add-image '<PATH_TO_FILE>':FRONT_COVER '<INPUT_MP3>'
```

## exiftool
```bash
# delete all GPS and XMP metadata from a media file
exiftool -gps:all= -xmp-exif:all= '<FILES_TO_PROCESS>'
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

## git
```bash
# remove a file from git index but don't delete the local copy.
git rm --cached '<PATH_TO_FILE>'

# squash the last 3 commits
git reset --soft HEAD~3 && git commit -m '<NEW_MESSAGE>' && git push -f

# delete the most recent commit and rollback changes to the previous commit
git reset --hard HEAD~1

# add upstream to a GitHub fork
git remote add upstream 'https://github.com/<ORIGINAL_OWNER>/<ORIGINAL_REPOSITORY>.git'

# sync a GitHub fork with master.  Be sure to have added 'upstream' as a remote
git fetch upstream && git checkout master && git merge upstream/master

# show content of last stash
git stash show -p

# delete your local changes and replace with what is currently on master
git fetch --all && git reset --hard origin/master

# don't use your system keychain for this repository
git config --local credential.helper ""

# Have git prompt for your new password next push
git config --global --unset user.password

# sync a branch with master
git checkout master && git pull && git checkout '<BRANCH_TO_SYNC>' && git merge master

# cherry pick a commit
git cherry-pick -x '<COMMIT_SHA>'

# clear saved git passwords in macOS keychain, make sure to press enter key after each line.
git credential-osxkeychain erase
host=github.com
protocol=https
```

## gpg
```bash
# generate a key
gpg --full-generate-key

# list keys and show short IDs (used by gradle)
gpg --list-keys --keyid-format SHORT

# list keys for which I have both the public and private keys
gpg --list-secret-keys --keyid-format LONG

# Print GPG public key in ASCII armor format
gpg --armor --export "<GPG_KEY_ID>"

# Publish a public key (using Ubuntu's keyservers)
gpg --keyserver keyserver.ubuntu.com --send-keys "<GPG_KEY_ID>"

# Force gpg to output a secring.gpg file in the current directory
gpg --export-secret-keys -o secring.gpg
```

## grep
```bash
# recursive grep for text in files 
grep -rnw '<ROOT_DIRECTORY_TO_SEARCH>' -e '<PATTERN>'
```

## groups and users
```bash
# list current user's groups
groups

# list another user's groups
groups '<USERNAME>'

# Add existing user to new group
sudo usermod -a -G '<GROUP_TO_ADD>' '<USERNAME>'

# list users on a system
compgen -u
```

## imagemagick
```bash
# Remove a white background from an image
convert '<INPUT_FILE>' -fuzz 20% -transparent white out.png

# Make a GIF from JPG files in a directory
convert -dispose none -loop 0 -delay 100 *.JPG -resize 20% out.gif

# Create a favicon from a square png
convert '<SOURCE_PNG_FILE>' -define icon:auto-resize=128,96,64,48,32,16 favicon.ico

# Convert a pdf to png (high resolution)
convert -density 288 '<INPUT_PDF>' '<OUTPUT_PNG>'
```

## iperf3
```bash
# Start iperf3 server
iperf3 -s

# connect to server with iperf3 client
iperf3 -c '<SERVER_IP>'
```


## lsof
```bash
# Quickly (-n) list all open sockets by port (-P) on local device
lsof -Pn -i4
```

## ln
```bash
# create symlink.  Omit trailing slashes
ln -s '<DIRECTORY_TO_LINK_TO>' '<NEW_SYM_LINK_NAME>'
```

## nginx
```bash
# restart an nginx service
sudo nginx -t && sudo systemctl restart nginx
```

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


## php
```bash
# Initalize a dev php server at localhost:8080 rooted at ./public_html
php -S localhost:8080 -t public_html/
```

## ps
```bash
# get process name if you have its pid
ps -p '<PID>' -o comm=

# get detailed information about process with PID
ps -Flw -p '<THE_PID>'
```

## rdfind
```bash
# Recursively delete duplicate files in a directory
rdfind -deleteduplicates true '<PATH_TO_DIRECTORY>'
```

## rsync
```bash
# archive, show progress, delete files on dest.  Note trailing slash on SOURCE_FOLDER
rsync -avh --progress --delete "<SOURCE_FOLDER>/" "<DEST_FOLDER>"

# archive, use ssh to copy to dest on server
rsync -avh "<SOURCE_FOLDER>/" "user@myserver.com:<DEST_FOLDER>"
```

#### notes
`-a` stands for "archive mode", implies:
* `-r`: recursive
* `-l`: copy symlinks as symlinks
* `-p`: preserve permissions
* `-t`: preserve times
* `-g`: preserve group
* `-o`: preserve owner (super-user only)
* `-D`: preserve device files and special files

other interesting args:
* `-v` - verbose
* `-h` - human readable
* `-P` - show progress bar and keep partially copied files
* `-n` - dry run
* `--delete` - delete files on dest which are not in source 
* `-u` - skip files that are newer on destination

## pgrep
```bash
# compare against entire process name (why isn't this the default?!)
pgrep -f '<PATTERN>'
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

## samba
```bash
# create or change password of samba user
smbpasswd -a '<USERNAME_TO_CREATE_OR_CHANGE>'

# enable the account of an existing samba user
sudo smbpasswd -e '<USERNAME_TO_CREATE_OR_CHANGE>'

# create a system user for use with samba
sudo adduser --no-create-home --shell /usr/sbin/nologin --disabled-password --disabled-login --ingroup sambashare '<USERNAME>'

# Various ways to get status/information about smbd:
smbstatus
pdbedit -L -v
net usershare info --long
smbtree
```

## sox
```bash
# Generate a spectrogram for an audio file
sox '<INPUT_FILE>' -n spectrogram -o out.png
```

## ssh
```bash
# List supported key types on a client
ssh -Q key

# Probe a server about its supported ssh algorithims
nmap --script ssh2-enum-algos -sV -Pn -p 22 '<HOSTNAME_OR_IP>'

# Get info about an existing ssh key (either pub or priv key)
ssh-keygen -l -f '<PATH_TO_FILE>'

# Remove an entry from known_hosts
ssh-keygen -R '<HOSTNAME_OR_IP>'

# Generate a new ed25519 priv/pub pair (best practice)
ssh-keygen -t ed25519 -C '<DESCRIPTION>'

# Generate a new rsa priv/pub pair (legacy systems)
ssh-keygen -t rsa -b 4096 -C '<DESCRIPTION>'
```

## systemctl/systemd
```bash
# get status of a service
systemctl status '<SERVICE_NAME>'

# enable service at boot
systemctl enable '<SERVICE_NAME>'

# list all known services
systemctl list-units --all

# list all known unit files
systemctl list-unit-files

# display a unit file
systemctl cat '<SERVICE_NAME>'

# display service's dependencies
systemctl list-dependencies '<SERVICE_NAME>'

# mark a service as unstartable by nobody
systemctl mask '<SERVICE_NAME>'

# unmask a service and return it to its previous state
systemctl unmask '<SERVICE_NAME>'

# reload unit files after editing them
systemctl daemon-reload
```

## tar
```bash
# Extract .tar.gz
tar -xvzf '<PATH_TO_TAR_FILE>'

# Create .tar.xz, based out of the specified dir
tar -cJf '<NAME_OF_FILE>.tar.xz' -C 'DIR_TO_USE_AS_ROOT_OF_TAR' .

# Create .tar.xz, use as many threads as possible
XZ_OPT='-T0' tar -cJf '<NAME_OF_FILE>.tar.xz' .
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

## wget
```bash
# download all media files on a page
wget -nd -r -l 1 -H -A png,gif,jpg,svg,jpeg,webm -e robots=off '<WEBSITE_URL>'

# recursively download the contents of a website
wget -e robots=off -m -k -np -w 5 '<URL>'

# download contents of an open directory (not recursive)
wget --no-directories --no-parent -r -l 1 -H '<URL>'
```

## whois
```bash
# get whois data for host
whois example.com
```

## xxd
```bash
# view binary files
xxd -b '<THE_FILE>' | less
```

## yt-dlp
```bash
# rip embedded vimeo
yt-dlp '<LINK_TO_VIDEO>' --referer '<LINK_TO_PAGE_VIDEO_IS_EMBEDED_ON>'
```