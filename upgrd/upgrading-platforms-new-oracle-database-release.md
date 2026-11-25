## About Upgrading Platforms for a New Oracle Database Release

Review these topics if you upgrade your operating system or hardware for a new Oracle Database release.

- About Upgrading Your Operating System
  Check operating system requirements for new releases, and if necessary, upgrade your operating system before upgrading Oracle Database.
- Options for Transporting Data to a Different Operating System
  Review these restrictions and guidelines if you want to perform a cross-platform upgrade.

**Parent topic:** [Introduction to Upgrading Oracle Database](intro-to-upgrading-oracle-database.md)

### About Upgrading Your Operating System

Check operating system requirements for new releases, and if necessary, upgrade your operating system before upgrading Oracle Database.

When you upgrade to a new release of Oracle software, the operating system requirements may have changed. If required, upgrade the operating system before upgrading Oracle Database.

**See Also:**

- [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform to obtain a list of supported operating systems

- Your operating system-specific documentation for information about how to perform an operating system upgrade

**Parent topic:** About Upgrading Platforms for a New Oracle Database Release

### Options for Transporting Data to a Different Operating System

Review these restrictions and guidelines if you want to perform a cross-platform upgrade.

When using DBUA or when performing a manual upgrade for Oracle Database, you cannot directly migrate or transport data in a database on one operating system to a database on another operating system. For example, you cannot migrate data in an Oracle database on Solaris to an Oracle 12c database on Windows using DBUA. You must follow procedures specific to your operating system platforms.

To see the platforms that support cross-platform data transport, run the following query using SQL\*Plus:

    SELECT * FROM V$TRANSPORTABLE_PLATFORM ORDER BY PLATFORM_NAME;

**Note:**

If the source platform and the target platform are of different endianness, then you cannot use the `RMAN` `CONVERT` `DATABASE` command. This process requires both the source and target platform to be the same endian value. Your available options are Data Pump replication, Data Pump export/import, or Transportable Tablespace, with an `RMAN` `CONVERT` `TABLESPACE`. If the platforms are of the same endianness, then no conversion is necessary and data can be transported as if on the same platform.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/transporting-data.md) for a discussion of transporting data across platforms

- [Oracle Database Backup and Recovery User's Guide](../bradv/rman-transporting-data-across-platforms.md) for information on using the `RMAN` `CONVERT` `DATABASE` and `RMAN` `CONVERT` `TABLESPACE` commands

**Parent topic:** About Upgrading Platforms for a New Oracle Database Release
