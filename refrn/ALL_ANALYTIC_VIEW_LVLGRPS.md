## 2.44 ALL_ANALYTIC_VIEW_LVLGRPS

`ALL_ANALYTIC_VIEW_LVLGRPS` describes the analytic view measure and level groups of the analytic views accessible to the current user.

### Related Views

- `DBA_ANALYTIC_VIEW_LVLGRPS` describes the analytic view measure and level groups of all analytic views in the database.

- `USER_ANALYTIC_VIEW_LVLGRPS` describes the analytic view measure and level groups of the analytic views owned by the current user. This view does not display the `OWNER` column.

| Column               | Datatype        | NULL | Description                                                                                                                                                                                                                                                                                                    |
|:---------------------|:----------------|:-----|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`              | `VARCHAR2(128)` |      | Owner of the analytic view                                                                                                                                                                                                                                                                                     |
| `ANALYTIC_VIEW_NAME` | `VARCHAR2(128)` |      | Name of the analytic view                                                                                                                                                                                                                                                                                      |
| `CACHE_TYPE`         | `VARCHAR2(128)` |      | Type of the materialized view; one of the following:<br>• `DYNAMIC`<br>• `MATERIALIZED` (the default value)                                                                                                                                                                                                    |
| `DIMENSION_ALIAS`    | `VARCHAR2(128)` |      | Alias of the attribute dimension in the group                                                                                                                                                                                                                                                                  |
| `HIER_ALIAS`         | `VARCHAR2(128)` |      | Alias of the hierarchy associated with the attribute dimension in the group                                                                                                                                                                                                                                    |
| `LEVEL_NAME`         | `VARCHAR2(128)` |      | Name of the level in the hierarchy in the group                                                                                                                                                                                                                                                                |
| `MEASURE_NAME`       | `VARCHAR2(128)` |      | Names of the measures in the group                                                                                                                                                                                                                                                                             |
| `AV_LVLGRP_ORDER`    | `NUMBER`        |      | Order of the groups in the analytic view                                                                                                                                                                                                                                                                       |
| `LEVEL_MEAS_ORDER`   | `NUMBER`        |      | Order of the levels and measures in the group                                                                                                                                                                                                                                                                  |
| `ORIGIN_CON_ID`      | `NUMBER`        |      | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |

**See Also:**

- "[DBA_ANALYTIC_VIEW_LVLGRPS](DBA_ANALYTIC_VIEW_LVLGRPS.md)"

- "[USER_ANALYTIC_VIEW_LVLGRPS](USER_ANALYTIC_VIEW_LVLGRPS.md)"
