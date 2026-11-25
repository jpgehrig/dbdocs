## Compatibility Issues for Applications on Different Releases of Oracle Database

You can encounter compatibility issues between different releases of Oracle Database that can affect your applications.

Compatibility issues can occur due to differences between Oracle Database releases. Also, in each new release of Oracle Database, new Oracle reserved words can be added, or initialization parameters can be changed, or the data dictionary can be changed. Review the relevant topics in this documentation for more information.

When you upgrade your Oracle Database software to a new release, ensure that your applications do not use any words reserved by Oracle, that your applications are compatible with the initialization parameters of the database, and that your applications are compatible with the data dictionary of the database.

Also be aware that new releases of Oracle Database can be supported only on particular operating system releases or patch sets. An operating system release and patch set that is supported for use with a previous release of Oracle Database can not be supported for current releases. Check operating system requirements before you install oracle software to perform an upgrade. In addition, to be able to use some features, your system can require additional patch sets or kernel additions.

**Related Topics**

- [Oracle SQL Reserved Words and Keywords](../sqlrf/Oracle-SQL-Reserved-Words-and-Keywords.md)

**Parent topic:** [Upgrading Applications After Upgrading Oracle Database](upgrading-apps-after-oracle-db-upgrade.md)
