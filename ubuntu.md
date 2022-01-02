## trash-cli
```bash
# Move a file or directory to the trash
trash-put '<FILENAME>'

# View contents of trash
trash-list

# Empty the Trash
trash-empty
```

## apt and dpkg
```bash
# Install a .deb
dpkg -i '<PATH_TO_DEB_FILE>'
apt-get install -f

# Add a PPA
add-apt-repository 'ppa:<PPA_NAME>'
apt-get update
apt-get install '<PACKAGE_TO_INSTALL>'

# Remove a PPA
apt-add-repository --remove 'ppa:<PPA_NAME>'
apt-get update

# Remove package
apt-get remove '<PACKAGE_NAME>'

# Remove package and delete all of its config files
apt-get purge '<PACKAGE_NAME>'
```

## mdadm
```bash
# show all raid statuses
cat /proc/mdstat

# Check array status
mdadm -D '/dev/<NAME_OF_ARRAY>'

# Remove/Delete raid array
sudo umount -l '/dev/<NAME_OF_ARRAY>' # lazily unmount
sudo mdadm --stop '/dev/<NAME_OF_ARRAY>'
sudo mdadm --zero-superblock '/dev/<ID_OF_EACH_HDD>'
sudo mdadm --remove '/dev/<NAME_OF_ARRAY>'
sudo wipefs -a '/dev/<ID_OF_EACH_HDD>' # stop kernel from re-adding

# don't forget to remove any entries in /etc/fstab if applicable
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

## lsusb
```bash
# list all usb device ids (vendor:product id)
lsusb

# dump usb heierarchy as a tree
lsusb -t
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

# view detailed smart information for a disk (ATA disks)
sudo smartctl -a -d ata '/dev/<DEVICE_ID>'

# view detailed smart information for a disk (SCSI to ATA, typically for external USB hdd's)
sudo smartctl -a -d sat '/dev/<DEVICE_ID>'

# get lots of information about a disk
sudo smartctl -x '/dev/<DEVICE_ID>'

# temporarily set usb quirks flag for a device - use UAS, but still allow smartctl (reset on reboot)
cat "/sys/module/usb_storage/parameters/quirks" # verify empty first
printf "<VENDOR_ID>":"<PRODUCT_ID>":"u\n" | sudo tee "/sys/module/usb_storage/parameters/quirks" # plug in device and try again
```

## zfs
```bash
# create raidz1 pool
sudo zpool create '<SOME_NAME_HERE>' raidz '/dev/<DEVICE_ID1>' '/dev/<DEVICE_ID2>' '/dev/<DEVICE_ID3>'

# create raid0 pool
sudo zpool create '<SOME_NAME_HERE>' '/dev/<DEVICE_ID1>' '/dev/<DEVICE_ID2>' '/dev/<DEVICE_ID3>'

# check zpool statues
zpool status

# move zpool mount location
sudo zfs set mountpoint='<PATH_TO_NEW_MOUNT_POINT>' '<NAME_OF_ZPOOL>'

# destroy a zpool
sudo zpool destroy '<NAME_OF_ZPOOL>'
sudo wipefs -a '/dev/<ID_OF_EACH_HDD>' # stop kernel from re-adding

# list zpools which can be imported
sudo zpool import

# import zpool
sudo zpool import '<NAME_OF_ZPOOL>'

# create snapshot.  nb: datasets cannot be destroyed if snapshots of it exist.
sudo zfs snapshot '<FILESYSTEM_NAME>@<SNAPSHOT_NAME>'

# list snapshots
zfs list -t snapshot

# initiate a scrub
zpool scrub '<NAME_OF_POOL>'

# kill a running scrub
zpool scrub -s '<NAME_OF_POOL>'
```


## Useful Programs
```bash
# SMART monitoring and GUI
sudo apt -y install smartmontools gsmartcontrol

# GUI Partioner
sudo apt -y install gparted

# screen recorder
sudo apt -y install kazam

# trash management cli that actually works
sudo apt -y install trash-cli

# zfs
sudo apt -y install zfsutils-linux
```

## sed
```bash
# grab all lines in a file matching REGEX_LINE_TO_MATCH and for each line replace TEXT_TO_REPLACE_REGEX w/ REPLACEMENT_TEXT
sudo sed -i -e '/<REGEX_LINE_TO_MATCH>/s/<TEXT_TO_REPLACE_REGEX>/<REPLACEMENT_TEXT>/' '<FILE_TO_EDIT>'

# enables extended regex: capturing groups '(foo)' and quantifiers '?'
sudo sed -i -E 's/<REGEX_TEXT_TO_REPLACE>/<REPLACEMENT_TEXT>/'
```

## hostnamectl
```bash
# change this computer's (static, pretty, transient) hostname
hostnamectl set-hostname '<NEW_HOSTNAME>'
```

## udisksctl
```bash
# power off an external hard drive (do this after unmounting)
sudo udisksctl power-off -b '/dev/<DEVICE_ID>'
```