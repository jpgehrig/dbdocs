## Modifying Oracle Clusterware Binaries After Installation

After installation, if you need to modify the Oracle Clusterware configuration, then you must unlock the Grid home. Review this information about unlocking the Grid home.

For example, if you want to apply a one-off patch, or if you want to modify an Oracle Exadata configuration to run IPC traffic over RDS on the interconnect instead of using the default UDP, then you must unlock the Grid home.

**Caution:**

Before relinking executables, you must shut down all executables that run in the Oracle home directory that you are relinking. In addition, shut down applications linked with Oracle shared libraries.

Unlock the home using the following procedure:

1.  Go to the `/u01/app/19.0.0/grid/crs/install` directory, and unlock the Grid home using the command `rootcrs.sh -unlock`:

        # cd /u01/app/19.0.0/grid/crs/install
        # ./rootcrs.sh -unlock

2.  Change user to the Oracle Grid Infrastructure software owner, and relink binaries using the command syntax `make -f /u01/app/19.0.0/grid/rdbms/lib/ins_rdbms.mk ``target`, where target is the binaries that you want to relink. For example, where you are updating the interconnect protocol from UDP to IPC, enter the following command:

        # su grid
        $ make -f /u01/app/19.0.0/grid/rdbms/lib/ins_rdbms.mk ipc_rds ioracle

    **Note:**

    To relink binaries, you can also change to the grid installation owner and run the command `/u01/app/19.0.0/grid/bin/relink`.

3.  Relock the Grid home and restart the cluster as follows:

        # ./rootcrs.sh -lock
        # crsctl start crs

    Repeat steps 1 through 3 on each cluster member node.

**Note:**

Do not delete directories in the Grid home. For example, do not delete the directory Grid_home/OPatch. If you delete the directory, then the Grid infrastructure installation owner cannot use OPatch to patch the Grid home, and OPatch displays the error message "`checkdir error: cannot create `Grid_home`/OPatch`".

**Parent topic:** [Oracle Grid Infrastructure Postinstallation Tasks](oracle-grid-infrastructure-postinstallation-tasks.md)
