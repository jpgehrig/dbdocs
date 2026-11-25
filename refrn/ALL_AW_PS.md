## 2.105 ALL_AW_PS

`ALL_AW_PS` describes the page spaces in the analytic workspaces accessible to the current user.

### Related Views

- `DBA_AW_PS` describes the page spaces in all analytic workspaces in the database.

- `USER_AW_PS` describes the page spaces in the analytic workspaces owned by the current user. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL       | Description                                    |
|:--------------|:----------------|:-----------|:-----------------------------------------------|
| `OWNER`       | `VARCHAR2(128)` | `NOT NULL` | Owner of the analytic workspace                |
| `AW_NUMBER`   | `NUMBER`        | `NOT NULL` | Number of the analytic workspace               |
| `AW_NAME`     | `VARCHAR2(128)` |            | Name of the analytic workspace                 |
| `PSNUMBER`    | `NUMBER(10)`    |            | Number of the page space                       |
| `GENERATIONS` | `NUMBER`        |            | Number of active generations in the page space |
| `MAXPAGES`    | `NUMBER`        |            | Maximum pages allocated in the page space      |

**See Also:**

- "[DBA_AW_PS](DBA_AW_PS.md)"

- "[USER_AW_PS](USER_AW_PS.md)"

- [Oracle OLAP User’s Guide](../olaug/overview.md) for more information about the OLAP option for Oracle Database
