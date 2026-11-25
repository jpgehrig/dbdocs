Oracle Text enables text queries through SQL and **Pl/SQL** from most Oracle interfaces.

Oracle Text enables text queries through SQL and **Pl/SQL** from most Oracle interfaces. By installing Oracle Text with an Oracle Database server, client tools such as SQL\*Plus and Pro\*C/C++ are able to retrieve and manipulate text in Oracle Database.

Oracle Text manages textual data in concert with traditional data types in Oracle Database. When text is inserted, updated, or deleted, Oracle Text automatically manages the change.

If you install Oracle Text from the media and do not have a previous release of Oracle Text installed, then Oracle Database is already configured for use with Oracle Text if one of the following is true:

- You created the database by using Oracle Database Configuration Assistant in standalone mode, and selected the Typical database creation type.

- The database is a **starter database** that you created by using Oracle Universal Installer (OUI) and selected the Create and configure a database option in "Select Installation Option" window.

**See Also:**

- [Oracle Text Application Developer's Guide](../ccapp/migrating-oracle-text-applications.md)

- [Oracle Database Upgrade Guide](../upgrd/index.md)

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/installing-oracle-text-filtering-component.md)

### Configuring Oracle Text Using Database Configuration Assistant

To use Oracle Database Configuration Assistant to configure Oracle Database for use with Oracle Text at the time you create the database, select Oracle Text as the option to configure when prompted.

To configure the database at a later time:

1.  Start Database Configuration Assistant.

    From the Start menu, select All Programs, then select Oracle - HOMENAME, then select Configuration and Migration Tools, and then select Database Configuration Assistant.

2.  Select Configure Database Options.

3.  Select the database to modify when prompted.

4.  Select Oracle Text as the option to configure when prompted.

**Parent topic:** [Postinstallation Configuration Tasks on Windows](postinstallation-configuration-tasks-on-windows.md)
