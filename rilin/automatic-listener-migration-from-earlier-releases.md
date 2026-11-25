## Automatic Listener Migration from Earlier Releases

Review this information for listener migration from earlier database releases.

If your system has an Oracle Grid Infrastructure 11g Release 2 (11.2), 12c Release 1 (12.1), 12c Release 2 (12.2), or 18c installation, and you install Oracle Grid Infrastructure 19c either to coexist with or to upgrade the Oracle Grid Infrastructure 11.2, 12.1, 12.2, or 18c installation, then most installation types automatically migrate the existing listener to the 19c Oracle home. During migration, the upgrade process configures and starts a default Oracle Net Listener using the same TCP/IP port as the existing listener, with the IPC key value.

During the Oracle Clusterware upgrade, the default listener (`LISTENER_``nodename`) is migrated to the Oracle Grid Infrastructure home (Grid home). Oracle Database Configuration Assistant always uses the default listener.

**Note:**

During migration, client applications may not be able to connect to any databases that are registered to the listener that is being migrated.

**Parent topic:** [Creating Oracle RAC or Oracle RAC One Node Databases with Oracle DBCA](selecting-dbca-options-to-create-oracle-rac-or-oracle-rac-one-node-databases-with-dbca.md)
