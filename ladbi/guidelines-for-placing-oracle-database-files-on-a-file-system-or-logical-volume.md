## Guidelines for Placing Oracle Database Files On a File System or Logical Volume

If you choose to place the Oracle Database files on a file system, then use the following guidelines when deciding where to place them:

- The default path suggested by Oracle Universal Installer for the database file directory is a subdirectory of the Oracle base directory.

- You can choose either a single file system or more than one file system to store the database files:

  - If you want to use a single file system, then choose a file system on a physical device that is dedicated to the database.

    For best performance and reliability, choose a RAID device or a logical volume on more than one physical device, and implement a stripe-and-mirror-everything (SAME) storage policy.

  - If you want to use more than one file system, then choose file systems on separate physical devices that are dedicated to the database.

    This method enables you to distribute physical input-output operations and create separate control files on different devices for increased reliability. It also enables you to fully implement Oracle Optimal Flexible Architecture (OFA) guidelines. Choose the `Advanced` database creation option to implement this method.

- If you intend to create a preconfigured database during the installation, then the file system (or file systems) that you choose must have at least 2 GB of free disk space.

  For production databases, you must estimate the disk space requirement depending on the use of the database.

- For optimum performance, the file systems that you choose must be on physical devices that are used only by the database.

- The Oracle user running the Oracle Database installation must have write permissions to create the files in the path that you specify.

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
