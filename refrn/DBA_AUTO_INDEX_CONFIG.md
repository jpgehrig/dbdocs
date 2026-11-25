## 4.165 DBA_AUTO_INDEX_CONFIG

`DBA_AUTO_INDEX_CONFIG` displays the current configuration parameter settings for automatic indexing.

You can set automatic indexing configuration parameters by using the `DBMS_AUTO_INDEX.CONFIGURE` procedure.

| Column            | Datatype         | NULL       | Description                                         |
|:------------------|:-----------------|:-----------|:----------------------------------------------------|
| `PARAMETER_NAME`  | `VARCHAR2(128)`  | `NOT NULL` | Name of the configuration parameter                 |
| `PARAMETER_VALUE` | `VARCHAR2(4000)` |            | Value of the configuration parameter                |
| `LAST_MODIFIED`   | `TIMESTAMP(6)`   |            | Time at which the parameter value was last modified |
| `MODIFIED_BY`     | `VARCHAR2(128)`  |            | User who last modified the parameter value          |

**Note:**

This view is available starting with Oracle Database 19c.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_AUTO_INDEX.md) for more information about the `DBMS_AUTO_INDEX.CONFIGURE` procedure
