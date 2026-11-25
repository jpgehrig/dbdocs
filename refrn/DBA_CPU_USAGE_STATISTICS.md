## 4.223 DBA_CPU_USAGE_STATISTICS

`DBA_CPU_USAGE_STATISTICS` displays database CPU usage statistics.

| Column             | Datatype       | NULL       | Description                         |
|:-------------------|:---------------|:-----------|:------------------------------------|
| `DBID`             | `NUMBER`       | `NOT NULL` | Database ID                         |
| `VERSION`          | `VARCHAR2(17)` | `NOT NULL` | Database version                    |
| `TIMESTAMP`        | `DATE`         | `NOT NULL` | Time at which the CPU usage changed |
| `CPU_COUNT`        | `NUMBER`       |            | CPU count of the database           |
| `CPU_CORE_COUNT`   | `NUMBER`       |            | CPU core count of the database      |
| `CPU_SOCKET_COUNT` | `NUMBER`       |            | CPU socket count of the database    |
