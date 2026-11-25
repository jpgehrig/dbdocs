## 2.106 ALL_AWS

`ALL_AWS` describes the analytic workspaces accessible to the current user.

### Related Views

- `DBA_AWS` describes all analytic workspaces in the database.

- `USER_AWS` describes the analytic workspaces owned by the current user. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL       | Description                                                                              |
|:--------------|:----------------|:-----------|:-----------------------------------------------------------------------------------------|
| `OWNER`       | `VARCHAR2(128)` | `NOT NULL` | Owner of the analytic workspace                                                          |
| `AW_NUMBER`   | `NUMBER`        | `NOT NULL` | Number of the analytic workspace                                                         |
| `AW_NAME`     | `VARCHAR2(128)` |            | Name of the analytic workspace                                                           |
| `AW_VERSION`  | `VARCHAR2(4)`   |            | Format version of the analytic workspace:<br>• `9.1`<br>• `10.1`<br>• `10.2`<br>• `11.1` |
| `PAGESPACES`  | `NUMBER`        |            | Number of pagespaces in the analytic workspace                                           |
| `GENERATIONS` | `NUMBER`        |            | Number of active generations in the analytic workspace                                   |
| `FROZEN`      | `VARCHAR2(6)`   |            | Freeze state of the analytic workspace:<br>• `Frozen`<br>• `NoThaw`                      |

**See Also:**

- "[DBA_AWS](DBA_AWS.md)"

- "[USER_AWS](USER_AWS.md)"

- [Oracle OLAP User’s Guide](../olaug/overview.md) for more information about the OLAP option for Oracle Database
