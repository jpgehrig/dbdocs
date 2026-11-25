## About Oracle Deinstallation Options

The `deinstall.bat` command stops Oracle software, and removes Oracle software and configuration files on the operating system.

You can remove the following software using `deinstall`:

- Oracle Database

- Oracle Grid Infrastructure, which includes Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM)

- Oracle Real Application Clusters (Oracle RAC)

- Oracle Database Client

The deinstall command is available in Oracle home directories after installation. It is located in the `ORACLE_HOME``\deinstall` directory.

The deinstallation tool uses the information you provide, plus information gathered from the software home to create a response file. You can alternatively supply a response file generated previously by the `deinstall` command using the `–checkonly` option, or by editing the response file template.

**Note:**

- You must run the `deinstall` command from the same release to remove Oracle software. Do not run the `deinstall` command from a later release to remove Oracle software from an earlier release. For example, do not run the `deinstall` command from the 19c Oracle home to remove Oracle software from an existing 12.2 Oracle home

- Starting with Oracle Database 12c Release 1 (12.1.0.2), the `roothas.bat `script replaces the `roothas.pl` script in the Oracle Grid Infrastructure home for Oracle Restart, and the `rootcrs.bat` script replaces the `rootcrs.pl` script in the Grid home for Oracle Grid Infrastructure for a cluster.

If the software in the Oracle home is not running (for example, after an unsuccessful installation), then the deinstallation tool cannot determine the configuration, and you must provide all the configuration details either interactively or in a response file.

In addition, before you run `deinstall` for Oracle Grid Infrastructure installations:

- Dismount Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and disable Oracle Automatic Storage Management Dynamic Volume Manager (Oracle ADVM).

- If Grid Naming Service (GNS) is in use, then notify your DNS administrator to delete the subdomain entry from the DNS.

**See Also:**

[Oracle Real Application Clusters Installation Guide for Microsoft Windows x64 (64-Bit)](../riwin/local-listener-for-an-oracle-rac-database.md) for information about the `-local` option

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
