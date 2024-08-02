## Configure Settings:
```bash
sudo raspi-config
```

## Get system version information
```bash
# Kernel version
uname -a

# Everything else
cat /etc/os-release
```

## Mount FAT32 USB
```bash
sudo mount -t vfat '/dev/<PARTITION_TO_MOUNT>' '/media/<MOUNT_FOLDER>' -o uid=1000,gid=100,utf8
```

## Useful Programs
```bash
# headless jre
sudo apt -y install openjdk-11-jre-headless

# samba
sudo apt -y install samba samba-common-bin
```

## Get CPU temp
```bash
vcgencmd measure_temp
```