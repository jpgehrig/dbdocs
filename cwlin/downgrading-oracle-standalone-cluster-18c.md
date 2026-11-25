## Downgrading Oracle Standalone Cluster to 18c

Use this procedure to downgrade Oracle Standalone Cluster to Oracle Grid Infrastructure 18c after a successful upgrade.

1.  As `grid` user, delete the Oracle Grid Infrastructure 19c Management Database:
        $ $ORACLE_HOME/bin/dbca -silent -deleteDatabase -sourceDB -MGMTDB
2.  As `root` user, use the command syntax `rootcrs.sh -downgrade` from 19c Grid home to downgrade Oracle Grid Infrastructure on all nodes, in any sequence. For example:
        # $ORACLE_HOME/crs/install/rootcrs.sh -downgrade

    Run this command from a directory that has write permissions for the Oracle Grid Infrastructure installation user. You can run the downgrade script in parallel on all cluster nodes, but one.
3.  As `root` user, downgrade the last node after you downgrade all other nodes:
        # $ORACLE_HOME/crs/install/rootcrs.sh -downgrade
4.  As `grid` user, remove Oracle Grid Infrastructure 19c Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the `rootupgrade.sh` script has run successfully, log in as the Oracle Grid Infrastructure installation owner.

    2.  Use the following command to start the installer, where `/u01/app/19.0.0/grid` is the location of the new (upgraded) Grid home:

            $ cd $ORACLE_HOME/oui/bin
            ./runInstaller -nowait -waitforcompletion -ignoreSysPrereqs -updateNodeList -silent CRS=false ORACLE_HOME=/u01/app/19.0.0/grid "CLUSTER_NODES=node1,node2,node3" -doNotUpdateNodeList

        Add the flag `-cfs` if the Grid home is a shared home.
5.  As `grid` user, set Oracle Grid Infrastructure 18c Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the `rootupgrade` script has run successfully, log in as the Oracle Grid Infrastructure installation owner.

    2.  Use the following command to start the installer, where the path you provide for `ORACLE_HOME` is the location of the home directory from the earlier Oracle Clusterware installation.

            $ cd $ORACLE_HOME/oui/bin
            $ ./runInstaller -nowait -waitforcompletion -ignoreSysPrereqs -updateNodeList -silent CRS=true ORACLE_HOME=/u01/app/18.0.0/grid "CLUSTER_NODES=node1,node2,node3"
6.  As `root` user, start the 18c Oracle Clusterware stack on all nodes.
        # crsctl start crs
7.  As `grid` user, from any Oracle Grid Infrastructure 18c node, remove the MGMTDB resource as follows:
        $ $ORACLE_HOME/bin/srvctl remove mgmtdb -f
8.  As `grid` user, run DBCA in the silent mode from the 18c Grid home and create the Management Database container database (CDB) as follows:
        $ $ORACLE_HOME/bin/dbca -silent -createDatabase -createAsContainerDatabase true
        -templateName MGMTSeed_Database.dbc -sid -MGMTDB -gdbName _mgmtdb
        -storageType ASM -diskGroupName ASM_DG_NAME
        -datafileJarLocation /u01/app/18.0.0/grid/assistants/dbca/templates
        -characterset AL32UTF8 -autoGeneratePasswords -skipUserTemplateCheck
9.  Configure the Management Database by running the Configuration Assistant from the location `$ORACLE_HOME/bin/mgmtca —local`.
10. As `grid` user, run the `post_gimr_ugdg.pl` script from 19c Grid home:
        $ $ORACLE_HOME/crs/install/post_gimr_ugdg.pl -downgrade -clusterType SC -destHome /u01/app/19.0.0/grid
        -lowerVersion 18.0.0.0.0 -oraBase /u01/app/grid2

    Where:

    `SC` is the type of the cluster as Oracle Standalone Cluster. The value for `-clusterType` can be SC for Oracle Standalone Cluster, DSC for Oracle Domain Services Cluster, or MC for Oracle Member Cluster.

    `/u01/app/19.0.0/grid` is the Oracle home for Oracle Grid Infrastructure 19c.

    `18.0.0.0.0` is the version of Oracle Grid Infrastructure to which you are downgrading.

    `/u01/app/grid2` is the Oracle base for Oracle Grid Infrastructure 19c

**Parent topic:** [Downgrading Oracle Clusterware to 18c](downgrading-oracle-clusterware-to-18c.md)
