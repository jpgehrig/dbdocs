Use Oracle Enterprise Manager Cloud Control or the Oracle ASM command line tool (`asmcmd`) to identify existing disk groups, and to determine if sufficient space is available in the disk group.

1.  Connect to the Oracle ASM instance and start the instance if necessary:
        $ $ORACLE_HOME/bin/asmcmd
        ASMCMD> startup
2.  Enter one of the following commands to view the existing disk groups, their redundancy level, and the amount of free disk space in each one:
        ASMCMD> lsdg

    or

        $ORACLE_HOME/bin/asmcmd -p lsdg

    The `lsdg` command lists information about mounted disk groups only.
3.  From the output, identify a disk group with the appropriate redundancy level and note the free space that it contains.
4.  If necessary, install or identify the additional disk devices required to meet the storage requirements for your installation.

**Note:**

If you are adding devices to an existing disk group, then Oracle recommends that you use devices that have the same size and performance characteristics as the existing devices in that disk group.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
