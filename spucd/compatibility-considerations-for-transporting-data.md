When transporting data, Oracle Database computes the lowest compatibility level at which the target database must run.

You can transport a tablespace or a table from a source database to a target database having the same or higher compatibility setting using transportable tablespaces, even if the target database is on the same or a different platform. The data transport operation fails if the compatibility level of the source database is higher than the compatibility level of the target database.

The following table shows the minimum compatibility requirements of the source and target databases in various scenarios. The source and target database need not have the same compatibility setting.

Table 1-1 Minimum Compatibility Requirements

| Transport Scenario                                                                                                    | Minimum Compatibility Setting                                                                                                                                                           |                                                        |
|:----------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------|
| Source Database                                                                                                       | Target Database                                                                                                                                                                         |                                                        |
| Transporting a database using full transportable export/import                                                        | 12.0 (`COMPATIBLE` initialization parameter setting for an Oracle Database 12c or later database<br>12 (`VERSION` Data Pump export parameter setting for an 11.2.0.3 or later database) | 12.0 (`COMPATIBLE` initialization parameter setting)   |
| Transporting a tablespace between databases on the same platform using transportable tablespaces                      | 8.0 (`COMPATIBLE` initialization parameter setting)                                                                                                                                     | 8.0 (`COMPATIBLE` initialization parameter setting)    |
| Transporting a tablespace with different database block size than the target database using transportable tablespaces | 9.0 (`COMPATIBLE` initialization parameter setting)                                                                                                                                     | 9.0 (`COMPATIBLE` initialization parameter setting)    |
| Transporting a tablespace between databases on different platforms using transportable tablespaces                    | 10.0 (`COMPATIBLE` initialization parameter setting)                                                                                                                                    | 10.0 (`COMPATIBLE` initialization parameter setting)   |
| Transporting tables between databases                                                                                 | 11.2.0 (`COMPATIBLE` initialization parameter setting for an Oracle Database 12c or later database                                                                                      | 11.2.0 (`COMPATIBLE` initialization parameter setting) |

**Note:**

- When you use full transportable export/import, the source database must be an Oracle Database 11g Release 2 (11.2.0.3) or later database, and the target database must be an Oracle Database 12c or later database.

- When transporting a database from Oracle Database 11g Release 2 (11.2.0.3) or later database to Oracle Database 12c or later database, you must set the Data Pump export parameter `VERSION` to `12` or higher.

- When transporting a database from an Oracle Database 19c database to an Oracle Database 19c database, you must set the initialization parameter `COMPATIBLE` to `19.0.0` or higher.

**Parent topic:** [Transporting Databases](transporting-databases.md)
