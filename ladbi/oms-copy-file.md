## cp Command Reference

Use the copy command `cp` to copy files.

### Syntax

    cp src_filepath dst_filepath

### Usage Notes

You can copy the files from a POSIX mount point to an Oracle Memory Speed (OMS) mount point, an OMS mount point to a POSIX mount point, within a single OMS mount point, or between OMS mount points associated with the same SID.

You must use absolute paths for files residing in the OMS file system. The `cp` command is enabled only when the Oracle instance is down. Oracle recommends that you use SQL commands to copy files into and out of the OMS file system using the instance.

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
