## 5.296 DBA_ROLLING_PARAMETERS

`DBA_ROLLING_PARAMETERS` lists the available parameters of the `DBMS_ROLLING` PL/SQL package.

| Column        | Datatype        | NULL | Description                                      |
|:--------------|:----------------|:-----|:-------------------------------------------------|
| `SCOPE`       | `VARCHAR2(128)` |      | Database unique name associated with a parameter |
| `TYPE`        | `VARCHAR2(7)`   |      | Type of parameter                                |
| `NAME`        | `VARCHAR2(32)`  |      | Name of the parameter                            |
| `DESCRIPTION` | `VARCHAR2(256)` |      | Description of the parameter                     |
| `CURVAL`      | `VARCHAR2(256)` |      | Current value of the parameter                   |
| `LSTVAL`      | `VARCHAR2(256)` |      | Prior value of the parameter                     |
| `DEFVAL`      | `VARCHAR2(256)` |      | Default value of the parameter                   |
| `MINVAL`      | `NUMBER`        |      | Minimum value of the parameter                   |
| `MAXVAL`      | `NUMBER`        |      | Maximum value of the parameter                   |

**See Also:**

- [Oracle Data Guard Concepts and Administration](../sbydb/using-DBMS_ROLLING-to-perform-rolling-upgrade.md) for more information about rolling operations.

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ROLLING.md) for more information about the `DBMS_ROLLING` package
