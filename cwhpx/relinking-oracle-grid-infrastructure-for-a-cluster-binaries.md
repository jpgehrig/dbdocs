After installing Oracle Grid Infrastructure for a cluster (Oracle Clusterware and Oracle ASM configured for a cluster), if you need to modify the binaries, then use the following procedure, where `Grid_home` is the Oracle Grid Infrastructure for a cluster home:

**Caution:**

Before relinking executables, you must shut down all executables that run in the Oracle home directory that you are relinking. In addition, shut down applications linked with Oracle shared libraries.

As `root`:

    # cd Grid_home/crs/install
    # rootcrs.sh -unlock

As the Oracle Grid Infrastructure for a cluster owner:

    $ export ORACLE_HOME=Grid_home
    $ Grid_home/bin/relink

As root again:

    # cd Grid_home/rdbms/install/
    # ./rootadd_rdbms.sh
    # cd Grid_home/crs/install
    # rootcrs.sh -lock

You must relink the Oracle Clusterware and Oracle ASM binaries every time you apply an operating system patch or after you perform an operating system upgrade that does not replace the root file system. For an operating system upgrade that results in a new root file system, you must remove the node from the cluster and add it back into the cluster.

For upgrades from previous releases, if you want to deinstall the prior release Grid home, then you must first unlock the prior release Grid home. Unlock the previous release Grid home by running the command `rootcrs.sh -unlock` from the previous release home. After the script has completed, you can run the `deinstall` command.

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
