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
zip -e <ARCHIVE>.zip input1.txt input2.txt

# Encypt and zip a directory
zip -er <ARCHIVE>.zip <PATH_TO_DIRECTORY>
```

## Software Update via Terminal
```bash
# Check for new updates
softwareupdate -l

# Install an update
softwareupdate -i <FULL_NAME_OF_UPDATE>
```

## Show information about a volume
```bash
diskutil info '<PATH_TO_VOLUME>'
```