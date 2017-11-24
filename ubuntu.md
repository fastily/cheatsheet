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

## Add a PPA and install
```bash
sudo add-apt-repository ppa:<PPA_NAME> && sudo apt-get update
sudo apt-get install <PACKAGE_TO_INSTALL>
```