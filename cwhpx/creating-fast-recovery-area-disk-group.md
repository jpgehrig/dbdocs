Procedure to create the fast recovery area disk group.

1.  Go to the Oracle Grid Infrastructure home `bin` directory, and start Oracle ASM Configuration Assistant (ASMCA).
    For example:

        $ cd /u01/app/19.0.0/grid/bin
        $ ./asmca

    ASMCA opens the home window.
2.  Click Disk Groups in the left panel to open the Disk Groups tab.
3.  Click Create to create a new disk group.
    The Create Disk Groups window opens.
4.  Provide configuration information for the fast recovery area as prompted:
    In the Disk Group Name field, enter a descriptive name for the fast recovery area group. For example: FRA.

    In the Redundancy section, select the level of redundancy you want to use. For example: Normal

    In the Select Member Disks field, select eligible disks you want to add to the fast recovery area, and click OK.
5.  When the Fast Recovery Area disk group creation is complete, click Exit and click Yes to confirm closing the ASMCA application.

**Parent topic:** [Creating a Fast Recovery Area](creating-a-fast-recovery-area.md)
