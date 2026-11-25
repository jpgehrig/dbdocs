## mount, unmount and lsmount Command Reference

Use `mount`, `umount` and, `lsmount` to manage and query the Oracle Memory Speed file system mount points.

### Syntax

    mount Device mount_path
    umount mount_path
    lsmount

### Usage Notes

`mount` creates a mount point for the uber file referred to as Device in the command syntax. `mount` does not allow a previously mounted uber file to be mounted again. `mount` supports a maximum of two mount points. The directory for the mount point must exist in the underlying POSIX file system and should not have write permissions.

`umount` unmounts a previously mounted OMS file system.

`lsmount` lists all the mount points.

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
