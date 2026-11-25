## 2.34 ALL_ANALYTIC_VIEW_HIER_CLS_AE

`ALL_ANALYTIC_VIEW_HIER_CLS_AE` describes the classifications of the hierarchies in the analytic views (across all editions) accessible to the current user.

### Related Views

- `DBA_ANALYTIC_VIEW_HIER_CLS_AE` describes the classifications of the hierarchies in all analytic views (across all editions) in the database.

- `USER_ANALYTIC_VIEW_HIER_CLS_AE` describes the classifications of the hierarchies in the analytic views (across all editions) owned by the current user. This view does not display the `OWNER` column.

| Column               | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:---------------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`              | `VARCHAR2(128)` | `NOT NULL` | Owner of the hierarchy                                                                                                                                                                                                                                                                                         |
| `ANALYTIC_VIEW_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the analytic view                                                                                                                                                                                                                                                                                      |
| `DIMENSION_ALIAS`    | `VARCHAR2(128)` |            | Alias of the attribute dimension in the analytic view                                                                                                                                                                                                                                                          |
| `HIER_ALIAS`         | `VARCHAR2(128)` |            | Alias of the hierarchy in the attribute dimension in the analytic view                                                                                                                                                                                                                                         |
| `CLASSIFICATION`     | `VARCHAR2(128)` |            | Classification associated with the hierarchy                                                                                                                                                                                                                                                                   |
| `VALUE`              | `CLOB`          |            | Value of the classification, or NULL if not specified                                                                                                                                                                                                                                                          |
| `LANGUAGE`           | `VARCHAR2(64)`  |            | `NLS_LANGUAGE` value associated with the classification, or NULL if not specified                                                                                                                                                                                                                              |
| `ORDER_NUM`          | `NUMBER`        | `NOT NULL` | Order of the classification in the list of classifications associated with the hierarchy                                                                                                                                                                                                                       |
| `ORIGIN_CON_ID`      | `NUMBER`        |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |
| `EDITION_NAME`       | `VARCHAR2(128)` |            | Name of the application edition where the analytic view is defined                                                                                                                                                                                                                                             |

**Note:**

This view is available starting with Oracle Database 19c, Release Update 19.13.

**See Also:**

- "[DBA_ANALYTIC_VIEW_HIER_CLS_AE](DBA_ANALYTIC_VIEW_HIER_CLS_AE.md)"

- "[USER_ANALYTIC_VIEW_HIER_CLS_AE](USER_ANALYTIC_VIEW_HIER_CLS_AE.md)"
