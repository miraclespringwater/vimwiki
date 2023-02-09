
## Extracting .tar.gz
```
tar -xvf filename -C directory 
```

## BTRFS
* Chris Titus Guide: https://christitus.com/btrfs-guide/
### Making a filesystem
```bash
mkfs.btrfs -L mylabel /dev/partition
```


## Filesystems
### Identifying existing file systems
```bash
lsblk -f
```

## systemd mount/systemd automount
### Helpful links
* https://forum.manjaro.org/t/root-tip-how-to-systemd-mount-unit-samples/1191
* https://forum.manjaro.org/t/root-tip-how-to-use-systemd-to-mount-any-device/1185
* https://forum.endeavouros.com/t/root-mounting-any-device-using-systemd-mount-and-automount/7696
* https://man.archlinux.org/man/systemd.unit.5.en
* https://unix.stackexchange.com/questions/206315/whats-the-difference-between-usr-lib-systemd-system-and-etc-systemd-system
* https://blog.tomecek.net/post/automount-with-systemd/
### Prereqs/tips
* A .mount and .automount unit needs to be created.
* The mount unit will create the mountpoint if it does not exist.
* The automount unit will fail if the mount unit is active.
* The automount until the start the mount unit when the mountpoint is accessed (via terminal or app)
* Mount units must be named the mount point with the extension of .mount so if you use a mountpoint named /data/backup the unit file must be named data-backup.mount
* Automount units use the name of the mount unit with an extension of .automount so the automount unit for the example data-backup.mount must be named data-backup.automount.
* TIP: don't use dashes in the mountpoint unless you escape using the following:
```bash
systemd-escape -p --suffix=mount "/media/home-backup"
systemd-escape -p --suffix=automount "/media/home-backup"
```
* Get UUID of disk with the following:
```bash
lsblk -no UUID /dev/<part>
```
### Creating .mount unit
* Create unit file at /etc/systemd/system/path-to-mountpoint.mount
* Example unit:
```
[Unit]
Description=Mount build partition

[Mount]
What=/dev/disk/by-uuid/$UUID
Where=$YOUR_MOUNT_PATH
Type=ext4
Options=rw,noatime

[Install]
WantedBy=multi-user.target
```
* Use noatime option for SSD's
* Create automount unit file at same path but with .automount suffix.
* Example automount unit:
```
[Unit]
Description=Automount USB backup partition

[Automount]
Where=$YOUR_MOUNT_PATH
TimeoutIdleSec=10

[Install]
WantedBy=multi-user.target
```
* May need to reload daemon with the following:
```bash
sudo systemctl daemon-reload
```
* Start/enable the automount (or mount if not a USB/removable device) unit:
```bash
sudo systemctl enable --now <unitname>.automount
```
