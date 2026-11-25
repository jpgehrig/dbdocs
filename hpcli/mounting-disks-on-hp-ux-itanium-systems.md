On most HP-UX systems, the disk mounts automatically when you insert it into the disk drive. If the disk does not mount automatically, then follow these steps to mount it.

1.  If necessary, switch the user to `root`:
        $ sudo - root
2.  If necessary, unmount the currently mounted disc, then remove it from the drive:
        # /usr/sbin/umount /SD_DVD

    In this example, `/SD_DVD` is the mount point directory for the disc drive.
3.  Insert the appropriate disc into the disc drive to mount it:
        # /usr/sbin/mount -F cdfs -o rr /dev/dsk/cxtydz /SD_DVD

    In this example, `/SD_DVD` is the disc mount point directory and `/dev/dsk/cxtydz` is the device name for the disc device, for example `/dev/dsk/c0t2d0`.
4.  If Oracle Universal Installer displays the Disk Location dialog box, enter the disc mount point directory path, for example:
        /SD_DVD

**Parent topic:** [Copying the Software to the Hard Disk](copying-the-software-to-the-hard-disk.md)
