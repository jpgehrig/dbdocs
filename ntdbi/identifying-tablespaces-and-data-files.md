## Identifying Tablespaces and Data Files

An Oracle Database is divided into smaller logical areas of space known as tablespaces.

Each tablespace corresponds to one or more physical data files. Data files contain the contents of logical database structures such as tables and indexes. A data file can be associated with only one tablespace and database.

The following table lists the tablespaces and data files in the Oracle Database. By default, the data files are located in the `ORACLE_BASE``\oradata\``DB_NAME` directory:

Table 9-2 Tablespaces and Data Files

| Tablespace | Data File       | Description                                                                                                                                                                                                                                                 |
|:-----------|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `EXAMPLE`  | `EXAMPLE01.DBF` | Stores the Sample Schemas, if you included them.                                                                                                                                                                                                            |
| `SYSAUX`   | `SYSAUX01.DBF`  | Serves as an auxiliary tablespace to the `SYSTEM` tablespace. Some products and options that previously used the `SYSTEM` tablespace now use the `SYSAUX` tablespace to reduce the load on the `SYSTEM` tablespace.                                         |
| `SYSTEM`   | `SYSTEM01.DBF`  | Stores the data dictionary, including definitions of tables, views, and stored procedures needed by the Oracle Database. Information in this area is maintained automatically.                                                                              |
| `TEMP`     | `TEMP01.DBF`    | Stores temporary tables and indexes created during the processing of your SQL statement. If you run a SQL statement that involves a lot of sorting, such as the constructs `GROUP` `BY`, `ORDER` `BY`, or `DISTINCT`, then you must expand this tablespace. |
| `UNDOTBS`  | `UNDOTBS01.DBF` | Stores undo information. This contains one or more undo segments that maintain transaction history that is used to roll back, or undo, changes to the database.<br>All starter databases are configured to run in automatic undo management mode.           |
| `USERS`    | `USERS01.DBF`   | Stores database objects created by database users.                                                                                                                                                                                                          |

**See Also:**

- [Oracle Database Concepts](../cncpt/logical-storage-structures.md)

- [Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

- [Oracle Database 2 Day DBA](../admqs/managing-database-storage-structures.md)

**Parent topic:** [Getting Started with Oracle Database](getting-started-with-oracle-database.md)
