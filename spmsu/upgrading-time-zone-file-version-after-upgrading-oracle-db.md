If the Pre-Upgrade Information Tool instructs you to upgrade the time zone files after completing the database upgrade, then use the `DBMS_DST` PL/SQL package to upgrade the time zone file.

Oracle Database supplies multiple versions of time zone files. There are two types of files associated with each time zone file: a large file, which contains all the time zones defined in the database, and a small file, which contains only the most commonly used time zones. The large versions are designated as `timezlrg_``version_number``.dat`. The small versions are designated as `timezone_``version_number``.dat`. The files are located in the `oracore/zoneinfo` subdirectory under the Oracle Database home directory.

**Related Topics**

- [Oracle Database Globalization Support Guide](../nlspg/datetime-data-types-and-time-zone-support.md)
- <https://support.oracle.com/rs?type=doc&id=1585343.1>

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
