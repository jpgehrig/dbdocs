## Downgrading to Oracle Grid Infrastructure 11g Release 2 (11.2)

Use this procedure to downgrade to Oracle Grid Infrastructure 11g Release 2 (11.2).

1.  Delete the Oracle Grid Infrastructure 19c Management Database:
        dbca -silent -deleteDatabase -sourceDB -MGMTDB
2.  As an Administrator user, use the command syntax `Grid_home``\crs\install\rootcrs.bat -downgrade` to stop the Oracle Grid Infrastructure 19c resources, and shut down the Oracle Grid Infrastructure stack.
    Run this command from a directory that has write permissions for the Oracle Grid Infrastructure installation user.

    You can run the downgrade script in parallel on all but one of the cluster nodes. You must downgrade the last node after you downgrade all other nodes.
3.  Remove Oracle Grid Infrastructure 19c Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the upgrade to Oracle Grid Infrastructure 12c has completed successfully, log in as the Oracle Grid Infrastructure installation owner.
    2.  Use the following command to start the installer, where `C:\app\19.0.0\grid` is the location of the new (upgraded) Grid home:
            C:\>cd C:\app\19.0.0\grid\oui\bin
            setup.exe -nowait -updateNodeList -silent CRS=false
            ORACLE_HOME=C:\app\19.0.0\grid
            "CLUSTER_NODES=node1,node2,node3" LOCAL_NODE=local_node_running_the_command
            -doNotUpdateNodeList

        Add the option `-cfs` if the Grid home is a shared home.
4.  Set the Oracle Grid Infrastructure 11g Release 2 (11.2) Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the upgrade to Oracle Grid Infrastructure 12c has completed successfully, log in as the Oracle Grid Infrastructure installation owner.
    2.  Use the following command to start the installer, where the path you provide for `ORACLE_HOME` is the location of the home directory from the earlier Oracle Clusterware installation.
            C:\>cd C:\app\11.2.0\grid\oui\bin
            setup.exe -nowait -updateNodeList -silent CRS=true
            ORACLE_HOME=C:\app\11.2.0\grid -doNotUpdateNodeList

        Add the option `-cfs` if the Grid home is a shared home.
5.  Manually start the Oracle Clusterware stack for Oracle Grid Infrastructure 11g Release 2 (11.2).
    On each node, start Oracle Clusterware from the earlier release Oracle Clusterware home using the command `crsctl start crs`. For example. if the earlier release home is `C:\app\11.2.0\grid`, use the following command on each node:

        C:\>cd C:\app\11.2.0\grid\bin> crsctl start crs

**Parent topic:** [Downgrading Oracle Clusterware to an Earlier Release](downgrading-oracle-clusterware-after-an-upgrade.md)
