On most Oracle Solaris systems, the disk mounts automatically when you insert it into the disk drive. If the disk does not mount automatically, then follow these steps to mount it.

1.  If necessary, switch the user to `root` and eject the currently mounted disk, then remove it from the drive:
        $ sudo sh
        password:
        # eject
2.  Insert the appropriate installation media into the disk drive.
3.  Verify if the disk is mounted automatically:
        # ls /dvd/dvd0

    If this command fails to display the contents of the installation media, then enter a command similar to the following to mount it:

        # /usr/sbin/mount -r -F hsfs /dev/dsk/cxtydzs2 /dvd

    In this example, `/dvd` is the disc mount point directory and `/dev/dsk/cxtydzs2` is the device name for the disc device.

**Parent topic:** [Copying the Software to the Hard Disk](copying-the-software-to-the-hard-disk.md)
