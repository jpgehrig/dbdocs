## 3.30 ALL_REPLICATION_PROCESS_EVENTS

`ALL_REPLICATION_PROCESS_EVENTS` provides information about the replication processes events accessible to the current user.

### Related View

`DBA_REPLICATION_PROCESS_EVENTS` provides information about the replication processes events in the database.

| Column          | Datatype         | NULL       | Description                                                                                                                                                                |
|:----------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `STREAMS_TYPE`  | `VARCHAR2(10)`   |            | Streams type:<br>• `XStream`<br>• `GoldenGate`                                                                                                                             |
| `PROCESS_TYPE`  | `VARCHAR2(27)`   |            | Process type:<br>• `Capture`<br>• `Capture server`<br>• `Apply Coordinator`<br>• `Apply Server`<br>• `Apply Network Receiver`<br>• `Apply Reader`<br>• `Apply Hash server` |
| `STREAMS_NAME`  | `VARCHAR2(128)`  | `NOT NULL` | Streams name                                                                                                                                                               |
| `EVENT_NAME`    | `VARCHAR2(128)`  |            | Event name:<br>• `START`<br>• `STOP`<br>• `ABORT`<br>• `CREATE`<br>• `DROP`<br>• `PARAMETER CHANGE`<br>• `HANDLER CREATE`<br>• `HANDLER REMOVE`<br>• `ALTER`               |
| `DESCRIPTION`   | `VARCHAR2(2000)` |            | Event description                                                                                                                                                          |
| `EVENT_TIME`    | `TIMESTAMP(6)`   |            | Time when the event occurred                                                                                                                                               |
| `ERROR_NUMBER`  | `NUMBER`         |            | Error number (valid when event is Error)                                                                                                                                   |
| `ERROR_MESSAGE` | `VARCHAR2(2000)` |            | Error Message (valid when event is an error)                                                                                                                               |

**See Also:**

"[DBA_REPLICATION_PROCESS_EVENTS](DBA_REPLICATION_PROCESS_EVENTS.md)"
