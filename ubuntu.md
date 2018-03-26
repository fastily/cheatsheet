# Useful Ubuntu Commands

## Trash
```bash
# Move a file or directory to the trash
gvfs-trash <FILENAME>

# See contents of trash
gvfs-ls trash://

# Empty the Trash
gvfs-trash --empty
```

## Install a .deb
```bash
dpkg -i <PATH_TO_DEB_FILE>
apt-get install -f
```

## PPA
```bash
# Add a PPA
add-apt-repository ppa:<PPA_NAME>
apt-get update
apt-get install <PACKAGE_TO_INSTALL>

# Remove a PPA
apt-add-repository --remove ppa:<PPA_NAME>
apt-get update
```

## mdadm
```bash
# Check array status
mdadm -D /dev/<NAME_OF_ARRAY>
```

## Ubuntu Version
```bash
# Get your ubuntu version
lsb_release -r -s
```