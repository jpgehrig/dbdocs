## 5.202 DBA_MVREF_STATS_SYS_DEFAULTS

`DBA_MVREF_STATS_SYS_DEFAULTS` displays the system-wide defaults for the refresh history statistics properties for materialized views. These values can be altered with the `SET_SYSTEM_DEFAULTS` procedure by a database administrator.

### Related View

This view contains exactly two rows corresponding to the collection-level and retention-period properties; their initial values are `TYPICAL` and `31` respectively.

`USER_MVREF_STATS_SYS_DEFAULTS` displays the system-wide defaults for the refresh history statistics properties for materialized views accessible to the current user. These values can be altered with the `SET_SYSTEM_DEFAULTS` procedure by a database administrator.

| Column           | Datatype       | NULL | Description                                                                              |
|:-----------------|:---------------|:-----|:-----------------------------------------------------------------------------------------|
| `PARAMETER_NAME` | `CHAR(16)`     |      | Value of the `parameter_name` parameter:<br>• `COLLECTION_LEVEL`<br>• `RETENTION_PERIOD` |
| `VALUE`          | `VARCHAR2(40)` |      | The system-wide default value for the parameter                                          |

**See Also:**

"[USER_MVREF_STATS_SYS_DEFAULTS](USER_MVREF_STATS_SYS_DEFAULTS.md)"
