Learn how to create a new database manually. As part of its database software files, Oracle Database provides a sample initialization parameter file, which can you can edit to suit your needs.

You can choose to create database creation scripts using Oracle Database Configuration Assistant.

The following are the types of Database creation tasks:

- Copy an existing database and delete the old database.

- Copy an existing database and keep the old database.

- Create a new database when no database exists on your system.

### Manual Database Creation Tasks

Use Manual Database Creation Tasks to understand the manual tasks involved in creating a new database for each of these database creation categories. Each step is explained in detail in the following subsections.

Table 4-1 Manual Database Creation Tasks

| Task                                                                                                                | Copy existing database and delete old database | Copy existing database and keep old database | Create new database when no database exists on system |
|:--------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------|:---------------------------------------------|:------------------------------------------------------|
| [About Exporting an Existing Database](about-exporting-an-existing-database.md)                                     | Yes                                            | Note 1                                       | Not applicable                                        |
| [Deleting Database Files](deleting-database-files.md)                                                               | Yes                                            | No                                           | Not applicable                                        |
| [Modifying the Initialization Parameter File](modifying-the-initialization-parameter-file.md)                       | Yes                                            | Yes                                          | Yes                                                   |
| [Starting an Oracle Database Instance](starting-an-oracle-database-instance.md)                                     | Yes                                            | Yes                                          | Yes                                                   |
| [About Creating and Starting an Oracle Database Service](about-creating-and-starting-an-oracle-database-service.md) | No                                             | Yes                                          | Yes                                                   |
| [Adding the CREATE DATABASE Statement in a Script](putting-the-create-database-statement-in-a-script.md)            | Yes                                            | Yes                                          | Yes                                                   |
| [Running the CREATE DATABASE Script](running-the-create-database-script.md)                                         | Yes                                            | Yes                                          | Yes                                                   |
| [About Importing a Database](about-importing-a-database.md)                                                         | Yes                                            | Note 2                                       | Not applicable                                        |
| [Updating ORACLE_SID in the Registry](updating-oracle-sid-in-the-registry.md)                                       | No                                             | Only if you change the default `SID`         | Yes                                                   |
| [Backing Up the New Database](backing-up-the-new-database.md)                                                       | Yes                                            | Yes                                          | Yes                                                   |

**Note:**

If you copy data from an existing database to the new database, select Yes; otherwise, No. Also, if you import tables and other objects from the existing database, select Yes; otherwise, No.

An example in the following sections demonstrates how to create a database. In this example, the existing database is the starter database with a `SID` of `orcl` located in directory `C`:\\app\\username\\`oradata\orcl`. Copy `orcl` to a new database with a database name and `SID` of `prod` located in the directory `C:`\app\username`\oradata\prod`. Then, delete the starter database `orcl`.

- [About Exporting an Existing Database](about-exporting-an-existing-database.md)
  You are required to export an existing database only if you intend to copy its contents to a new database.
- [Deleting Database Files](deleting-database-files.md)
  Deleting database files is required only when you copy an existing database to a new database to replace the old database.
- [Modifying the Initialization Parameter File](modifying-the-initialization-parameter-file.md)
  Describes how to modify the initialization parameter file.
- [About Creating and Starting an Oracle Database Service](about-creating-and-starting-an-oracle-database-service.md)
  Learn how to create and start an Oracle Database service.
- [Starting an Oracle Database Instance](starting-an-oracle-database-instance.md)
  Learn how to start an instance without mounting a database.
- [Adding the CREATE DATABASE Statement in a Script](putting-the-create-database-statement-in-a-script.md)
  The `CREATE DATABASE` statement is a SQL statement that creates the database.
- [Running the CREATE DATABASE Script](running-the-create-database-script.md)
  Use this procedure to run the CREATE DATABASE script.
- [About Importing a Database](about-importing-a-database.md)
  Learn how to use Data Pump Import or Import.
- [Updating ORACLE_SID in the Registry](updating-oracle-sid-in-the-registry.md)
  If this is the first database on your computer or if you intend to make the new database the default database, then you must make a change in the registry.
- [Creating the ORACLE_SID Parameter](creating-the-oracle-sid-parameter.md)
  If you do not yet have the parameter `ORACLE_SID`, because this is the first database on your system, then you must create it.
- [Backing Up the New Database](backing-up-the-new-database.md)
  Use this procedure to prevent data loss.

**Parent topic:** [Postinstallation Database Creation on Windows](postinstallation-database-creation-on-windows.md)
