You can use Oracle Database 19c, 18c, Oracle Database 12c releases 1 and 2 and Oracle Database 11g release 2 (11.2.0.3 or later) with Oracle Grid Infrastructure 19c.

Do not use the versions of `srvctl`, `lsnrctl`, or other Oracle Grid infrastructure home tools to administer earlier version databases. Only administer earlier Oracle Database releases using the tools in the earlier Oracle Database homes. To ensure that the versions of the tools you are using are the correct tools for those earlier release databases, run the tools from the Oracle home of the database or object you are managing.

Oracle Database homes can only be stored on Oracle ASM Cluster File System (Oracle ACFS) if the database version is Oracle Database 11g release 2 or later.

When installing 11.2 databases on an Oracle Flex ASM cluster, the Oracle ASM cardinality must be set to `All`.

**Note:**

If you are installing Oracle Database 11g release 2 with Oracle Grid Infrastructure 12c release 2 (12.2), then before running Oracle Universal Installer (OUI) for Oracle Database, run the following command on the local node only:

    Grid_home/oui/bin/runInstaller -ignoreSysPrereqs -updateNodeList
    ORACLE_HOME=Grid_home "CLUSTER_NODES={comma_separated_list_of_nodes}"
    CRS=true LOCAL_NODE=local_node [-cfs]

Use the `-cfs` option only if the Grid_home is on a shared location.

On IBM AIX on POWER Systems (64–Bit), when installing Oracle RAC database 12c release 1 (12.1.0.2) on Oracle Grid Infrastructure 12c release 2 (12.2), do the following:

1.  Install and configure Oracle Grid Infrastructure 12c release 2 (12.2) as described in this guide.

2.  Copy the Oracle RAC database 12c release 1 (12.1.0.2) shiphome locally on one of the nodes.

3.  Edit the file `database/install/oraparam.ini` and comment the following line:

        ***********************
         EXT_LIB=../stage/ext/lib
         ***********************

4.  Save the changes and run the Oracle RAC database 12c release 1 (12.1.0.2) installer.

        ./runInstaller

**Parent topic:** [Using Earlier Oracle Database Releases with Oracle Grid Infrastructure](using-earlier-oracle-database-releases-with-oracle-grid-infrastructure.md)
