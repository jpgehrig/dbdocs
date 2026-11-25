## 6.125 DBA_WORKLOAD_REPLAY_SCHEDULES

`DBA_WORKLOAD_REPLAY_SCHEDULES` displays the names of replay schedules for the current replay directory.

A replay schedule defines one or multiple workload captures, and the order to start their replays. The current replay directory is set by `DBMS_WORKLOAD_REPLAY.SET_REPLAY_DIRECTORY('replay_dir')`. Each row in the view contains information about one replay schedule.

| Column          | Datatype        | NULL       | Description                                                                                                                |
|:----------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------|
| `SCHEDULE_NAME` | `VARCHAR2(128)` | `NOT NULL` | The name of a schedule to be replayed. It defines one or multiple workload captures, and the order to start their replays. |
| `DIRECTORY`     | `VARCHAR2(128)` | `NOT NULL` | Directory object name for the replay schedule name                                                                         |
| `STATUS`        | `VARCHAR2(128)` |            | `NEW` if the schedule is being created, `CURRENT` if the schedule is currently being used by a replay, otherwise `NULL`    |

**See Also:**

- "[DBA_WORKLOAD_SCHEDULE_CAPTURES](DBA_WORKLOAD_SCHEDULE_CAPTURES.md)" displays the workload captures in a replay schedule.

- "[DBA_WORKLOAD_SCHEDULE_ORDERING](DBA_WORKLOAD_SCHEDULE_ORDERING.md)" displays the order to start captures in a replay schedule.

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_REPLAY.md) for more information about the `DBMS_WORKLOAD_REPLAY` package
