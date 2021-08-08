## Hide a file/folder
```bash
# Hide
chflags hidden <FILE_NAME>

# Show
chflags nohidden <FILE_NAME>
```

## Recursively delete .DS_STORE
```bash
find . -name '*.DS_Store' -type f -delete
```

## Make password-protected, encypted zips
```bash
# Encypt and zip two files
zip -e '<ARCHIVE>.zip' 'input1.txt' 'input2.txt'

# Encypt and zip a directory
zip -er '<ARCHIVE>.zip' '<PATH_TO_DIRECTORY>'
```

## Software Update via Terminal
```bash
# Check for new updates
softwareupdate -l

# Install an update
softwareupdate -i '<FULL_NAME_OF_UPDATE>'

# Install all available updates
softwareupdate -ai
```

## Show information about a volume
```bash
diskutil info '<PATH_TO_VOLUME>'
```

## Get summed lengths of videos in folders of current dir
```bash
for d in */ ; do
	mdls "$d"/*.mov | grep Duration | awk '{ print $3 }' | paste -s -d+ - | bc
done
```

## Show hardware information
```bash
# general hardware information
system_profiler SPHardwareDataType

# show name of CPU
sysctl -n machdep.cpu.brand_string

# show arch
uname -m
```

## Uninstall Xcode CLI tools
```bash
sudo rm -rf "/Library/Developer/CommandLineTools"
```

## WiFi info
```bash
# Show Available WiFi Networks
/System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -s

# Get information about current WiFi connection
/System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -s
```

## Change Wallpaper
```bash
osascript -e 'tell application "Finder" to set desktop picture to POSIX file "<ABSOLUTE_PATH_TO_JPG>"'
```