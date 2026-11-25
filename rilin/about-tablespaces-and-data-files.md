## About Tablespaces and Data Files

For both single-instance and cluster database environments, Oracle Database is divided into smaller logical areas of space known as tablespaces.

Each tablespace corresponds to one or more data files on the shared storage. The following table shows the tablespace names used by an Oracle RAC database and the types of data they contain.

Table 6-2 Tablespace Names Used with Oracle Real Application Clusters Databases

| Tablespace Name | Contents                                                                                                                                                                                                                                                                                                   |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SYSAUX`        | An auxiliary system tablespace that contains the `DRSYS` (contains data for Oracle Text), `CWMLITE` (contains the OLAP schemas), `XDB` (for XML features), `ODM` (for Oracle Data Mining), `INDEX` and `EXAMPLE` schemas.                                                                                  |
| `SYSTEM`        | Consists of the data dictionary, including definitions of tables, views, and stored procedures needed by the database. Oracle Database automatically maintains information in this tablespace.                                                                                                             |
| `TEMP`          | Contains temporary tables and indexes created during SQL statement processing. You may need to expand this tablespace if you run a SQL statement that involves significant sorting, such as `ANALYZE COMPUTE STATISTICS` on a very large table, or the constructs `GROUP BY,` `ORDER` `BY`, or `DISTINCT`. |
| `UNDOTBS``n`    | Contains undo tablespaces for each instance that DBCA creates for automatic undo management.                                                                                                                                                                                                               |
| `USERS`         | Consists of application data. As you create and enter data into tables, Oracle Database fills this space with your data.                                                                                                                                                                                   |

You cannot alter these tablespace names when using the preconfigured database configuration option from OUI. However, you can change the names of the tablespaces if you use the advanced database creation method.

As mentioned, each tablespace has one or more data files on shared file systems. The data file names created by the preconfigured database configuration options vary by storage type such as Oracle ASM, or a cluster file system.

**Parent topic:** [Database Components Created Using Database Configuration Assistant](database-components-created-using-database-configuration-assistant.md)
