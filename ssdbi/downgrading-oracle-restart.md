Use this procedure to deconfigure and downgrade Oracle Restart, or to troubleshoot Oracle Restart installation errors.

Running `roothas.sh` with the command flags `-deconfig -force `enables you to deconfigure Oracle Restart without removing the installed binaries. This feature is useful if you encounter an error during an Oracle Grid Infrastructure for a standalone server installation. For example, when you run the `root.sh` command, and find a missing operating system package. By running `roothas.sh -deconfig -force`, you can deconfigure Oracle Restart, correct the cause of the error, and then run `root.sh` again.

1.  As the `oracle` user, create a backup of the SPFILE to a PFILE.
        CREATE PFILE='/u01/app/oracle/product/19.0.0/dbhome_1/dbs/test_init.ora'
        FROM SPFILE='/u01/oracle/dbs/test_spfile.ora';
2.  List all the Oracle Databases on the server with their version, unique name of the database, and Oracle home information.
        $ srvctl config database -home
3.  Downgrade Oracle Database. Refer to [Oracle Database Upgrade Guide](../upgrd/downgrading-oracle-db-after-upgrade.md) for more information about required pre-downgrade tasks, downgrade tasks, post-downgrade tasks, and compatibility information.
    **Note:**

    Downgrade Oracle Database only if the Oracle Database version is higher than the Oracle Restart version to which you are downgrading Oracle Restart.
4.  As the `oracle` user, downgrade the Oracle Restart resources corresponding to the Oracle Database, only if you have downgraded your Oracle Database.
        $ srvctl downgrade database -d db_unique_name -oraclehome $ORACLE_HOME -t to_version
5.  Inspect the Oracle Restart configuration of each database, service, and listener.
        $ srvctl config database -db db_unique_name
        $ srvctl config service -db db_unique_name
        $ srvctl config listener -listener listener_name

    Make a note of the configuration information and use this information when adding the components back to Oracle Restart.
6.  Stop all databases and listeners that are running before you deconfigure or downgrade Oracle Restart.
        $ srvctl stop database -db db_unique_name
        $ srvctl stop listener [-listener listener_name]
7.   As the `root` user, run `roothas.sh` with the `-deconfig -force` flags to deconfigure Oracle Restart.
        # /u01/app/oracle/product/19.0.0/grid/crs/install/roothas.sh -deconfig -force
8.  As the `grid` user, update the Oracle central inventory (`oraInventory`).
        $ /u01/app/oracle/product/19.0.0/grid/oui/bin/runInstaller -updateNodeList -silent ORACLE_HOME=upgraded_Grid_home -local CRS=false
9.  As the `root` user, run `roothas.sh` with the `-unlock` flag to unlock the previous release Oracle Restart home.
        # /u01/app/oracle/product/18.0.0/grid/crs/install/roothas.sh -unlock -dstcrshome previous_release_Grid_home
10. As the `grid` user, reconfigure the previous release Oracle Restart home using the `gridSetup.sh` command.
        $ /u01/app/oracle/product/18.0.0/grid/gridSetup.sh
11. As the `oracle` user, add the components back to Oracle Restart with the same attributes that you noted down before deconfiguring Oracle Restart.
    1.  Add Oracle Database to the Oracle Restart configuration.
            $ srvctl add database -db db_unique_name -oraclehome Oracle_home
    2.  Add the listener to the Oracle Restart configuration.
            $ srvctl add listener -listener listener_name -oraclehome Oracle_home

        For the `-oraclehome` parameter, provide the Oracle home path from which the listener was running before the downgrade.
    3.  Add each service to the database, using the `srvctl add service` command.
            $ srvctl add service -db db_unique_name -service service_name_list

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/downgrading-oracle-db-after-upgrade.md)

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
