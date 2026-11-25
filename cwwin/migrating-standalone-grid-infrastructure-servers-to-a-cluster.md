## Migrating Standalone Grid Infrastructure Servers to a Cluster

If you have an Oracle Database installation using Oracle Restart (an Oracle Grid Infrastructure installation for a standalone server), you can reconfigure that server as a cluster member node, then complete the following tasks.

1.  Inspect the Oracle Restart configuration with the Server Control (SRVCTL) utility using the following syntax, where db_unique_name is the unique name for the database, and lsnrname is the name of the listener for the database:
        srvctl config database -db db_unique_name
        srvctl config service -db db_unique_name
        srvctl config listener -listener lsnrname

    Write down the configuration information for the server; you will need this information in a later step.
2.  Stop all of the databases, services, and listeners that you discovered in step 1.
3.  If present, unmount all Oracle Automatic Storage Management Cluster File System (Oracle ACFS) file systems.
4.  Log in as an Administrator user and navigate to the directory `Grid_home``\crs\install`, where Grid_home is the location of your Oracle Grid Infrastructure home (Grid home) directory, for example:
        C:\> cd app\19.0.0\grid\crs\install
5.  Unconfigure the Oracle Grid Infrastructure installation for a standalone server (Oracle Restart) using the following command:
        C:\..\install> roothas.bat -deconfig -force
6.  Prepare the server for Oracle Clusterware configuration, as described in Chapter 2 through Chapter 7 of this guide. In addition, choose to install Oracle Grid Infrastructure for a cluster in the same location as Oracle Restart, or in a different location:
    | Option                                                 | Description                                                                                                |
    |:-------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------|
    | Installing in the Same Location as Oracle Restart      | Proceed to step 7.                                                                                         |
    | Installing in a Different Location than Oracle Restart | Set up Oracle Grid Infrastructure software in the new Grid home software location, then proceed to step 7. |
7.  Set the environment variables as follows:
        export oracle_install_asm_UseExistingDG=true or false
        export oracle_install_asm_DiskGroupName=disk_group_name
        export oracle_install_asm_DiskDiscoveryString=asm_discovery_string
        export oracle_install_asm_ConfigureGIMRDataDG=true or false
        export oracle_install_asm_GIMRDataDGName=disk_group_name
8.  As the Oracle Installation user for Oracle Grid Infrastructure, run the installer.
    You can complete the installation interactively, or if you want to perform a silent installation, then save and stage the response file. After saving the response file, run the following command. For the `-responseFile` parameter, specify the full path name where the response file was saved, for example:

        C:\> Grid_home\setup.exe -silent -responseFile C:\Users\dba1\scripts\GI.rsp
9.  Mount the Oracle ASM disk group used by Oracle Restart.
10. If you used Oracle ACFS with Oracle Restart, then:
    1.  Start Oracle ASM Configuration Assistant (ASMCA). Run the `volenable` command to enable all Oracle Restart disk group volumes.
    2.  Mount all Oracle ACFS file systems manually.
11. Add back Oracle ACFS resources to the Oracle Clusterware home, using the information you wrote down in step 1.
    Register the Oracle ACFS resources using a commands similar to the following:
        C:\> cd app\grid\product\19.0.0\grid\bin
        C:\..bin> srvctl add filesystem -device \\.\ORCLDATADISK4
        -diskgroup ORestartData -volume db1
        -mountpointpath C:\app\grid\prodcut\19.0.0\dbhome1 -user grid
12. Add the Oracle Database for support by Oracle Grid Infrastructure for a cluster, using the configuration information you recorded in step 1. Use the following command syntax, where db_unique_name is the unique name of the database on the node, and nodename is the name of the node:
        srvctl add database -db db_unique_name -spfile -pwfile -oraclehome %ORACLE_HOME% -node
        nodename

    1.  Verify that the `%ORACLE_HOME%` environment variable is set to the location of the database home directory.
    2.   To add the database name `mydb`, enter the following command:
            srvctl add database -db mydb -spfile -pwfile -oraclehome %ORACLE_HOME% -node node1
    3.  Add each service to the database, using the command `srvctl add service`. For example:
            srvctl add service -db mydb -service myservice
13. Add nodes to your cluster, as required, using the Oracle Grid Infrastructure installer.
    **See Also:**

    - [Recording Response Files](recording-response-files.md) for more information about saving the response file

    - [Oracle Clusterware Administration and Deployment Guide](../cwadd/adding-and-deleting-cluster-nodes.md) for information about adding nodes to your cluster

**Parent topic:** [Modifying or Deinstalling Oracle Grid Infrastructure](modifying-or-deinstalling-oracle-grid-infrastructure.md)
