You must design and carry out an appropriate backup strategy to ensure a successful upgrade.

For Oracle Database Enterprise Edition, with non-CDB upgrades, the primary fallback mechanism is Flashback Database. By default, AutoUpgrade creates a guaranteed restore point before the upgrade. This restore point can be used to quickly revert the database upgrade if needed.

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

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)
