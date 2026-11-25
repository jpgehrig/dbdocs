## Deinstalling Oracle ASMLIB On Oracle Database

If Oracle ASM library driver (Oracle ASMLIB) is installed but you do not use it for device path persistence, then deinstall Oracle ASMLIB:

1.  Log in as `root`.
2.  Stop Oracle ASM and any running database instance:
        # srvctl stop database

        # srvctl stop asm
3.  Stop the Oracle Restart stack:
        # cd Grid_home/bin

        # crsctl stop has

    Where, Grid_home is the Oracle Grid Infrastructure home directory path.
4.  Unload Oracle ASMLIB without restarting the system.
        # /usr/sbin/oracleasm exit
5.  Stop Oracle ASMLIB:
        # /usr/sbin/oracleasm configure -d
6.  Remove the `oracleasm` library and tools RPMs:
        # rpm -e oracleasm-support

        # rpm -e oracleasmlib
7.  Check if any `oracleasm` RPMs are remaining:
        # rpm -qa| grep oracleasm
8.  If any `oracleasm` configuration files are remaining, remove them:
        # rpm -qa| grep oracleasm | xargs rpm -e

        Oracle ASMLIB and associated RPMs are now removed.

Start the Oracle Restart stack.

**Parent topic:** [Configuring Storage Device Path Persistence Using Oracle ASMLIB](configuring-storage-device-path-persistence-using-oracle-asmlib.md)
