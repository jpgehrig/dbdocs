You must choose a location for Oracle home for the new release of Oracle Database that is separate from the Oracle home of your current release.

Using separate installation locations enables you to keep your existing Oracle software installed along with the new Oracle software. By using separate installation locations, you can test the upgrade process on a test database before replacing your production environment entirely.

When you upgrade a database, whether the database is a non-CDB or a CDB, a new location is needed to install the new Oracle home.

If you are upgrading a PDB by using an unplug/plug upgrade, then the target CDB into which you plug the PDB is the location for the PDB. There is no need to choose a new location for installing the target Oracle homes, because the target CDB already has its Oracle home.

**Parent topic:** [Installing Oracle Software in a New Oracle Home](installing-oracle-software-in-a-new-oracle-home.md)
