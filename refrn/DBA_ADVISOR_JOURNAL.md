## 4.27 DBA_ADVISOR_JOURNAL

`DBA_ADVISOR_JOURNAL` displays the journal entries for all tasks in the database.

### Related View

`USER_ADVISOR_JOURNAL` displays the journal entries for the tasks owned by the current user. This view does not display the `OWNER` column.

| Column               | Datatype         | NULL       | Description                                                                                                         |
|:---------------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------|
| `OWNER`              | `VARCHAR2(128)`  |            | Owner of the task                                                                                                   |
| `TASK_ID`            | `NUMBER`         | `NOT NULL` | Identifier of the task or workload object                                                                           |
| `TASK_NAME`          | `VARCHAR2(128)`  |            | Name of the task or workload object                                                                                 |
| `EXECUTION_NAME`     | `VARCHAR2(128)`  |            | The name of the task execution with which this entry (row) is associated                                            |
| `JOURNAL_ENTRY_SEQ`  | `NUMBER`         | `NOT NULL` | Sequence number of the journal entry (unique for each task). This sequence number is used to order the data.        |
| `JOURNAL_ENTRY_TYPE` | `VARCHAR2(12)`   |            | Type of the task:<br>• `FATAL`<br>• `ERROR`<br>• `WARNING`<br>• `INFORMATION`<br>• `INFORMATION[2 | 3 | 4 | 5 | 6]` |
| `JOURNAL_ENTRY`      | `VARCHAR2(4000)` |            | Entry in the journal                                                                                                |

**See Also:**

"[USER_ADVISOR_JOURNAL](USER_ADVISOR_JOURNAL.md)"
