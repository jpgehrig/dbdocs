Use the Parallel Upgrade Utility with the `-T` option to take schema-based tablespaces offline during upgrade.

Oracle Database can read file headers created in earlier releases, so you are not required to do anything to them during the upgrade. The file headers of `READ ONLY` tablespaces are updated when they are changed to `READ WRITE`.

If the upgrade suffers a catastrophic error, so that the upgrade is unable to bring the tablespaces back online, then review the upgrade log files. The log files contain the actual SQL statements required to make the tablespaces available. To bring the tablespaces back online, you must run the SQL statements in the log files for the database, or run the log files for each PDB.

### Viewing Tablespace Commands in Upgrade Log Files

If a catastrophic upgrade failure occurs, then you can navigate to the log directory (`Oracle_base``/cfgtoologs/dbua`), and run commands in the log files manually to bring up tablespaces. You can view tablespace commands in the following log files:

- Non-CDB Upgrades: `catupgrd0.log`

- PDB databases: `catupgrd``pdbname``0.log`, where `pdbname` is the name of the PDB that you are upgrading.

At the beginning of each log file, you find SQL statements such as the following, which sets tables to `READ ONLY`:

    SQL> ALTER TABLESPACE ARGROTBLSPA6 READ ONLY;

    Tablespace altered.

    SQL> ALTER TABLESPACE ARGROTBLSPB6 READ ONLY;

    Tablespace altered.

Near the end of each log file, you find SQL statements to reset tables to `READ WRITE`:

    SQL> ALTER TABLESPACE ARGROTBLSPA6 READ WRITE;

    Tablespace altered.

    SQL> ALTER TABLESPACE ARGROTBLSPB6 READ WRITE;

    Tablespace altered.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/transporting-data.md) for information about transporting tablespaces between databases

**Parent topic:** [Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades](db-preparation-tasks-before-starting-db-upgrades.md)
