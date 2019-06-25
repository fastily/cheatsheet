# Useful Ubuntu Commands

## Trash
### < 18.04
```bash
# Move a file or directory to the trash
gvfs-trash <FILENAME>

# See contents of trash
gvfs-ls trash://

# Empty the Trash
gvfs-trash --empty
```
### >= 18.04
```bash
# move file/directory to trash
gio trash <FILENAME>

# empty the trash
gio trash --empty
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

# Get version information about this debian distro
lsb_release -a
```

## lsblk
```bash
# list out all block devices
lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT

```

## smart
```bash
# enable smart on a drive
sudo smartctl -s on '/dev/<DEVICE_ID>'

# estimate how long it will take to run a test
sudo smartctl -c '/dev/<DEVICE_ID>'

# run a smart test
sudo smartctl -t short '/dev/<DEVICE_ID>'

# view drive's test stats
sudo smartctl -l selftest '/dev/<DEVICE_ID>'

# view detailed smart information for a SATA drive
sudo smartctl -a -d ata '/dev/<DEVICE_ID>'
```

## Useful Programs
```bash
# SMART monitoring and GUI
sudo apt -y install smartmontools gsmartcontrol

# GUI Partioner
sudo apt -y install gparted

# screen recorder
sudo apt -y install kazam

# zfs
sudo apt -y install zfsutils-linux
```