## Migrating from Oracle ASM Filter Driver to Oracle ASMLib for Oracle Restart

Oracle ASMFD is deprecated and Oracle ASM filtering is disabled starting with kernel version 5.14. To avail the filtering functionality, migrate from Oracle ASMFD to Oracle ASMLIB 3.1 in rolling mode.

Prerequisites

- If Oracle ASM Filter Driver (Oracle ASMFD) is installed and configured for an existing Oracle ASM installation, then you must explicitly disable Oracle ASMFD filtering before installing and configuring Oracle ASMLib.
- These steps apply to Oracle Linux 8 or later version servers that are running UEK6 or kernel version `5.4.17-2136.342.1` or later.

1.  Confirm if Oracle ASMFD is configured and running.
        # asmcmd lsdsk
        Path
        AFD:DATA1
        AFD:DATA2

    The `AFD` in the results indicate that the disks are configured using Oracle ASMFD.
2.  Apply the one-off patches for the following bugs:
    1.  37347369
    2.  37214236
    3.  37230154
    4.  37405185
3.  Shut down the Oracle Restart stack.
        # crsctl stop has
4.  Depending on your operating system, install the latest versions (3.1.x or later) of the `oracleasmlib` and `oracleasm-support` packages.
        # rpm -ihv oracleasm-support-3.1.x.rpm
        # rpm -ihv oracleasmlib-3.1.x.rpm

    **Note:**

    Oracle Unbreakable Enterprise Kernel (UEK) includes driver module, so you do not need to install `kmod-oracleasm`. For more information about installing the Oracle ASMLib packages, refer to [Installing and Configuring Oracle ASMLib v3](https://docs.oracle.com/en/operating-systems/oracle-linux/asmlib/).
5.  Run the Oracle ASM initialization script and configure Oracle ASMLib.
        # /etc/init.d/oracleasm init
        # /etc/init.d/oracleasm configure -i
6.  Scan for Oracle ASM labeled disks using the following command as `root`.
        # /etc/init.d/oracleasm scandisks
7.  List the Oracle ASMLib disks.
        # /etc/init.d/oracleasm listdisks
8.  Verify the status of the Oracle ASMLib disks.
        # /etc/init.d/oracleasm status
9.  Disable Oracle ASMFD filtering.
        # $ORACLE_HOME/bin/asmcmd afd_filter -d
10. Start the Oracle Restart stack.
        # crsctl start has
11. Confirm if Oracle ASMLib is configured and running.
        # asmcmd lsdsk
        Path
        ORCL:DATA1
        ORCL:DATA2

    The `ORCL` in the results indicate that the disks are configured using Oracle ASMLib.

**Related Topics**

- [Installing and Configuring Oracle ASMLIB Software](installing-and-configuring-oracle-asmlib-software.md)
- [Deconfiguring Oracle ASM Filter Driver](deconfiguring-oracle-asmfd.md)

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure for a Standalone Server](configuring-storage-for-oracle-grid-infrastructure-for-a-standalone-server.md)
