## Deinstallation Response File Example for Oracle Database Client

You can run the deinstallation tool with the `-paramfile` option to use the values you specify in the response file.

The following is an example of a response file, in which the Oracle Database binary owner is `oracle`, the Oracle Database home (Oracle home) is in the path `C:\app\oracle\product\19.0.0\client_1`, the Oracle base (where other Oracle software is installed) is `C:\app\oracle`, the Oracle Inventory home is `C:\Program Files\Oracle\Inventory`, and the local node (the node where you run the deinstallation session from) is `myserver`:

    # Copyright (c) 2005, 2019, Oracle and/or its affiliates. All rights reserved.
    ORACLE_HOME=C:\app\dbinstall3\19.3admnClnt\client_1
    COMPS_TO_REMOVE=ntoledb,asp.net,odp.net
    ORACLE_HOME_VERSION=19.0.0.0.0
    ORACLE_BASE=C:\app\dbinstall3\19.3admnClnt\cbase
    INVENTORY_LOCATION=C:\Program Files\Oracle\Inventory
    CRS_HOME=false
    HOME_TYPE=CLIENT
    silent=false
    WindowsRegistryCleanupList=C:\Users\DBINST~1\AppData\Local\Temp\2\deinstall2019-05-30_03-29-28AM\utl\registry_cleanup.lst
    MinimumSupportedVersion=11.2.0.1.0
    LOCAL_NODE=<hostname>
    local=false
    ObaseCleanupPtrLoc=C:\Users\DBINST~1\AppData\Local\Temp\2\deinstall2019-05-30_03-29-28AM\utl\orabase_cleanup.lst
    ORACLE_HOME=C:\app\dbinstall3\19.3admnClnt\client_1
    LOGDIR=C:\Program Files\Oracle\Inventory\logs\
    OLD_ACTIVE_ORACLE_HOME=
    ORACLE_HOME_VERSION_VALID=true

**Parent topic:** [Removing Oracle Database Client Software](removing-oracle-database-client-software.md)
