## Deconfiguring Oracle ASM Filter Driver

If Oracle ASM Filter Driver (Oracle ASMFD) is installed but you do not use it for device path persistence, then deconfigure Oracle ASMFD.

1.  Log in as `root`.
2.  Set the environment variable `$ORACLE_BASE` to a temporary location.
    `# export ORACLE_BASE=/tmp`
3.  Shut down the Oracle Restart stack.
        # crsctl stop has
4.  Stop Oracle ACFS kernel modules.
        # $ORACLE_HOME/bin/acfsload stop
5.  Deconfigure Oracle ASMFD filtering.
        # $ORACLE_HOME/bin/asmcmd afd_deconfigure
6.  Start Oracle ACFS kernel modules.
        # $ORACLE_HOME/bin/acfsload start

    **Note:**

    This step is required even if you do not use Oracle ACFS.
7.  Start the Oracle Restart stack.
        # crsctl start has

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure for a Standalone Server](configuring-storage-for-oracle-grid-infrastructure-for-a-standalone-server.md)
