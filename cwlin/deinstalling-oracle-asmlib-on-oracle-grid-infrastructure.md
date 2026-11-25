## Deinstalling Oracle ASMLIB On Oracle Grid Infrastructure

If Oracle ASM library driver (Oracle ASMLIB) is installed but you do not use it for device path persistence, then deinstall Oracle ASMLIB.

1.  Log in as `root`.
2.  Stop Oracle ASM and any running database instance on the node:
        # srvctl stop instance -d db_unique_name-node node_name
        # srvctl stop asm -node node_name

    To stop the last Oracle Flex ASM instance on the node, stop the Oracle Clusterware stack:
        # Grid_home/bin/crsctl stop crs
3.  Unload ASMLIB without restarting the system:
        # /usr/sbin/oracleasm exit
4.  Stop Oracle ASMLIB:
        # /usr/sbin/oracleasm configure -d
5.  Remove the `oracleasm` library and tools RPMs:
        # rpm -e oracleasm-support

        # rpm -e oracleasmlib
6.  Check if any `oracleasm` RPMs are remaining:
        # rpm -qa| grep oracleasm
7.  If any `oracleasm` configuration files are remaining, remove them:
        # rpm -qa| grep oracleasm | xargs rpm -e

    Oracle ASMLIB and associated RPMs are now removed.

**Parent topic:** [Configuring Storage Device Path Persistence Using Oracle ASMLIB](configuring-storage-device-path-persistence-using-oracle-asmlib.md)
