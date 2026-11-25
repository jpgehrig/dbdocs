## Guidelines for Placing Oracle Recovery Files on a File System

Use the guidelines listed in this section to place Oracle recovery files on a file system.

**Note:**

You must choose a location for recovery files only if you intend to enable automated backups during the installation.

If you place the Oracle recovery files on a file system, use the following guidelines when deciding where to place them:

- To prevent disk failure from making both the data files and the recovery files unavailable, place the recovery files in a file system on a different physical disk from the data files.

  **Note:**

  Alternatively, for both data files and recovery files, use an Oracle Automatic Storage Management disk group.

- The file system that you choose must have at least 2 GB of free disk space.

  The disk space requirement is the default disk quota configured for the fast recovery area (specified by the `DB_RECOVERY_FILE_DEST_SIZE` initialization parameter).

  If you choose the Advanced database configuration option, you can specify a different disk quota value. After you create the database, you can also use Oracle Enterprise Manager Cloud Control or Oracle Enterprise Manager Database Express to specify a different value.

  **See Also:**

  [Oracle Database Backup and Recovery User's Guide](../bradv/rman-architecture.md)

- Oracle Universal Installer suggests that the default location for the database file directory is a subdirectory of the Oracle base directory. However, this default location is not recommended for production databases.

**Parent topic:** [Creating Directories for Oracle Data Files or Recovery Files](creating-directories-data-and-recovery-files.md)
