## About Oracle Deinstallation Options

The `deinstall.bat` command stops Oracle software, and removes Oracle software and configuration files on the operating system.

The `deinstall` command is available in Oracle home directories after installation. It is located in the `%ORACLE_HOME%\deinstall` directory.

`deinstall` creates a response file by using information in the Oracle home and using the information you provide. You can use a response file that you generated previously by running the `deinstall` command using the `-checkonly` option. You can also edit the response file template.

**Note:**

- You must run the `deinstall` command from the same release to remove Oracle software. Do not run the `deinstall` command from a later release to remove Oracle software from an earlier release. For example, do not run the `deinstall` command from the 19c Oracle home to remove Oracle software from an existing 11.2.0.4 Oracle home.

- Starting with Oracle Database 12c Release 1 (12.1.0.2), the `roothas.bat` script replaces the `roothas.pl` script in the Oracle Grid Infrastructure home for Oracle Restart, and the `rootcrs.bat` script replaces the `rootcrs.pl` script in the Grid home for Oracle Grid Infrastructure for a cluster.

If the software in the Oracle home is not running (for example, after an unsuccessful installation), then the `deinstall` cannot determine the configuration and you must provide all the configuration details either interactively or in a response file.

**Parent topic:** [Removing Oracle RAC Software](removing-oracle-rac-software.md)
