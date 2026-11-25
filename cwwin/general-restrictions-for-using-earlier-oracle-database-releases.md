## General Restrictions for Using Earlier Oracle Database Releases

You can use Oracle Database 12c Release 1 and Release 2 and Oracle Database 11g Release 2 with Oracle Grid Infrastructure 12c Release 2 (12.2).

Do not use the versions of `srvctl`, `lsnrctl`, or other Oracle Grid infrastructure home tools to administer earlier version databases. Only administer earlier Oracle Database releases using the tools in the earlier Oracle Database homes. To ensure that the versions of the tools you are using are the correct tools for those earlier release databases, run the tools from the Oracle home of the database or object you are managing.

Oracle Database homes can only be stored on Oracle ASM Cluster File System (Oracle ACFS) if the database release is Oracle Database 11g Release 2 or higher. Earlier releases of Oracle Database cannot be installed on Oracle ACFS because these releases were not designed to use Oracle ACFS.

When installing Oracle databases on a Flex ASM cluster, the Oracle ASM cardinality must be set to `All`.

**Note:**

If you are installing Oracle Database 11g Release 2 with Oracle Grid Infrastructure 12c Release 2 (12.2), then before running the Oracle Universal Installer (OUI) for Oracle Database, run the following command on the local node only:

    Grid_home\oui\bin\setup.exe -ignoreSysPrereqs -updateNodeList
    ORACLE_HOME=Grid_home "CLUSTER_NODES={comma_separated_list_of_nodes}"
    CRS=true LOCAL_NODE=local_node [-cfs]

Use the `-cfs` option only if the Grid_home is on a shared location.

**Parent topic:** [Using Earlier Oracle Database Releases with Grid Infrastructure](using-earlier-oracle-database-releases-with-grid-infrastructure.md)
