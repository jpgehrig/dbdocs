## Testing the Oracle Automatic Storage Management Installation

After installing Oracle Grid Infrastructure for a single instance, use the ASMCMD command-line utility to test the Oracle ASM installation.

To test the Oracle Automatic Storage Management installation:

1.  Use SQL\*Plus to connect to the Oracle Automatic Storage Management instance as the `SYS `user with `SYSASM` privilege and start the instance if necessary:
        DRIVE_LETTER:\>sqlplus /nolog
        SQL> CONNECT SYS as SYSASM
        Enter password: SYS_password
        SQL> STARTUP
2.  Enter the following command to view the existing disk groups, their redundancy level, and the amount of free disk space in each one:
        SQL> SELECT NAME,TYPE,TOTAL_MB,FREE_MB FROM V$ASM_DISKGROUP;

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-intro.md)

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](install-configure-oracle-grid-infrastructure-standalone-server.md)
