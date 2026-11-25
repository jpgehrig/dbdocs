## Changing the Oracle Grid Infrastructure Base Path

After installing Oracle Grid Infrastructure for a cluster (Oracle Clusterware and Oracle ASM configured for a cluster), you can change the Grid base path, if required.

This procedure applies to Oracle Grid Infrastructure 19c Release Update (19.21) and later releases.

**Note:**

Before changing the Grid base, you must shut down all executable that run in the Grid base directory that you are relinking. In addition, shut down applications linked with Oracle shared libraries.

1.  As the `root` user, create a new Oracle base directory and change the owner and group for the directory and files in the new Grid base.
        # mkdir -p /u02/app/grid
        # chown -R grid:oinstall /u02/app/grid
2.  Stop the Oracle Clusterware stack and TFA on all cluster nodes.
        # $ORACLE_HOME/bin/crsctl stop crs
        # tfactl stop
3.  Copy the Oracle Grid Infrastructure files from the old Grid base location to the new Grid base location. For example, where the old Grid base is `/u01/app/grid` and the new Grid base is `/u02/app/grid`.
        # cp -pR /u01/app/grid /u02/app/grid
4.  Create a backup of the old Oracle base to ensure new files are not created.
        # cp /u01/app/grid /u01/app/grid.old
5.  Edit the `crsconfig_params` file using a text editor and update the ORACLE_BASE parameter to the new Oracle base on all cluster nodes.
        ORACLE_BASE=/u02/app/grid
6.  Edit the `orabasetab` file using a text editor and update the ORACLE_BASE parameter in to the new Oracle base on all cluster nodes.
        /u01/app/19.0.0/grid:/u02/app/grid:OraGI19Home1:N:
7.  Edit the `/etc/oracle/olr.loc` file using a text editor and update the `olrconfig_loc` parameter with the new `ORACLE_BASE` path.
        olrconfig_loc=/u02/app/grid/crsdata/$HOSTNAME/olr/$HOSTNAME_19.olr
8.  Restore Oracle Grid Infrastructure home file permissions on all cluster nodes.
        # /u01/app/19.0.0/grid/crs/install/rootcrs.sh -init
9.  Move AHF data directory to the new Oracle base.
        # ahfctl movedatadir /u02/app/grid
10. Start the Oracle Clusterware stack on all cluster nodes.
        # $ORACLE_HOME/bin/crsctl start crs
11. Delete the old Oracle base directory.
        # mv /u01/app/grid /u01/app/grid.old
12. Update the new Oracle base location in the `Grid_home``/inventory/ContentsXML/oraclehomeproperties.xml` and `Grid_home``/network/admin/sqlnet.ora` files.
13. Confirm if any logs or traces are created in the old Oracle base after this change.
        # diff /u02/app/grid/diag/crs/node_name/crs/trace/ /u01/app/grid.old/diag/crs/node_name/crs/trace/

**Parent topic:** [Applying Patches to Oracle Grid Infrastructure](applying-patches-to-oracle-asm.md)
