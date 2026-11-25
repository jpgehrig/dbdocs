## 4.171 DBA_AUTOTASK_CLIENT_JOB

`DBA_AUTOTASK_CLIENT_JOB` displays information about currently running Scheduler jobs created for automated maintenance tasks.

`DBA_AUTOTASK_CLIENT_JOB` provides information about some objects targeted by those jobs, as well as some additional statistics from previous instantiations of the same task. Some of this additional data is taken from generic Scheduler views.

| Column                 | Datatype        | NULL       | Description                                                                                                                                                                         |
|:-----------------------|:----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CLIENT_NAME`          | `VARCHAR2(64)`  |            | Name of the client                                                                                                                                                                  |
| `JOB_NAME`             | `VARCHAR2(65)`  |            | Name of the job                                                                                                                                                                     |
| `JOB_SCHEDULER_STATUS` | `VARCHAR2(15)`  |            | Job status:<br>• `DISABLED`<br>• `RETRY SCHEDULED`<br>• `SCHEDULED`<br>• `RUNNING`<br>• `COMPLETED`<br>• `BROKEN`<br>• `FAILED`<br>• `REMOTE`<br>• `SUCCEEDED`<br>• `CHAIN_STALLED` |
| `TASK_NAME`            | `VARCHAR2(64)`  |            | Name of the task being performed                                                                                                                                                    |
| `TASK_TARGET_TYPE`     | `VARCHAR2(64)`  |            | Type of the target being processed                                                                                                                                                  |
| `TASK_TARGET_NAME`     | `VARCHAR2(513)` | `NOT NULL` | Name of the target                                                                                                                                                                  |
| `TASK_PRIORITY`        | `VARCHAR2(7)`   |            | Priority of the task:<br>• `URGENT`<br>• `HIGH`<br>• `MEDIUM`<br>• `LOW`                                                                                                            |
| `TASK_OPERATION`       | `VARCHAR2(64)`  |            | Operation performed on the object                                                                                                                                                   |
