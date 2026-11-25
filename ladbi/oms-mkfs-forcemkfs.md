## mkfs and forcemkfs Command Reference

Use `mkfs` and `forcemkfs` to format the OMS uber file placed in a PMEM DAX mount point.

### Syntax

    mkfs PMEM_device blksz
    forcemkfs PMEM_device blksz

In this example, PMEM_device is the uber file.

Both `mkfs` and `forcemks` accept an optional block size blksz argument. Currently, 4 KB is the only supported block size. `mkfs` and `forcemkfs` will not format an uber file that is mounted as an OMS file system.

### Usage Notes

The uber file size must be an exact multiple of 2 MB. `mkfs` checks if the uber file includes a preexisting OMS file system. If `mkfs` finds a preexisting OMS file system, `mkfs` will print an error.

`forcemkfs` does not check for a preexisting OMS file system in the uber file and proceeds with laying out a new OMS file system in the uber file.

**Caution:**

After you run `forcemkfs`, the data in the uber file cannot be restored.

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
