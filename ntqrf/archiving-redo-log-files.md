If you installed Oracle Database through the Typical installation, then it is created in the `NOARCHIVELOG` mode. If you created your database through the Custom option of Oracle Database Configuration Assistant, then you had the choice of either `ARCHIVELOG` or `NOARCHIVELOG`.

In `NOARCHIVELOG` mode, redo logs are not archived. Setting your archive mode to `ARCHIVELOG` and enabling automatic archiving causes redo log files to be archived. This protects Oracle Database from both instance and disk failure.

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-archived-redo-log-files.md) for more information about “Managing Archived Redo Logs."

**Parent topic:** [Starting Database Tools from the Command Line](starting-database-tools-from-the-command-line.md)
