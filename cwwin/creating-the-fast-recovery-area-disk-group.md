## Creating the Fast Recovery Area Disk Group

You can use ASMCA to create an Oracle ASM disk group for the fast recovery area.

1.  Navigate to the bin directory in the Grid home and start Oracle ASM Configuration Assistant (ASMCA).
    For example:
        C:\> cd C:\app\19.0.0\grid\bin
        C:\> asmca

    ASMCA opens at the Disk Groups tab.
2.  Click Disk Groups in the left panel to open the Disk Groups tab.
3.  Click Create to create a new disk group.
    The Create Disk Groups window opens.
4.  In the Create Disk Groups window, enter the following information, then click OK:
    1.  In the Disk Group Name field, enter a descriptive name for the fast recovery area disk group. For example: `FRA`.
    2.  In the Redundancy section, select the level of redundancy you want to use. For example: `Normal`.
    3.  In the Select Member Disks field, select eligible disks to be added to the fast recovery area, and click OK.
5.  When the Fast Recovery Area disk group creation is complete, click Exit and click Yes to confirm closing the ASMCA application.

**Parent topic:** [Create a Fast Recovery Area Disk Group](create-a-fast-recovery-area-disk-group.md)
