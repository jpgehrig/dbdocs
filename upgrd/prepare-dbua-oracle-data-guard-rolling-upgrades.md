## Preparing for Database Rolling Upgrades Using Oracle Data Guard

If you perform your upgrade using Oracle Data Guard to carry out a rolling upgrade, then you must move the Data Guard broker configuration files before starting your upgrade.

The default location for the `DB_BROKER_CONFIG` files is in the `dbs` directory in the earlier release Oracle Database Oracle home. When you perform a rolling upgrade of database instances using Oracle Data Guard, you must move the `DG_BROKER_CONFIG` files to a mount point location outside of the earlier release Oracle home. Also ensure that the `DG_BROKER_CONFIG_FILE`n parameters specify that location, instead of a location in the earlier release Oracle home. During database upgrade, don't migrate the listener. After the upgrade is complete, stop the listener, shut down the database, copy over the `listener.ora` and `tnsnames.ora` from the earlier source Oracle Database release environment to the new Oracle Database release environment, and start the listener and database

### Tasks Before Starting Your Upgrade

To enable access to the `DB_BROKER_CONFIG` files during a rolling upgrade, you must complete the following tasks before starting the upgrade

1.  Before you start the upgrade, if you are not using Oracle Automatic Storage Management (Oracle ASM) for storage, then set the Oracle Data Guard files `DG_BROKER_CONFIG_FILE1` and `DG_BROKER_CONFIG_FILE2` to a separate mount point on your server that is outside of the Oracle home path for either the source or target Oracle Database Oracle homes.

    **Note:**

    Prior to Oracle Database 21c, the default ORACLE_HOME layout combined ORACLE_HOME, ORACLE_BASE_HOME and ORACLE_BASE_CONFIG into a single location. Starting with Oracle Database 21c, the only available configuration is a read-only ORACLE_HOME where ORACLE_BASE_HOME and ORACLE_BASE_CONFIG are located separately from ORACLE_HOME. Files such as the Oracle Data Guard Files, which were previously located in the folder `dbs`, are now located in `ORACLE_BASE_CONFIG/dbs`.

2.  Complete a successful upgrade of your earlier release Oracle home to the new Oracle Database release.

### Tasks During the Upgrade

Do not migrate the listener during the upgrade.

Oracle recommends that you use AutoUpgrade to complete the upgrade. See:

[AutoUpgrade and Oracle Data Guard](autoupgrade-oracle-database-config-options.md)

### Tasks After Completing Your Upgrade

1.  Stop the listener for the new release Oracle Database.
2.  Shut down the new release Oracle Database.
3.  Copy over the `listener.ora` and `tnsnames.ora` files from the earlier release Oracle Database to the new release Oracle Database.
4.  Start the listener and new release Oracle Database

Refer to Oracle Data Guard Broker for information about moving your Data Guard broker configuration files.

**Related Topics**

- [Renaming the Broker Configuration Files](../dgbkr/managing-oracle-data-guard-broker-configurations.md)

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)
