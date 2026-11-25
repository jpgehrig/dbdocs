## 3.54 ALL_SCHEDULER_NOTIFICATIONS

`ALL_SCHEDULER_NOTIFICATIONS` displays information about the E-mail notifications for the jobs accessible to the current user.

### Related Views

- `DBA_SCHEDULER_NOTIFICATIONS` displays information about the E-mail notifications for all jobs in the database.

- `USER_SCHEDULER_NOTIFICATIONS` displays information about the E-mail notifications for the jobs owned by the current user. This view does not display the `OWNER` column.

| Column               | Datatype         | NULL       | Description                                                                                                                                                                                                                                              |
|:---------------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NOTIFICATION_OWNER` | `VARCHAR2(128)`  | `NOT NULL` | Owner of this notification                                                                                                                                                                                                                               |
| `OWNER`              | `VARCHAR2(128)`  | `NOT NULL` | Owner of the job this notification is for                                                                                                                                                                                                                |
| `JOB_NAME`           | `VARCHAR2(128)`  | `NOT NULL` | Name of the job this notification is for                                                                                                                                                                                                                 |
| `JOB_SUBNAME`        | `VARCHAR2(128)`  |            | Subname of the job this notification is for                                                                                                                                                                                                              |
| `RECIPIENT`          | `VARCHAR2(4000)` | `NOT NULL` | E-mail address to send this E-mail notification to                                                                                                                                                                                                       |
| `SENDER`             | `VARCHAR2(4000)` |            | E-mail address to send this E-mail notification from                                                                                                                                                                                                     |
| `SUBJECT`            | `VARCHAR2(4000)` |            | Subject of the notification E-mail                                                                                                                                                                                                                       |
| `BODY`               | `VARCHAR2(4000)` |            | Body of the notification E-mail                                                                                                                                                                                                                          |
| `FILTER_CONDITION`   | `VARCHAR2(4000)` |            | Filter specifying which job events to send notifications for                                                                                                                                                                                             |
| `EVENT`              | `VARCHAR2(19)`   |            | Job event to send notifications for:<br>• `JOB_STARTED`<br>• `JOB_SUCCEEDED`<br>• `JOB_FAILED`<br>• `JOB_BROKEN`<br>• `JOB_COMPLETED`<br>• `JOB_STOPPED`<br>• `JOB_SCH_LIM_REACHED`<br>• `JOB_DISABLED`<br>• `JOB_CHAIN_STALLED`<br>• `JOB_OVER_MAX_DUR` |
| `EVENT_FLAG`         | `NUMBER`         | `NOT NULL` | Event number of the job event to send notifications for                                                                                                                                                                                                  |

**See Also:**

- "[DBA_SCHEDULER_NOTIFICATIONS](DBA_SCHEDULER_NOTIFICATIONS.md)"

- "[USER_SCHEDULER_NOTIFICATIONS](USER_SCHEDULER_NOTIFICATIONS.md)"
