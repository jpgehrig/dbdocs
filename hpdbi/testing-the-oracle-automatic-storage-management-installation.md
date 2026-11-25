After installing Oracle Grid Infrastructure for a single instance, use the ASMCMD command-line utility to test the Oracle ASM installation.

1.  Open a shell window, and temporarily set the ORACLE_SID and ORACLE_HOME environment variables to specify the appropriate values for the Oracle ASM instance to use.
    For example, if the Oracle ASM SID is named +ASM and the Oracle home is located in the grid subdirectory of the ORACLE_BASE directory, then enter the following commands to create the required settings:

    Bourne, Bash or Korn shell:

        $ ORACLE_SID=+ASM
        $ export ORACLE_SID
        $ ORACLE_HOME=/u01/app/oracle/product/19.0.0/grid
        $ export ORACLE_HOME

    C shell:

        % setenv ORACLE_SID +ASM
        % setenv ORACLE_HOME /u01/app/oracle/product/19.0.0/grid
2.  Use ASMCMD to list the disk groups for the Oracle ASM instance:
        $ORACLE_HOME/bin/asmcmd lsdg

    If the Oracle ASM instance is running, then ASMCMD connects by default as the SYS user with SYSASM privileges, and is available.
3.  If the Oracle ASM instance is not running, then start the Oracle ASM instance using the following command:
        $ORACLE_HOME/bin/srvctl start asm

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-asm-asmcmd.md)

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](installing-and-configuring-oracle-grid-infrastructure-for-a-standalone-server.md)
