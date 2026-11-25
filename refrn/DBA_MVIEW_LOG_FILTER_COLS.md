## 5.194 DBA_MVIEW_LOG_FILTER_COLS

`DBA_MVIEW_LOG_FILTER_COLS` displays all columns (excluding primary key columns) being logged in the materialized view logs.

| Column        | Datatype        | NULL | Description                            |
|:--------------|:----------------|:-----|:---------------------------------------|
| `OWNER`       | `VARCHAR2(128)` |      | Owner of the master table being logged |
| `NAME`        | `VARCHAR2(128)` |      | Name of the master table being logged  |
| `COLUMN_NAME` | `VARCHAR2(128)` |      | Column being logged                    |
