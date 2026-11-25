## 4.194 DBA_CHANGE_NOTIFICATION_REGS

`DBA_CHANGE_NOTIFICATION_REGS` describes all change notification registrations in the database.

### Related View

`USER_CHANGE_NOTIFICATION_REGS` describes the change notification registrations owned by the current user. This view does not display the `USERNAME` column.

| Column              | Datatype        | NULL | Description                                                                                                                 |
|:--------------------|:----------------|:-----|:----------------------------------------------------------------------------------------------------------------------------|
| `USERNAME`          | `VARCHAR2(31)`  |      | For invoker's rights units, the user creating the registration<br>For definer's rights units, the owner of the registration |
| `REGID`             | `NUMBER`        |      | Internal registration ID                                                                                                    |
| `REGFLAGS`          | `NUMBER`        |      | Registration flags                                                                                                          |
| `CALLBACK`          | `VARCHAR2(256)` |      | Notification callback                                                                                                       |
| `OPERATIONS_FILTER` | `NUMBER`        |      | Operations filter (if specified)                                                                                            |
| `CHANGELAG`         | `NUMBER`        |      | Transaction lag between notifications (if specified)                                                                        |
| `TIMEOUT`           | `NUMBER`        |      | Registration timeout (if specified)                                                                                         |
| `TABLE_NAME`        | `VARCHAR2(63)`  |      | Name of the registered table                                                                                                |

**See Also:**

"[USER_CHANGE_NOTIFICATION_REGS](USER_CHANGE_NOTIFICATION_REGS.md)"
