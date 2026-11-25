## 4.345 DBA_HIGH_WATER_MARK_STATISTICS

`DBA_HIGH_WATER_MARK_STATISTICS` displays information about database high-watermark statistics.

| Column        | Datatype        | NULL       | Description                                                                    |
|:--------------|:----------------|:-----------|:-------------------------------------------------------------------------------|
| `DBID`        | `NUMBER`        | `NOT NULL` | Identifier of the database for which the high-watermark statistics are tracked |
| `NAME`        | `VARCHAR2(64)`  | `NOT NULL` | Name of the high-watermark statistic (see Table 4-1)                           |
| `VERSION`     | `VARCHAR2(17)`  | `NOT NULL` | Database version in which the high watermarks were tracked                     |
| `HIGHWATER`   | `NUMBER`        |            | Highest value of the statistic seen at sampling time                           |
| `LAST_VALUE`  | `NUMBER`        |            | Value of the statistic at the last sample time                                 |
| `DESCRIPTION` | `VARCHAR2(128)` |            | Description of the high-watermark statistics (see Table 4-1)                   |

Table 4-1 DBA_HIGH_WATER_MARK_STATISTICS Statistics

| Name              | Description                                                |
|:------------------|:-----------------------------------------------------------|
| ACTIVE_SESSIONS   | Maximum Number of Active Sessions seen in the system       |
| CPU_COUNT         | Maximum Number of CPUs                                     |
| DATAFILES         | Maximum Number of Datafiles                                |
| DB_SIZE           | Maximum Size of the Database (Bytes)                       |
| EXADATA_DISKS     | Number of physical disks                                   |
| INSTANCES         | Oracle Database instances                                  |
| PART_INDEXES      | Maximum Number of Partitions belonging to an User Index    |
| PART_TABLES       | Maximum Number of Partitions belonging to an User Table    |
| QUERY_LENGTH      | Maximum Query Length                                       |
| SEGMENT_SIZE      | Size of Largest Segment (Bytes)                            |
| SESSIONS          | Maximum Number of Concurrent Sessions seen in the database |
| SQL_NCHAR_COLUMNS | Maximum Number of SQL NCHAR Columns                        |
| TABLESPACES       | Maximum Number of Tablespaces                              |
| USER_INDEXES      | Number of User Indexes                                     |
| USER_MV           | Maximum Number of Materialized Views (User)                |
| USER_TABLES       | Number of User Tables                                      |
