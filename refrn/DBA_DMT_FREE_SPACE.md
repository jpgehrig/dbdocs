## 4.268 DBA_DMT_FREE_SPACE

`DBA_DMT_FREE_SPACE` describes the free extents in all dictionary managed tablespaces in the database.

| Column          | Datatype | NULL       | Description                                               |
|:----------------|:---------|:-----------|:----------------------------------------------------------|
| `TABLESPACE_ID` | `NUMBER` | `NOT NULL` | Identifier number of the tablespace containing the extent |
| `FILE_ID`       | `NUMBER` | `NOT NULL` | File identifier number of the file containing the extent  |
| `BLOCK_ID`      | `NUMBER` | `NOT NULL` | Starting block number of the extent                       |
| `BLOCKS`        | `NUMBER` | `NOT NULL` | Size of the extent (in Oracle blocks)                     |
