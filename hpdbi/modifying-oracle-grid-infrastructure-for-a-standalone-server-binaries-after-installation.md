Relink the Oracle Restart and Oracle ASM binaries every time you apply an operating system patch or after an operating system upgrade.

**Caution:**

Before relinking executables, you must shut down all executables that run in the Oracle home directory that you are relinking. In addition, shut down applications linked with Oracle shared libraries.

1.  Log in as `root` and unlock the grid home:
        # cd Grid_home/crs/install
        # roothas.sh -unlock
2.  Log in as the `grid `user and relink the binaries:
        $ export ORACLE_HOME=Grid_home
        $ Grid_home/bin/relink
3.  Log in as `root` again and perform the following steps:
        # cd Grid_home/rdbms/install/
        # ./rootadd_rdbms.sh
        # cd Grid_home/crs/install
        # roothas.sh -lock

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](installing-and-configuring-oracle-grid-infrastructure-for-a-standalone-server.md)
