# Useful macOS Commands
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

## Recursively delete music metadata files
```bash
find . -name '*.nfo' -type f -delete
find . -name '*.m3u' -type f -delete
find . -name '*.m3u8' -type f -delete
```