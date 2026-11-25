## 5.361 DBA_SQL_QUARANTINE

`DBA_SQL_QUARANTINE` displays information about SQL Quarantine configurations.

Each row in this view represents a quarantine configuration for a SQL plan.

| Column            | Datatype         | NULL       | Description                                                                                                                                                                                     |
|:------------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SIGNATURE`       | `NUMBER`         | `NOT NULL` | Unique SQL identifier generated from normalized SQL text                                                                                                                                        |
| `NAME`            | `VARCHAR2(128)`  | `NOT NULL` | Unique plan identifier in string form as a search key                                                                                                                                           |
| `SQL_TEXT`        | `CLOB`           | `NOT NULL` | Un-normalized SQL text                                                                                                                                                                          |
| `PLAN_HASH_VALUE` | `NUMBER`         |            | Unique plan identifier in numeric form as a search key                                                                                                                                          |
| `CPU_TIME`        | `VARCHAR2(4000)` |            | CPU time threshold (in seconds)                                                                                                                                                                 |
| `IO_MEGABYTES`    | `VARCHAR2(4000)` |            | I/O threshold (in megabytes)                                                                                                                                                                    |
| `IO_REQUESTS`     | `VARCHAR2(4000)` |            | Physical I/O threshold (number of physical I/O requests)                                                                                                                                        |
| `ELAPSED_TIME`    | `VARCHAR2(4000)` |            | Elapsed time threshold (in seconds)                                                                                                                                                             |
| `IO_LOGICAL`      | `VARCHAR2(4000)` |            | Logical I/O threshold (number of logical I/O requests)                                                                                                                                          |
| `CREATOR`         | `VARCHAR2(128)`  |            | User who created the quarantine configuration                                                                                                                                                   |
| `ORIGIN`          | `VARCHAR2(16)`   |            | Method by which the quarantine configuration was created. The only possible value is `RESOURCE-MANAGER`, which indicates that the quarantine configuration was created by the Resource Manager. |
| `DESCRIPTION`     | `VARCHAR2(500)`  |            | Text description                                                                                                                                                                                |
| `CREATED`         | `TIMESTAMP(6)`   | `NOT NULL` | Time at which the quarantine configuration was created                                                                                                                                          |
| `LAST_EXECUTED`   | `TIMESTAMP(6)`   |            | Time at which the quarantine configuration was last used                                                                                                                                        |
| `ENABLED`         | `VARCHAR2(3)`    |            | Indicates whether the quarantine configuration is enabled (`YES`) or disabled (`NO`)                                                                                                            |
| `AUTOPURGE`       | `VARCHAR2(3)`    |            | Indicates whether the quarantine configuration is auto-purged (`YES`) or not (`NO`)                                                                                                             |

**Note:**

This view is available starting with Oracle Database 19c.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/query-optimizer-concepts.md) for more information about quarantined SQL plans
