## A  Oracle Data Guard Broker Upgrading and Downgrading

Use these topics to upgrade or downgrade Oracle databases and Oracle Enterprise Manager Cloud Control (Cloud Control) in a broker configuration.

- Upgrading from Oracle Database 11g Release 2 (11.2) to Oracle Database 12c

- Considerations While Using the DBMS_ROLLING Package

- Downgrading from Oracle Database 12c

**See Also:**

[Oracle Data Guard Installation](oracle-data-guard-broker-installation-requirements.md)

### Upgrading from Oracle Database 11g Release 2 (11.2) to Oracle Database 12c

If you are currently running Oracle Data Guard on Oracle Database 11g Release 2 (11.2), then you can upgrade the database software to Oracle Database 12c Release 1 (12.1) or Oracle Database 12c Release 2 (12.2) using the Oracle Database installation documentation that is appropriate for your operating system.

The following steps use Oracle Database 12c Release 2 (12.2), but you could substitute Oracle Database 12c Release 1 (12.1).

1.  Issue the following DGMGRL command to disable fast-start failover:

        DGMGRL> DISABLE FAST_START FAILOVER;

2.  Shut down the Oracle Data Guard broker.

    1.  Issue the following DGMGRL command to disable the broker's active management of the databases in the Oracle Data Guard configuration:

            DGMGRL> DISABLE CONFIGURATION;

    2.  Issue the following SQL\*Plus statement to stop the broker:

            SQL> ALTER SYSTEM SET DG_BROKER_START=FALSE;

3.  Make a copy of the current broker configuration files, as indicated by the following initialization parameters: `DG_BROKER_CONFIG_FILE1` and `DG_BROKER_CONFIG_FILE2`.

4.  Upgrade the Oracle Database software to Oracle Database 12c Release 2 (12.2). For step-by-step upgrade instructions, see the Oracle Database installation documentation that is appropriate for your operating system.

    The DGMGRL command-line interface must also be upgraded in order to manage and monitor a broker configuration running on Oracle Database 12c Release 2 (12.2). DGMGRL running on Oracle Database 12c Release 2 (12.2) cannot be used to manage Oracle Data Guard running on Oracle Database 10g or Oracle Database 11g.

    **Note:**

    Existing DGMGRL command-line scripts for Oracle Database 11g Release 2 (11.2) are supported by the DGMGRL command-line interface available in Oracle Database 12c Release 2 (12.2).

5.  After the upgrade to Oracle Database 12c Release 2 (12.2), start the broker on all databases in the Data Guard configuration that have been upgraded to Oracle Database 12c Release 2 (12.2). For example:

    1.  Issue the following SQL\*Plus statements to start the broker:

            SQL> ALTER SYSTEM SET DG_BROKER_START=TRUE;

    2.  Issue the following command to enable the broker's active management of the database in the Oracle Data Guard configuration on the database whose control file role is primary:

            DGMGRL> ENABLE CONFIGURATION;

    The first time the broker starts on Oracle Database 12c Release 2 (12.2) it detects the existence of the Oracle Database 11g Release 2 (11.2) broker configuration files. It automatically upgrades them to include any new properties that were introduced in Oracle Database 12c Release 2 (12.2). This automatic conversion is transparent, permanent, and occurs only once.

**Note:**

The observer that was started prior to the upgrade will automatically be stopped and unable to observe the configuration once the upgrade is complete. You must use an Oracle Database 12c version of the Oracle Observer software to observe Oracle databases running on Oracle Database 12c Release 2 (12.2) or higher.

### Considerations While Using the DBMS_ROLLING Package

When upgrading from Oracle Database Version 12.2 to a higher database version, broker management can remain enabled. However, some considerations must be kept in mind.

The considerations are as follows:

- The broker configuration files must be in a release-neutral location and accessible throughout the upgrade process.

- After upgrading the leading group members, ensure broker communication between the leading group and the trailing group is successful before proceeding with the upgrade process.

  Communication may be disrupted if network files are either not moved to the upgraded `ORACLE_HOME` or need to be edited appropriately. In such cases, shut down the upgraded databases (transient logical standby and any other Leading Group Standby databases), stop the listener, copy the `listener.ora` and `tnsnames.ora` or fix them as appropriate, restart the listener, and restart the databases.

- Before you run the `DBMS_ROLLING` procedure, the physical standby databases must have been operating in Active Data Guard mode.

  If the physical standby databases were operating only in the mounted mode, and the primary database is a multitenant database, you must open the primary database including all its PDBs, and the temp file configuration must be confirmed before you run procedures in the `DBMS_ROLLING` package. This ensures that the necessary temp files are created and available during the upgrade process.

### Downgrading from Oracle Database 12c

If you have upgraded to Oracle Database 12c Release 1 (12.1) or Oracle Database 12c Release 2 (12.2) and want to downgrade to your prior release, then you must downgrade the database release and re-create the broker configuration.

Take the following steps (these steps use Oracle Database 12c Release 2 (12.2), but you could substitute Oracle Database 12c Release 1 (12.1)).

1.  Delete (remove) the Oracle Database 12c Release 2 (12.2) broker configuration using Enterprise Manager or DGMGRL running on Oracle Database 12c Release 2 (12.2). For example, the DGMGRL `REMOVE CONFIGURATION` command can be used.
2.  Downgrade the Oracle Database software to the prior Oracle release. See the Oracle Database documentation that is appropriate for your operating system.
3.  You can downgrade the Oracle Data Guard broker to Oracle Database 11g Release 2 (11.2) as follows:
    - If you are confident that you made no changes to your broker configuration after upgrading to Oracle Database 12c Release 2 (12.2), then you can copy the broker configuration files that you created during the upgrade procedure (described in Upgrading from Oracle Database 11g Release 2 (11.2) to Oracle Database 12c). Then, invoke Enterprise Manager or the DGMGRL command-line interface and reenable the broker configuration as it existed at the time you made that copy.

    - Alternatively, you can invoke Enterprise Manager or the DGMGRL command-line interface to re-create the broker configuration.
