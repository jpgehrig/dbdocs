## df Command Reference

Use `df` to determine the total space, used space, and free space in a mounted Oracle Memory Speed (OMS) file system.

### Syntax

    df mount_path

### Example

    OMS> df /oracle/omsfs_1
    Free (KB) : 10265748
    Used (KB) : 218928
    Total (KB): 10484676
    OMS>

### Usage Notes

The OMS file system mounted at `/oracle/omsfs_1` has a total available space of 10 GB. Out of this 10 GB total space, 213 MB is in use and approximately 9.8 GB is free space.

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
