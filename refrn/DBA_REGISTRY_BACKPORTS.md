## 5.278 DBA_REGISTRY_BACKPORTS

`DBA_REGISTRY_BACKPORTS` displays backported bug fixes that were applied to the database. This view displays only bug fixes that changed the data dictionary of the database.

| Column          | Datatype       | NULL       | Description                                                                                                                                                   |
|:----------------|:---------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BUGNO`         | `NUMBER`       | `NOT NULL` | Bug number                                                                                                                                                    |
| `VERSION_FULL`  | `VARCHAR2(30)` | `NOT NULL` | Component full version                                                                                                                                        |
| `COMP_ID`       | `VARCHAR2(30)` | `NOT NULL` | Component identifier                                                                                                                                          |
| `NAMESPACE`     | `VARCHAR2(30)` | `NOT NULL` | Component namespace                                                                                                                                           |
| `BACKPORT_TYPE` | `VARCHAR2(30)` | `NOT NULL` | Type of backported bug fix<br>The value of this columns is always `DICTIONARY`, which indicates that the bug fix changed the data dictionary of the database. |
| `BACKPORT_TIME` | `TIMESTAMP(6)` | `NOT NULL` | Date and time at which the backported bug fix was applied                                                                                                     |

**Note:**

This view is available starting with Oracle Database 19c.
