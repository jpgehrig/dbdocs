## 5.295 DBA_ROLLING_EVENTS

`DBA_ROLLING_EVENTS` lists all the events reported from the `DBMS_ROLLING` PL/SQL package.

| Column       | Datatype        | NULL | Description                                            |
|:-------------|:----------------|:-----|:-------------------------------------------------------|
| `EVENTID`    | `NUMBER`        |      | Event identifier which identifies event order          |
| `EVENT_TIME` | `TIMESTAMP(6)`  |      | Time associated with the event                         |
| `TYPE`       | `VARCHAR2(7)`   |      | Type of event: `INFO`, `NOTICE`, `WARNING`, or `ERROR` |
| `MESSAGE`    | `VARCHAR2(256)` |      | Text describing the event details                      |
| `STATUS`     | `NUMBER`        |      | Status code associated with an event                   |
| `INSTID`     | `NUMBER`        |      | Instruction ID associated with an event                |
| `REVISION`   | `NUMBER`        |      | Plan revision number associated with an event          |

**See Also:**

- [Oracle Data Guard Concepts and Administration](../sbydb/using-DBMS_ROLLING-to-perform-rolling-upgrade.md) for more information about rolling operations.

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ROLLING.md) for more information about the `DBMS_ROLLING` package
