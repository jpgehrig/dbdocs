## 6.258 TS_PITR_CHECK

This view, created by `catpitr.sql`, provides information on any dependencies or restrictions that might prevent tablespace point-in-time recovery from proceeding.

This view applies only to the tablespace point-in-time recovery feature.

| Column            | Datatype        | NULL | Description                                                                                                                                      |
|:------------------|:----------------|:-----|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `OBJ1_OWNER`      | `VARCHAR2(128)` |      | The owner of the object preventing tablespace point-in-time recovery. See the `REASON` column for details.                                       |
| `OBJ1_NAME`       | `VARCHAR2(128)` |      | The name of the object preventing tablespace point-in-time recovery                                                                              |
| `OBJ1_SUBNAME`    | `VARCHAR2(128)` |      | Subordinate to `OBJ1_NAME`                                                                                                                       |
| `OBJ1_TYPE`       | `VARCHAR2(16)`  |      | The object type for the object preventing tablespace point-in-time recovery                                                                      |
| `TS1_NAME`        | `VARCHAR2(30)`  |      | Name of the tablespace containing the object preventing tablespace point-in-time recovery                                                        |
| `OBJ2_NAME`       | `VARCHAR2(128)` |      | The name of a second object which may be preventing tablespace point-in-time recovery. If NULL, object 1 is the only object preventing recovery. |
| `OBJ2_SUBNAME`    | `VARCHAR2(128)` |      | Subordinate to `OBJ2_NAME`                                                                                                                       |
| `OBJ2_TYPE`       | `VARCHAR2(15)`  |      | The object type for the second object (will be NULL if `OBJ2_NAME` is NULL)                                                                      |
| `OBJ2_OWNER`      | `VARCHAR2(128)` |      | The owner of the second object (will be NULL if `OBJ2_NAME` is NULL)                                                                             |
| `TS2_NAME`        | `VARCHAR2(30)`  |      | Name of the tablespace containing second object which may be preventing tablespace point-in-time recovery (-1 indicates not applicable)          |
| `CONSTRAINT_NAME` | `VARCHAR2(128)` |      | Name of the constraint                                                                                                                           |
| `REASON`          | `VARCHAR2(81)`  |      | Reason why tablespace point-in-time recovery cannot proceed                                                                                      |

**See Also:**

[Oracle Database Backup and Recovery User’s Guide](../bradv/performing-rman-tspitr.md) for more information about tablespace point-in-time recovery
