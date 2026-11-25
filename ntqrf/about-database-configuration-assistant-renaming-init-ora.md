When you create a database using Oracle Database Configuration Assistant (Oracle DBCA), a Server Parameter File (SPFILE) is created from the initialization parameter file, and the initialization parameter file is renamed.

Oracle does not recognize the renamed file as an initialization parameter file, and it is not used after the instance is started.

If you want to modify an instance created with Oracle DBCA after it starts, you must use the`ALTER SYSTEM` statement. You cannot change the Server Parameter File itself, because it is a binary file that cannot be browsed or edited using a text editor. The location of the newly-created Server Parameter File is `ORACLE_HOME``\database`. The Server Parameter File file name is `spfile``SID``.ora`.

**See Also:**

[Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** [Overview of Initialization Parameter File](initialization-parameter-file-overview.md)
