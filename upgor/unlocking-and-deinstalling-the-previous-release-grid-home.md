After upgrading from previous releases, if you want to deinstall the previous release Grid home, then you must first change the permission and ownership of the previous release Grid home.

1.  As the `root` user, unlock the previous release Grid home.
        # /u01/app/oracle/product/18.0.0/grid/crs/install/roothas.sh -unlock -dstcrshome previous_release_Grid_home
2.  After you change the permissions and ownership of the previous release Grid home, log in as the Oracle Grid Infrastructure installation owner (`grid`, in the preceding example), and use the `deinstall` command from the previous release Grid home `$ORACLE_HOME/deinstall` directory.
    **Caution:**

    You must use the `deinstall` command from the same release to remove Oracle software. Do not run the `deinstall` command from a later release to remove Oracle software from an earlier release. For example, do not run the `deinstall` command from the 19.0.0.0.0 Grid home to remove Oracle software from an existing 18.0.0.0.0 Grid home.

**Parent topic:** [Upgrading and Patching Oracle Restart](upgrading-and-patching-oracle-restart.md)
