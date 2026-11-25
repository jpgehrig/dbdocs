## 4.44 DBA_ADVISOR_SQLW_TABLES

`DBA_ADVISOR_SQLW_TABLES` displays cross references between the workload statements and the tables referenced in the statement.

### Related View

`USER_ADVISOR_SQLW_TABLES` displays cross references between the workload statements and the tables referenced in the statement. This view does not display the `OWNER` column.

| Column          | Datatype        | NULL | Description                                     |
|:----------------|:----------------|:-----|:------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)` |      | Owner of the workload object                    |
| `WORKLOAD_ID`   | `NUMBER`        |      | Unique identifier number of the workload object |
| `WORKLOAD_NAME` | `VARCHAR2(128)` |      | Name of the workload                            |
| `SQL_ID`        | `NUMBER`        |      | Identifier of the statement                     |
| `TABLE_OWNER`   | `VARCHAR2(128)` |      | Owner of the table                              |
| `TABLE_NAME`    | `VARCHAR2(128)` |      | Name of the table                               |

**See Also:**

"[USER_ADVISOR_SQLW_TABLES](USER_ADVISOR_SQLW_TABLES.md)"
