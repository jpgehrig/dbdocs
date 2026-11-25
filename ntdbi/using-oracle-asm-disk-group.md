## Using an Oracle Automatic Storage Management Disk Group

Learn how to identify disk groups and determine the available free disk space.

You can store either database or recovery files in an existing Oracle Automatic Storage Management disk group that you created during the Oracle Grid Infrastructure for a standalone server installation.

**Note:**

The Oracle Automatic Storage Management instance that manages the existing disk group runs in a different Oracle home directory.

1.  In the Services Control Panel, ensure that the `OracleASMService+ASM` service has started.

2.  Open command prompt and temporarily set the `ORACLE_SID` environment variable to specify the appropriate value for the Oracle Automatic Storage Management instance.

    For example, if the Oracle Automatic Storage Management SID, which is named `+ASM`, is located in the `asm` directory, then enter the following setting:

        DRIVE_LETTER:\>set ORACLE_SID=+ASM

3.  Connect to the Oracle Automatic Storage Management instance as the `SYS` user with the `SYSASM` privilege and start the instance if necessary:

        DRIVE_LETTER:\>sqlplus /nolog
        SQL> CONNECT SYS as SYSASM
        Enter password: SYS_password
        SQL> STARTUP

4.  Enter the following command to view the existing disk groups, their redundancy level, and the amount of free disk space in each one:

        SQL> SELECT NAME,TYPE,TOTAL_MB,FREE_MB FROM V$ASM_DISKGROUP;

5.  From the output, identify a disk group with the appropriate redundancy level and note the free space that it contains.

6.  If necessary, install, or identify the additional disk devices required to meet the storage requirements.

    **Note:**

    If you are adding devices to an existing disk group, then Oracle recommends that you use devices that have the same size and performance characteristics as the existing devices in that disk group.

**Parent topic:** [Installing Oracle Database](installing-oracle-database.md)
