# Disk utility

## List all volumes

```bash
diskutil list
```

Disk identifiers follow the format `disk_s_`, where the underscores are replaced with identifying numbers.

## Get info

```bash
diskutil info disk1
```

## Unmounting and ejecting

```bash
diskutil umount disk1s2
```

Unmounting is just like ejecting a volume from Finder, but it can be done to internal disks.

```bash
diskutil unmountDisk disk1
```

The `unmountDisk` verb is similar to `umount`, but it unmounts an entire disk instead of one volume. Disks are specified with their mount point, as seen above. You can’t unmount your boot disk or volume, and you’ll get an error if you try to unmount a disk or drive that’s currently in use.

```bash
diskutil eject disk4
```

The `eject` verb is a lot like unmounting a drive, but only for removable disks. Removable disks are things like USB hard drives and flash drives. If it connects through an interface on the outside of your computer, it qualifies as a removable drive. Once a drive is ejected, it won’t appear in Finder or `diskutil list` until it’s physically unplugged and plugged in to its interface again.

```bash
diskutil mount disk1s2
```

The `mount` verb is the inverse of the umount verb. It mounts volumes on internal disks manually. Only unmounted volumes can be mounted, obviously. To mount all volumes on a disk, use `diskutil mountDisk disk1`, for example.

## Fixing problems with `diskutil`

```bash
diskutil verifyVolume disk1s2
```

The `verifyVolume` verb will run a verification pass on a specific volume. Verification involves checking the contents of the disk against the expected values. If any mismatches are found, the disk will be identified as in need of repair.

```bash
diskutil repairVolume disk1s2
```

If it turns out that your volume needs to be repaired after you’ve verified it, you can run the repairVolume verb. This will run a repair pass on the volume and attempt to fix any problems found in the verification process.

## Format and Erase Drives

```bash
diskutil eraseDisk JHFS+ "NewDiskName" GPT disk2
```

`GPT` = GUID partition map.

The eraseDisk verb handles reformatting disks, which erases all data and volumes on a single disk. The verb takes as inputs the format, new disk name and disk identifier, in that order. This example will erase `disk2` and reformat it as **journaled HFS+**. The new disk will have one volume named `NewDiskName`.

## Encrypt the Drive

Note: this cannot be used on macOS BigSur and newer.

```bash
diskutil cs convert disk2s2 -passphrase
```

## Reformat

```bash
diskutil reformat disk4s2
```

The `reformat` verb will erase a single volume on the disk while keeping the same name and format. It rewrites the same file system that the volume started with, resetting the volume to a blank state.

## Partition Drives

```bash
diskutil partitionDisk
```

The `partitionDisk` verb runs a command-line version of Disk Utility, allowing you to create multiple partitions on a single disk. It’s a little complicated, but it follows this format for its arguments:

```bash
diskutil partitionDisk MountPoint [numberOfPartitions] [APM|MBR|GPT] [part1Format part1Name part1Size part2Format part2Name part2Size part3Format part3Name part3Size ...]
```

Partition sizes can be specified in gigabytes with the G suffix (2 G) or terabytes with the T suffix (2 T). My favorite way to specify partition sizes, however, is with percentages (25%, for example). The size of the final partition can be specified with “R” to indicate that it should take up the remainder of the disk.

For example, the following command will create three partitions:

```bash
diskutil partitionDisk disk4 3 GPT JHFS+ Volume1 25% APFS Volume2 25% ExFAT Volume3 R
```

They’ll be formatted with JHFS+, APFS and ExFAT, and named Volume1, Volume2 and Volume3 respectively. Volume1 and Volume2 will each take up 25 percent of the disk, and Volume3 will occupy the remainder. It will also use the GUID Partition Table (GPT) which is one of the more flexible partition table options.

## List all volumes under APFS

```bash
diskutil apfs list
```

---

#macOS #Bash #CommandLine