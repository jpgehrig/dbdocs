## Migrating From Standard Edition to Enterprise Edition of Oracle Database

Review these options to migrate to Oracle Database Enterprise Edition from Oracle Database Standard Edition

If you have Oracle Database Standard Edition at a release earlier than the new Oracle Database release, then you can change it from a Standard Edition release to Oracle Database Enterprise Edition by selecting one of the following options:

- Perform a normal upgrade procedure.

  Install Oracle Enterprise Edition software in a new Oracle home, and follow the normal upgrade procedures as described in the "Upgrading Oracle Database" chapter. The Data Dictionary for Standard Edition and Enterprise Edition configurations are the same. The difference between Standard Edition and Enterprise Edition is in the options that are available in the server executable.

- Perform an In-Place Upgrade using the same Oracle home.

  If you have a Standard Edition database at a release earlier than the new release of Oracle Database, and you want to perform an in-place upgrade using the same Oracle home, then you must first upgrade the Standard Edition Database. After you complete the upgrade, use the procedure described here to install Oracle Database Enterprise Edition software and to move to Oracle Database Enterprise Edition.

**Caution:**

Performing this procedure deinstalls the Oracle Standard Edition software. It results in deleting database files that exist under the Oracle home, and under the Fast Recovery Area (FRA). Back up database files under the current Oracle home before you begin this procedure.

1.  Ensure that the release number of your Oracle Standard Edition server software is the same release as your Oracle Enterprise Edition server software.

2.  Shut down your database.

3.  If your operating system is Windows, then stop all Oracle services, including the `OracleService``SID` Oracle service, where `SID` is the instance name.

4.  Back up all database files under the current Oracle home that you must keep.

5.  Deinstall the Standard Edition server software.

    **Caution:**

    This step deletes all existing database files that reside under the Oracle home.

    Run the deinstallation tool from the Oracle home. The deinstallation tool is available as a separate command (`deinstall`) under the Oracle home directory after installation. It is located under `ORACLE_HOME/deinstall`.

    To deinstall an Oracle home on Microsoft Windows, use the following syntax:

        setup.exe –deinstall –home path_of_Oracle_home_to_be_deinstalled

    To deinstall an Oracle home on Linux and Unix, use the following syntax:

        $ ./runInstaller –deinstall –home path_of_Oracle_home_to_be_deinstalled

    **Note:**

    The deinstallation tool is integrated with the database installation media. You can run the deinstallation tool using `runInstaller` on Linux and Unix, or by using `setup.exe` on Windows with the `-deinstall` and `-home` options from the base directory of the Oracle Database, Oracle Database Client, or Oracle Grid Infrastructure installation media.

6.  Install Oracle Enterprise Edition server software.

    Select the same Oracle home that was used for the Standard Edition that you uninstalled, or select a new Oracle home. During the installation, be sure to select Enterprise Edition. When prompted, choose Software Only.

7.  If you have an existing database, then set your `ORACLE_SID` to this preexisting database.

    If your existing database is on Microsoft Windows, then you must recreate the database service by using the `ORADIM` utility.

8.  Start up your database.

**Related Topics**

- [Upgrading Oracle Database](upgrading-oracle-database-parallel-upgrade-utiility-replay-upgrade.md)

**Parent topic:** [About Converting Databases During Upgrades](converting-databases-upgrades.md)
