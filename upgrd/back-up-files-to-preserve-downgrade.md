## Back Up Files to Preserve Downgrade and Recovery Options

To ensure that you can recover from upgrade issues, and downgrade to an earlier release if necessary, Oracle recommends that you implement a backup strategy for your database, and for some specific files.

- Prepare a Backup Strategy Before Upgrading Oracle Database
  You must design and carry out an appropriate backup strategy to ensure a successful upgrade.
- Oracle Data Guard Broker Configuration File and Downgrades
  With upgrades to Oracle Database 19c and later releases, you must back up the Data Guard broker configuration file to preserve the capability to downgrade to an earlier release.
- Exporting a Broker Configuration
  Use the `EXPORT CONFIGURATION` command to export the metadata contained in the broker configuration file to a text file.

**Parent topic:** [Tasks to Prepare for Oracle Database Upgrades](tasks-to-prepare-for-oracle-database-upgrades.md)

### Prepare a Backup Strategy Before Upgrading Oracle Database

You must design and carry out an appropriate backup strategy to ensure a successful upgrade.

For Oracle Database Enterprise Edition, the primary fallback mechanism is Flashback Database. However, Flashback Database can't be used to revert an unplug-plug upgrade. For unplug-plug upgrades, rely on other fallback strategies, such as an RMAN backup.

If you use AutoUpgrade, then Oracle recommends that you specify `target_pdb_copy_option=``file_name_convert`, in the AutoUpgrade configuration file, where `file_name_convert` is a convert pattern prefixed to the data files. When you do that, AutoUpgrade directs the database to create copies of the data files before plugging in the database. Choosing to use this method enables you to use the original database as a fallback. However, be aware that when you create data file copies, the upgrade requires additional disk space and extra time.

To develop a backup strategy, consider the following questions:

- How long can the production database remain inoperable before business consequences become intolerable?
- What backup strategy is necessary to meet your availability requirements?
- Are backups archived in a safe, offsite location?
- Are backups tested to ensure that they are done properly?
- How quickly can backups be restored (including backups in offsite storage)?
- Have disaster recovery procedures been tested successfully?

Your backup strategy should answer all of these questions, and include procedures for successfully backing up and recovering your database. For information about implementing backup strategies using RMAN, review Oracle Database Backup and Recovery User’s Guide.

In addition, to ensure that you are prepared for a downgrade, review the downgrade chapter and complete any preparation steps you may need to prepare for your release.

**Related Topics**

- [Backing Up the Database](../bradv/backing-up-database.md)
- [Using Flashback Database and Restore Points](../bradv/using-flasback-database-restore-points.md)

**Parent topic:** Back Up Files to Preserve Downgrade and Recovery Options

### Oracle Data Guard Broker Configuration File and Downgrades

With upgrades to Oracle Database 19c and later releases, you must back up the Data Guard broker configuration file to preserve the capability to downgrade to an earlier release.

In releases before Oracle Database 19c, Oracle Database settings that are mapped to Oracle Data Guard broker properties are maintained in the Oracle Data Guard broker configuration file, and can be modified using the `DGMGRL` command-line interface. However, starting with Oracle Database 19c, these database settings are no longer stored in the broker configuration file. As a result of this change, although you can continue to modify these properties using DGMGRL, the values that you modify are no longer stored in the Oracle Data Guard broker configuration file. Instead, the DGMGRL commands directly modify the Oracle Database initialization parameters or database settings to which these Oracle Data Guard Broker properties are mapped.

Because of this change to the way that property settings are managed, if you use Oracle Data Guard broker, then Oracle recommends that you export your earlier release Oracle Data Guard broker configuration file to a secure backup location before you start the upgrade. If you do not back up the Oracle Data Guard broker configuration file before the upgrade, then after the upgrade, you cannot downgrade to an earlier release and retain the property options you previously selected for Oracle Data Guard.

**Parent topic:** Back Up Files to Preserve Downgrade and Recovery Options

### Exporting a Broker Configuration

Use the `EXPORT CONFIGURATION` command to export the metadata contained in the broker configuration file to a text file.

The directory in which the broker configuration file is stored must be accessible to the Oracle server process.

1.  Connect to the primary database.
        DGMGRL> CONNECT sysdg@North_Sales.example.com;
        Password: password
        Connected to "North_Sales"
        Connected as SYSDG.
2.  Export the broker configuration.
    The following command exports the broker configuration and stores it in a file named `myconfig.txt` in the trace directory.

        DGMGRL> EXPORT CONFIGURATION TO 'myconfig.txt';
        Succeeded.

**Parent topic:** Back Up Files to Preserve Downgrade and Recovery Options
