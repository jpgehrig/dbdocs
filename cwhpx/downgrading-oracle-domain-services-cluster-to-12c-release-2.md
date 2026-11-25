Use this procedure to downgrade Oracle Domain Services Cluster to Oracle Grid Infrastructure 12c Release 2 (12.2) after a successful upgrade.

1.  As `grid` user, downgrade the Management Database to Oracle Grid Infrastructure 12c Release 2 (12.2):
    1.  Manually copy the most recent time zone files from 19c Grid home to 12c Release 2 (12.2) Grid home, where `timezlrg_number` is the name of the most recent `timzlrg` file and `timezone_number` is the name of the most recent `timezone` file:

            $ cp $ORACLE_HOME/oracore/zoneinfo/timezlrg_number.dat /u01/app/12.2.0/grid/oracore/zoneinfo/timezlrg_number.dat
            $ cp $ORACLE_HOME/oracore/zoneinfo/timezone_number.dat /u01/app/12.2.0/grid/oracore/zoneinfo/timezone_number.dat

    2.  Downgrade application schema using the following command syntax from 19c Grid home:

            $ $ORACLE_HOME/bin/mgmtua downgrade -local -oldOracleHome /u01/app/12.2.0/grid -skipSystemSchemaDowngrade

    3.  Disable and stop MGMTDB resource from 19c Grid home:

            $ cd $ORACLE_HOME/bin
            $ ./srvctl disable mgmtdb
            $ ./srvctl stop mgmtdb

    4.  Downgrade system schema using the following procedure:

        1.  Set `ORACLE_SID` environment variable for 19c Grid home:

                $ export ORACLE_SID=-MGMTDB
                $ cd $ORACLE_HOME/bin

        2.  Start CDB and all PDBs in downgrade mode:

                $ ./sqlplus / as sysdba
                SQL> startup downgrade
                SQL> alter pluggable database all open downgrade;
                SQL> exit

        3.  Downgrade 19c Management Database using the following command syntax, where `/u01/app/grid2` is the Oracle base for Oracle Grid Infrastructure 19c:

                $ $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -d
                /u01/app/grid2 -e -l /u01/app/grid2/cfgtoollogs/mgmtua -b mgmtdowngrade -r
                $ORACLE_HOME/rdbms/admin/catdwgrd.sql

        4.  Set `ORACLE_HOME` and `ORACLE_SID` environment variables for 12c Release 2 (12.2) Grid home:

                $ export ORACLE_HOME=/u01/app/12.2.0/grid/
                $ export ORACLE_SID=-MGMTDB
                $ cd $ORACLE_HOME/bin

        5.  Start CDB and all PDBs in upgrade mode:

                $ ./sqlplus / as sysdba
                SQL> shutdown immediate
                SQL> startup upgrade
                SQL> alter pluggable database all open upgrade;
                SQL> exit

        6.  Run `catrelod` script for 12c Release 2 (12.2) Management Database using the following command syntax, where `/u01/app/grid` is the Oracle base for Oracle Grid Infrastructure 12c Release 2 (12.2):

                $ $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -d
                /u01/app/grid -e -l /u01/app/grid/cfgtoollogs/mgmtua -b mgmtdowngrade
                $ORACLE_HOME/rdbms/admin/catrelod.sql

        7.  Recompile all invalid objects after downgrade using the following command syntax from 12c Release 2 (12.2) Grid home:

                $ $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -d
                /u01/app/grid -e -l /u01/app/grid/cfgtoollogs/mgmtua -b mgmtdowngrade
                $ORACLE_HOME/rdbms/admin/utlrp.sql

    5.  Manually stop the Management Database:

            $ ./sqlplus / as sysdba
            SQL> shutdown immediate
            SQL> exit
2.  As `root` user, use the following command syntax `rootcrs.sh -downgrade` from 19c Grid home to downgrade Oracle Grid Infrastructure on all nodes, in any sequence. For example:
        # $ORACLE_HOME/crs/install/rootcrs.sh -downgrade

    Run this command from a directory that has write permissions for the Oracle Grid Infrastructure installation user. You can run the downgrade script in parallel on all cluster nodes, but one.
3.  As `root` user, downgrade the last node after you downgrade all other nodes:
        # $ORACLE_HOME/crs/install/rootcrs.sh -downgrade
4.  As `grid` user, remove Oracle Grid Infrastructure 19c Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the `rootupgrade.sh` script has run successfully, log in as the Oracle Grid Infrastructure installation owner.

    2.  Use the following command to start the installer, where `/u01/app/19.0.0/grid` is the location of the new (upgraded) Grid home:

            $ cd $ORACLE_HOME/oui/bin
            ./runInstaller -nowait -waitforcompletion -ignoreSysPrereqs
            -updateNodeList -silent CRS=false
            ORACLE_HOME=/u01/app/19.0.0/grid
            "CLUSTER_NODES=node1,node2,node3"
             -doNotUpdateNodeList

        Add the flag `-cfs` if the Grid home is a shared home.
5.  As `root` user, start the 12c Release 2 (12.2) Oracle Clusterware stack on all nodes.
        # crsctl start crs
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

- [Downgrading to Oracle Grid Infrastructure 12c Release 1 (12.1)](downgrading-to-oracle-grid-infrastructure-12c-release-1-12-1.md)

**Parent topic:** [Downgrading Oracle Clusterware to 12c Release 2 (12.2)](downgrading-oracle-clusterware-to-12c-release2.md)
