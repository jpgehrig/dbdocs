## Migrating Standalone Oracle Grid Infrastructure Servers to a Cluster

If you have an Oracle Database installation using Oracle Restart (that is, an Oracle Grid Infrastructure installation for a standalone server), and you want to configure that server as a cluster member node, then complete the following tasks:

1.  List all the Oracle databases on the server with their version, unique name of the database, and Oracle home information:

    `srvctl config database -home`

2.  Inspect the Oracle Restart configuration of each database with `srvctl` using the following syntax, where db_unique_name is the unique name of the database, and lsnrname is the name of the listener:

    `srvctl config database -db` `db_unique_name`

    `srvctl config service -db` `db_unique_name`

    `srvctl config listener -listener` `lsnrname`

    Write down the configuration information for the server.

3.  Stop all of the databases, services, and listeners that you discovered in step 1.

4.  If present, unmount all Oracle Automatic Storage Management Cluster File System (Oracle ACFS) file systems.

5.  As the `root` user, unconfigure the Oracle Grid Infrastructure installation for a standalone server (Oracle Restart).

        # cd /u01/app/19.0.0/grid/crs/install
        # roothas.sh -deconfig -force

6.  As the `grid` user, update the Oracle central inventory (`oraInventory`).

        $ /u01/app/19.0.0/grid/oui/bin/runInstaller -nowait -waitforcompletion
        -ignoreSysPrereqs -updateNodeList -silent -local CRS=false ORACLE_HOME=Grid_home
        "CLUSTER_NODES=node_list" -doNotUpdateNodeList"

7.  Open the `/etc/oratab` file and remove the entry corresponding to `oracle_restart_home`, in the following format:

        +ASM:oracle_restart_home:N

8.  Prepare the server for Oracle Clusterware configuration, as described in this document. In addition, you can install Oracle Grid Infrastructure for a cluster in the same location as Oracle Restart, or in a different location.

    Installing in the Same Location as Oracle Restart

    1.  Unlock the Oracle Grid Infrastructure installation for a standalone server (Oracle Restart) home, using the following command:

            roothas.sh -unlock -hahome oracle_restart_home

    2.  Proceed to step 9.

    Installing in a Different Location than Oracle Restart

    1.  Set up Oracle Grid Infrastructure software in the new Grid home software location as described in Installing Only the Oracle Grid Infrastructure Software.

    2.  Proceed to step 9.

9.  Set the environment variables as follows:

        export oracle_install_asm_UseExistingDG=true or false
        export oracle_install_asm_DiskGroupName=disk_group_name
        export oracle_install_asm_DiskDiscoveryString=asm_discovery_string

    If `oracle_install_asm_UseExistingDG` is set to false, then you do not need to specify other environment variables.

10. As the Oracle Grid Infrastructure installation owner, create and stage the response file for this installation as described in Recording Response Files.

11. Complete the installation in the silent mode using the following command:

        $ Grid_home/gridSetup.sh -silent -responseFile $ORACLE_HOME/GI.rsp

12. Run `root.sh`.

13. Mount the Oracle ASM disk group used by Oracle Restart.

14. If you used Oracle ACFS with Oracle Restart, then:

    1.  Start Oracle ASM Configuration Assistant (ASMCA). Run the `volenable` command to enable all Oracle Restart disk group volumes.

    2.  Mount all Oracle ACFS file systems manually.

15. Add back Oracle Clusterware services to the Oracle Clusterware home, using the information you wrote down in step 1, including adding back Oracle ACFS resources. For example:

        /u01/app/grid/product/19.0.0/grid/bin/srvctl add filesystem -device
        /dev/asm/db1  -diskgroup ORestartData -volume db1 -mountpointpath
        /u01/app/grid/product/19.0.0/db1 -user grid

16. Add the Oracle Database for support by Oracle Grid Infrastructure for a cluster, using the configuration information you recorded in step 1. Use the following command syntax, where db_unique_name is the unique name of the database on the node, and nodename is the name of the node:

    `srvctl add database -db ``db_unique_name`` -spfile ``spfile_name`` -pwfile ``pwfile_name` `-oraclehome $ORACLE_HOME -node` `nodename`

    1.  For example, first verify that the `ORACLE_HOME` environment variable is set to the location of the database home directory.

    2.  Next, to add the database name `mydb`, enter the following command:

            srvctl add database -db mydb -spfile spfile_name -pwfile pwfile_name -oraclehome $ORACLE_HOME -node node1

    3.  Add each service to the database, using the command `srvctl add service`. For example, add `myservice` as follows:

            srvctl add service -db mydb -service myservice -preferred myinstance

17. Add nodes to your cluster, as required, using the Oracle Grid Infrastructure installer.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/adding-and-deleting-cluster-nodes.md) for information about adding nodes to your cluster.

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
