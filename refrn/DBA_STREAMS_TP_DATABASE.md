## 6.15 DBA_STREAMS_TP_DATABASE

`DBA_STREAMS_TP_DATABASE` displays information about each database that contains Replication components.

| Column                   | Datatype        | NULL       | Description                             |
|:-------------------------|:----------------|:-----------|:----------------------------------------|
| `GLOBAL_NAME`            | `VARCHAR2(128)` | `NOT NULL` | Global name of the database             |
| `LAST_QUERIED`           | `DATE`          | `NOT NULL` | Time that the database was last queried |
| `VERSION`                | `VARCHAR2(128)` |            | Database version of the database        |
| `COMPATIBILITY`          | `VARCHAR2(128)` |            | Compatible setting of the database      |
| `MANAGEMENT_PACK_ACCESS` | `VARCHAR2(128)` |            | Management pack access of the database  |
