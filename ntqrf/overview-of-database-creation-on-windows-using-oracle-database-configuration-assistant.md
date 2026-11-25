Oracle recommends you use Oracle Database Configuration Assistant (Oracle DBCA) to create a Database, because it is easier.

It offers the same interface and operates the same way on all the supported platforms, so no step-by-step procedures or screenshots are included here.

Oracle DBCA prompts for a password when the Oracle Home User is a Windows Local User Account or when a Windows Domain User Account and the password for Oracle Home User is not stored in Oracle wallet. The main purpose of Oracle Home User is to run Windows services with Windows User Account. However, this user account (Oracle Home User) has a very limited set of operating system-level privileges and must not be used for database administration. Oracle DBCA now provides an interface to create an Oracle Database service under an Oracle Home User, as specified during the process of installation. But Oracle DBCA does not provide an interface to create a new Windows user as the Oracle Home User.

The services created are not allowed to interact with the Windows desktop. ORADIM, the Windows utility tool used to create the `OracleService``SID` - Oracle Database services, is used by Oracle Database Configuration Assistant to create those services on local and remote nodes. Oracle Database Configuration Assistant now accepts a user name and a password to run the service, and also changes the ownership of the files it creates (for example, the password file) so that it can be modified by the Oracle home user.

Oracle DBCA enables you to:

- Create a database

- Configure database options in a database

- Delete a database

- Manage templates

An initialization parameter file is an ASCII text file containing parameters. Use this file to create and modify a database using command-line tools. When you create a database using Oracle DBCA, a server parameter file (SPFILE) is created from the initialization parameter file, and the initialization parameter file is renamed. Oracle does not recognize the renamed file as an initialization parameter file, and it is not used after the instance is started.

If you want to modify an instance created with Oracle DBCA after it starts, you must use `ALTER SYSTEM` statements. You cannot change the server parameter file itself, because it is a binary file that cannot be browsed or edited using a text editor. The location of the newly-created server parameter file is `ORACLE_HOME``\database`. The server parameter file name is `spfile``SID``.ora`.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

- [Oracle Database 2 Day DBA](../admqs/installing-oracle-database-creating-database.md) for instructions on using Oracle DBCA

**Parent topic:** [Postinstallation Database Creation on Windows](postinstallation-database-creation-on-windows.md)
