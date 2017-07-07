## macOS shortcuts

## Hide a file/folder
```bash
chflags hidden FILENAME_HERE
```

```bash
chflags nohidden FILENAME_HERE
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