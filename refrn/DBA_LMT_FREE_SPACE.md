## 5.145 DBA_LMT_FREE_SPACE

`DBA_LMT_FREE_SPACE` describes the free extents in all locally managed tablespaces in the database.

| Column          | Datatype | NULL | Description                                               |
|:----------------|:---------|:-----|:----------------------------------------------------------|
| `TABLESPACE_ID` | `NUMBER` |      | Identifier number of the tablespace containing the extent |
| `FILE_ID`       | `NUMBER` |      | File identifier number of the file containing the extent  |
| `BLOCK_ID`      | `NUMBER` |      | Starting block number of the extent                       |
| `BLOCKS`        | `NUMBER` |      | Size of the extent (in Oracle blocks)                     |
