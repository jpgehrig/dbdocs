## 2.212 ALL_HIERARCHIES

`ALL_HIERARCHIES` describes the hierarchies accessible to the current user.

### Related Views

- `DBA_HIERARCHIES` describes all hierarchies in the database.

- `USER_HIERARCHIES` describes the hierarchies owned by the current user. This view does not display the `OWNER` column.

| Column            | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:------------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`           | `VARCHAR2(128)` | `NOT NULL` | Owner of the hierarchy                                                                                                                                                                                                                                                                                         |
| `HIER_NAME`       | `VARCHAR2(128)` | `NOT NULL` | Name of the hierarchy                                                                                                                                                                                                                                                                                          |
| `DIMENSION_OWNER` | `VARCHAR2(128)` | `NOT NULL` | Owner of the attribute dimension used by the hierarchy                                                                                                                                                                                                                                                         |
| `DIMENSION_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of the attribute dimension used by the hierarchy                                                                                                                                                                                                                                                          |
| `PARENT_ATTR`     | `VARCHAR2`      |            | The value of this column is always NULL                                                                                                                                                                                                                                                                        |
| `COMPILE_STATE`   | `VARCHAR2(7)`   |            | Compile status of the hierarchy:<br>• `VALID`<br>• `INVALID`                                                                                                                                                                                                                                                   |
| `ORIGIN_CON_ID`   | `NUMBER`        |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |

**See Also:**

- "[DBA_HIERARCHIES](DBA_HIERARCHIES.md)"

- "[USER_HIERARCHIES](USER_HIERARCHIES.md)"
