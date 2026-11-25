## Create an Uber File for Oracle Memory Speed

After mounting the DAX file system, create an uber file for the Oracle Memory Speed (OMS) file system.

An uber file is similar to a volume in a traditional kernel-based file system. The uber file stores all the metadata and data for OMS.

1.  Use `fallocate` to create uber files in the DAX-mounted file systems.
        # fallocate -l 800G /mnt/pmem0/omsuberfile.$ORACLE_SID
        # fallocate -l 800G /mnt/pmem1/omsuberfile.$ORACLE_SID

    In this example, `fallocate` creates two 800 GiB files in each of the DAX-mounted file systems. Ensure that the size of the file is an exact multiple of 2 MiB. This aligns the file extents on 2 MiB boundaries and enables access through HugePages virtual memory mappings.
2.  Change the ownership of the OMS uber file to the software owner user (`oracle`) and the Oracle Inventory group (`oinstall`), with read/write permissions.
        # chown oracle:oinstall /mnt/pmem0/omsuberfile.$ORACLE_SID
        # chmod 644 /mnt/pmem0/omsuberfile.$ORACLE_SID
3.  Use the `xfs_bmap` command to ensure that the extents are correctly aligned on 2 MiB boundaries.
        # xfs_bmap /mnt/pmem0/omsuberfile.$ORACLE_SID
        /mnt/pmem0/omsuberfile.test:
                     0: [0..4095]: 1765978112..1765982207
                     1: [4096..16773119]: 1765982208..1782751231
                     2: [16773120..20971519]: 1782751232..1786949631

    The output from the `xfs_bmap` command is in the following format:

        Extent Num:[Start Offset..End Offset]:Start block..End Block

    Offset and blocks are in units of 512 bytes. The file `/mnt/pmem0/omsuberfile.$ORACLE_SID` has 3 contiguous extents numbered 0-2.

Table 8-1 Size and Alignment of Extents in the Uber File (in Bytes)

| Extent | Start Offset | Start Offset Mod 2 M | Start Block | Start Block Mod 2 M | Number of 2 MiB Blocks |
|:-------|:-------------|:---------------------|:------------|:--------------------|:-----------------------|
| 0      | 0H           | 0H                   | D285600000H | 0H                  | 1H                     |
| 1      | 20000H       | 0H                   | D285800000H | 0H                  | FFEH                   |
| 2      | 0x1FFF00000H | 0H                   | D485400000H | 0H                  | 401H                   |

This table shows the Start Offset and Start Block converted into bytes and represented in hexadecimals. The Starts Offsets are all aligned on 2 MiB boundaries (Start Offset Mod 2 MiB is 0). The Start Block of each extent lies on a 2 MiB boundary (Start Block Mod 2 M is 0). Similarly, the size of the extents are exact multiples of 2 MiB.

The OMS uber file has a one-to-one relationship with an Oracle instance. You formalize the association by ending the uber file name with the Oracle instance identifier (SID). In the preceding example, the SID is `test`. Two uber files are `/mnt/pmem0/omsuberfile.test` and `/mnt/pmem1/omsuberfile.test`.

**Related Topics**

- [Verifying HugePages Behavior in XFS Files](hugepages-in-xfs-files.md)

**Parent topic:** [Setting-Up Hardware and Operating System Components for OMS](setting-up-hardware-oms.md)
