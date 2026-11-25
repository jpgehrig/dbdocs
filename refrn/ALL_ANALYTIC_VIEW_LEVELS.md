## 2.40 ALL_ANALYTIC_VIEW_LEVELS

`ALL_ANALYTIC_VIEW_LEVELS` describes the levels in the hierarchies in the analytic views accessible to the current user.

### Related Views

- `DBA_ANALYTIC_VIEW_LEVELS` describes the levels in the hierarchies in all analytic views in the database.

- `USER_ANALYTIC_VIEW_LEVELS` describes the levels in the hierarchies in the analytic views owned by the current user. This view does not display the `OWNER` column.

| Column               | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:---------------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`              | `VARCHAR2(128)` | `NOT NULL` | Owner of the analytic view                                                                                                                                                                                                                                                                                     |
| `ANALYTIC_VIEW_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the analytic view                                                                                                                                                                                                                                                                                      |
| `DIMENSION_ALIAS`    | `VARCHAR2(128)` |            | Alias of the attribute dimension in the analytic view                                                                                                                                                                                                                                                          |
| `HIER_ALIAS`         | `VARCHAR2(128)` |            | Alias of the hierarchy in the attribute dimension in the analytic view                                                                                                                                                                                                                                         |
| `LEVEL_NAME`         | `VARCHAR2(128)` | `NOT NULL` | Name of the level within the attribute dimension in the analytic view                                                                                                                                                                                                                                          |
| `ORDER_NUM`          | `NUMBER`        | `NOT NULL` | Order number of the level in the list of levels in the analytic view hierarchy                                                                                                                                                                                                                                 |
| `ORIGIN_CON_ID`      | `NUMBER`        |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |

**See Also:**

- "[DBA_ANALYTIC_VIEW_LEVELS](DBA_ANALYTIC_VIEW_LEVELS.md)"

- "[USER_ANALYTIC_VIEW_LEVELS](USER_ANALYTIC_VIEW_LEVELS.md)"
