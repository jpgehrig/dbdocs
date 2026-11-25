## Choose a New Location for Oracle Home when Upgrading

When you upgrade or patch the database, you must install the new Oracle home in a new location (an out-of-place upgrade or patch).

AutoUpgrade performs out-of-place upgrades and patches: This means that the upgrade or the patched Oracle home is in a new Oracle home. Previously, with an in-place upgrade or patch, the upgrade or patch was applied to the existing Oracle home. Using separate installation locations enables you to keep your existing Oracle software installed along with the new Oracle software. By using separate installation locations, you can test the upgrade or patch process in the out-of-place Oracle home database before replacing your production environment entirely.

When you upgrade a database, whether the database is a non-CDB or a CDB, the upgrade must be an out-of-place upgrade, which means that a new location is needed to install the new Oracle home.

**Related Topics**

- [How to speed up your database and GI patching](https://mikedietrichde.com/2022/05/09/how-to-speed-up-your-database-and-gi-patching/)

**Parent topic:** [Tasks to Prepare for Oracle Database Upgrades](tasks-to-prepare-for-oracle-database-upgrades.md)
