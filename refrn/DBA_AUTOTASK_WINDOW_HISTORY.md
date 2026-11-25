## 4.178 DBA_AUTOTASK_WINDOW_HISTORY

`DBA_AUTOTASK_WINDOW_HISTORY` displays historical information for automated maintenance task windows.

| Column              | Datatype                      | NULL | Description                    |
|:--------------------|:------------------------------|:-----|:-------------------------------|
| `WINDOW_NAME`       | `VARCHAR2(261)`               |      | Name of the maintenance window |
| `WINDOW_START_TIME` | `TIMESTAMP(6) WITH TIME ZONE` |      | Window start time              |
| `WINDOW_END_TIME`   | `TIMESTAMP(6) WITH TIME ZONE` |      | Window end time                |
