Use this procedure to downgrade Oracle Member Cluster to Oracle Grid Infrastructure 12c Release 2 (12.2) after a successful upgrade.

1.  As `grid` user, use the command syntax `mgmtua downgrade` from 19c Grid home to downgrade Oracle Member Cluster where `oldOracleHome` is 12c Release 2 (12.2) Grid home and `version` is the five digit release number:
        $ $ORACLE_HOME/bin/mgmtua downgrade -member -oldOracleHome /u01/app/12.2.0/grid -toVersion version
2.  As `root` user, use the command syntax `rootcrs.sh -downgrade` from 19c Grid home to downgrade Oracle Grid Infrastructure on all nodes, in any sequence. For example:
        # $ORACLE_HOME/crs/install/rootcrs.sh -downgrade

    Run this command from a directory that has write permissions for the Oracle Grid Infrastructure installation user. You can run the downgrade script in parallel on all cluster nodes, but one.
3.  As `root` user, downgrade the last node after you downgrade all other nodes:
        # $ORACLE_HOME/crs/install/rootcrs.sh -downgrade
4.  As `grid` user, remove Oracle Grid Infrastructure 19c Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the `rootupgrade.sh` script has run successfully, log in as the Oracle Grid Infrastructure installation owner.

    2.  Use the following command to start the installer, where `/u01/app/19.0.0/grid` is the location of the new (upgraded) Grid home:

            $ cd $ORACLE_HOME/oui/bin
            $ ./runInstaller -nowait -waitforcompletion -ignoreSysPrereqs
            -updateNodeList -silent CRS=false
            ORACLE_HOME=/u01/app/19.0.0/grid
            "CLUSTER_NODES=node1,node2,node3"
             -doNotUpdateNodeList

        Add the flag `-cfs` if the Grid home is a shared home.
5.  As `root` user, start the 12c Release 2 (12.2) Oracle Clusterware stack on all nodes.
        # crsctl start crs

    **Note:**

    You must start Oracle Clusterware on last downgraded node first, and then on other nodes.
6.  As `grid` user, set Oracle Grid Infrastructure 12c Release 2 (12.2) Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the `rootupgrade` script has run successfully, log in as the Oracle Grid Infrastructure installation owner.

    2.  Use the following command to start the installer, where the path you provide for `ORACLE_HOME` is the location of the home directory from the earlier Oracle Clusterware installation.

            $ cd $ORACLE_HOME/oui/bin
            $ ./runInstaller -nowait -waitforcompletion -ignoreSysPrereqs
            -updateNodeList -silent CRS=true
            ORACLE_HOME=/u01/app/12.2.0/grid
            "CLUSTER_NODES=node1,node2,node3"
7.  As `grid` user, downgrade CHA models from any node where the Grid Infrastructure stack is running from 12c Release 2 (12.2) Grid home and Management Database and `ochad` are up:
        $ ./srvctl stop cha
        $ ./chactl import model -file /u01/app/12.2.0/grid/cha/model/os_gold.svm -name DEFAULT_CLUSTER
        $ ./chactl import model -file /u01/app/12.2.0/grid/cha/model/db_gold.svm -name DEFAULT_DB
        $ ./srvctl start cha

    In the example above, `DEFAULT_CLUSTER` and `DEFAULT_DB` are function names that you must pass as values.

**Related Topics**

- [Downgrading Oracle Domain Services Cluster to 12c Release 2 (12.2)](downgrading-oracle-domain-services-cluster-to-12c-release-2.md)
- [Downgrading to Oracle Grid Infrastructure 12c Release 1 (12.1)](downgrading-to-oracle-grid-infrastructure-12c-release-1-12-1.md)

**Parent topic:** [Downgrading Oracle Clusterware to 12c Release 2 (12.2)](downgrading-oracle-clusterware-to-12.2.md)
