## 6.172 DBMS_ALERT_INFO

`DBMS_ALERT_INFO` describes registered alerts.

| Column    | Datatype         | NULL       | Description                                                                                   |
|:----------|:-----------------|:-----------|:----------------------------------------------------------------------------------------------|
| `NAME`    | `VARCHAR2(30)`   | `NOT NULL` | Name of the alert                                                                             |
| `SID`     | `VARCHAR2(30)`   | `NOT NULL` | Session ID of a session waiting for this alert                                                |
| `CHANGED` | `VARCHAR2(1)`    |            | Boolean flag to indicate that an alert has been signaled. `Y`: alert signaled, `N`: no alert. |
| `MESSAGE` | `VARCHAR2(1800)` |            | Optional message passed by signaler                                                           |
