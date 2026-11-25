## Creating the Fast Recovery Area Disk Group

Use this procedure to create the fast recovery area disk group.

1.  Navigate to the Grid home bin directory, and start ASM Configuration Assistant (ASMCA). For example:
        DRIVE_LETTER:\> cd \app\oracle\product\19.0.0\grid\bin
        DRIVE_LETTER:\> asmca
2.  ASMCA opens at the Disk Groups tab. Click Create to create a disk group.
3.  The Create Disk Groups window opens.
    In the Disk Group Name field, enter a descriptive name for the fast recovery area group. For example: `FRA`.

    In the Redundancy section, select the level of redundancy you want to use.

    In the Select Member Disks field, select the eligible disks to be added to the fast recovery area, and click OK.
4.  The Diskgroup Creation window opens to inform you when the disk group creation is complete. Click OK.
5.  Click Exit.

**See Also:**

- [Oracle Database Backup and Recovery User's Guide](../bradv/configuring-rman-client-basic.md)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-intro.md)

**Parent topic:** [Creating a Fast Recovery Area Disk Group](creating-a-fast-recovery-area-disk-group.md)
