Learn about backing up a database in NOARCHIVELOG mode.

For an Oracle database running in `NOARCHIVELOG` mode, the database must be in a consistent state when you create a VSS snapshot. Backups made while the database is open read/write are not supported.

- [Making Component-Based Backups of a NOARCHIVELOG Database](making-component-based-backups-of-a-noarchivelog.md)
  For an Oracle database in `NOARCHIVELOG` mode, the only supported component-based VSS snapshot is of `Oracle Database` when the type is full, default, or copy.
- [Making Volume-Based Backups of a NOARCHIVELOG Database](making-volume-based-backups-of-a-noarchivelog.md)
  Learn how to make volume-based backups of a NOARCHIVELOG database.

**Parent topic:** [About Backing Up a Database](about-backing-up-a-database.md)
