## Relinking Oracle Grid Infrastructure for a Cluster Binaries

After installing Oracle Grid Infrastructure for a cluster, if you modify the Oracle Grid Infrastructure binaries, then you must relink the binaries on Oracle Linux 8 or earlier releases.

**Note:**

You do not need to relink the Oracle Clusterware and Oracle ASM binaries when you:

- Perform a fresh install of Oracle Grid Infrastructure on Oracle Linux 9 or later releases.
- Upgrade the operating system to Oracle Linux 9 or later releases.
- Apply any operating system patch to Oracle Linux 9 and later releases.

**Caution:**

Before relinking executables, you must shut down all executables that run in the Oracle home directory that you are relinking. In addition, shut down applications linked with Oracle shared libraries. If present, unmount all Oracle Automatic Storage Management Cluster File System (Oracle ACFS) file systems.

As `root` user:

    # cd Grid_home/crs/install
    # rootcrs.sh -unlock

As the Oracle Grid Infrastructure for a cluster owner:

    $ export ORACLE_HOME=Grid_home
    $ Grid_home/bin/relink all

As `root` user again:

    # cd Grid_home/rdbms/install/
    # ./rootadd_rdbms.sh
    # cd Grid_home/crs/install
    # rootcrs.sh -lock

You must relink the Oracle Clusterware and Oracle ASM binaries every time you apply an operating system patch or after you perform an operating system upgrade that does not replace the root file system.

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
