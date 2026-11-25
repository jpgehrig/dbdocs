## Deinstallation Parameter File Example for Oracle RAC

You can run the `deinstall` command on Oracle RAC Databases with the `-paramfile` option to use the values you specify in the parameter file.

The following is an example of a parameter file, in which the Oracle Database binary owner is `oracle`, the Oracle Database home (Oracle home) is in the path `/u01/app/oracle/product/19.0.0/dbhome_1/`, the Oracle base (where other Oracle software is installed) is `/u01/app/oracle/`, the central Oracle Inventory home (`oraInventory`) is `/u01/app/oraInventory`, the virtual IP address (VIP) is `192.0.2.1`, the local node (the node where you run the `deinstall` command from) is `myserver`, and the OSDBA group is `dba`:

    #Copyright (c) 2005, 2014 Oracle Corporation. All rights reserved.
    #Mon Feb 17 06:48:39 UTC 2014
    DISK_GROUPS.sidb=
    ASM_HOME=
    ASM_LOCAL_SID=
    LOGDIR=/u01/app/oracle/product/19.0.0/dbhome_1/oraInventory/logs/
    ORACLE_BASE.sidb=/u01/app/oracle/
    RECOVERY_LOC.sidb=
    STORAGE_TYPE.sidb=FS
    ORACLE_BASE=/u01/app/oracle/
    INVENTORY_LOCATION=/u01/app/oraInventory
    DB_TYPE.sidb=SI_DB
    NODE_LIST.sidb=myserver
    ARCHIVE_LOG_DESTINATION_LOC.sidb=
    LOCAL_SID.sidb=sidb
    DB_UNIQUE_NAME_LIST=sidb
    ASM_FILES.sidb=
    HOME_TYPE=SIDB
    CRS_HOME=false
    RAW_MAPPING_FILE.sidb=
    SID_LIST.sidb=sidb
    ORACLE_BINARY_OK=true
    DATAFILE_LOC.sidb=/u01/app/oracle/oradata
    local=false
    LOCAL_NODE=myserver
    CREATION_MODE.sidb=y
    CONFIGFILE_LOC.sidb=
    DIAG_DEST.sidb=/u01/app/oracle/
    silent=false
    ORACLE_HOME=/u01/app/oracle/product/19.0.0/dbhome_1/
    SPFILE_LOC.sidb=

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
