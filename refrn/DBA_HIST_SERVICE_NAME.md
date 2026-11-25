## 5.46 DBA_HIST_SERVICE_NAME

`DBA_HIST_SERVICE_NAME` displays the names of the Services tracked by the Workload Repository.

This view contains information for `V$SERVICES`.

| Column              | Datatype       | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------|:---------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBID`              | `NUMBER`       | `NOT NULL` | Database ID for the snapshot                                                                                                                                                                                                                                                                                                                                                     |
| `SERVICE_NAME_HASH` | `NUMBER`       | `NOT NULL` | Hash of the service name                                                                                                                                                                                                                                                                                                                                                         |
| `SERVICE_NAME`      | `VARCHAR2(64)` | `NOT NULL` | Name of the service                                                                                                                                                                                                                                                                                                                                                              |
| `CON_DBID`          | `NUMBER`       |            | The database ID of the PDB for the sampled session                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`            | `NUMBER`       |            | The ID of the container that `CON_DBID` identifies. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[V\$SERVICES](V-SERVICES.md)"
