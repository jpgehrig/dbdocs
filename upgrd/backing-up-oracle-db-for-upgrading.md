## Back Up Oracle Database Before Upgrading

Use this procedure to back up your existing Oracle Database before you attempt an upgrade.

**Caution:**

Before you make any changes to the Oracle software, Oracle strongly recommends that you create a backup of the Oracle software and databases. For Oracle software running on Microsoft Windows operating systems, you must also take a backup of the Windows registry. On Microsoft Windows, without a registry backup, you cannot restore the Oracle software to a working state if the upgrade fails, and you want to revert to the previous software installation.

Before you cleanly shut down the database, you must run AutoUpgrade using the `preupgrade` parameter. To minimize downtime, you can perform an online backup, or create a guaranteed restore point.

1.  Sign on to Oracle RMAN:

        rman "target / nocatalog"

2.  Run the following RMAN commands:

        RUN
        {
            ALLOCATE CHANNEL chan_name TYPE DISK;
            sql 'ALTER SYSTEM ARCHIVE LOG CURRENT';
            BACKUP DATABASE FORMAT '/tmp/db%U' TAG before_upgrade
            PLUS ARCHIVELOG FORMAT '/tmp/arch%U' TAG before_upgrade;
            BACKUP CURRENT CONTROLFILE FORMAT '/tmp/ctl%U' TAG before_upgrade;
        }

    **Caution:**

    You must ensure that no other RMAN backup runs during this backup. If another RMAN command backs up and removes archive log, then this backup could be unrecoverable, because the other RMAN command has removed the archive logs.

**Related Topics**

- [About Online Backups and Backup Mode](../bradv/rman-backup-concepts.md)
- [Using Flashback Database and Restore Points](../bradv/using-flasback-database-restore-points.md)
- [Backing Up the Database](../bradv/backing-up-database.md)

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)
