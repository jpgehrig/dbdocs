Use this procedure to downgrade to Oracle Grid Infrastructure 11g Release 2 (11.2) .

1.  Delete the Oracle Grid Infrastructure 19c Management Database:

        $ dbca -silent -deleteDatabase -sourceDB -MGMTDB

2.  Use the command syntax `Grid_home``/crs/install/rootcrs.sh -downgrade` to stop the Oracle Grid Infrastructure 19c resources, and to shut down the stack. Run this command from a directory that has write permissions for the Oracle Grid Infrastructure installation user.

    You can run the downgrade script in parallel on all cluster nodes, but one.

3.  Downgrade the last node after you downgrade all other nodes:

        # /u01/app/19.0.0/grid/crs/install/rootcrs.sh -downgrade

4.  Follow these steps to remove Oracle Grid Infrastructure 19c Grid home as the active Oracle Clusterware home:

    1.  On any of the cluster member nodes where the `rootupgrade.sh` script has run successfully, log in as the Oracle Grid Infrastructure installation owner.

    2.  Use the following command to start the installer, where `/u01/app/19.0.0/grid` is the location of the new (upgraded) Grid home:

    <!-- -->

        $ cd /u01/app/19.0.0/grid/oui/bin
        $ ./runInstaller -nowait -waitforcompletion -ignoreSysPrereqs -updateNodeList
         -silent CRS=false ORACLE_HOME=/u01/app/19.0.0/grid
         "CLUSTER_NODES=node1,node2,node3" -doNotUpdateNodeList

    Add the `-cfs` option if the Grid home is a shared home.

5.  Follow these steps to set the Oracle Grid Infrastructure 11g Release 2 (11.2) Grid home as the active Oracle Clusterware home:

    1.  On any of the cluster member nodes where the `rootupgrade` script has run successfully, log in as the Oracle Grid Infrastructure installation owner.

    2.  Use the following command to start the installer, where the path you provide for the `ORACLE_HOME` is the location of the home directory from the earlier Oracle Clusterware installation.

            $ cd /u01/app/11.2.0/grid/oui/bin
            $ ./runInstaller -nowait -waitforcompletion -ignoreSysPrereqs -updateNodeList
             -silent CRS=true ORACLE_HOME=/u01/app/11.2.0/grid

        Add the `-cfs` option if the Grid home is a shared home.

6.  Start the Oracle Clusterware stack manually from the earlier release Oracle Clusterware home using the command `crsctl start crs`. For example, where the earlier release home is `/u01/app/11.2.0/grid`, use the following command on each node:

        /u01/app/11.2.0/grid/bin/crsctl start crs

**Parent topic:** [Downgrading Oracle Clusterware to an Earlier Release](downgrading-oracle-clusterware-after-an-upgrade.md)
