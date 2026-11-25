## 6.123 DBA_WORKLOAD_REPLAY_CLIENTS

`DBA_WORKLOAD_REPLAY_CLIENTS` displays all workload replay clients and their assigned instances.

| Column            | Datatype     | NULL       | Description                                                                                              |
|:------------------|:-------------|:-----------|:---------------------------------------------------------------------------------------------------------|
| `WRC_ID`          | `NUMBER(38)` | `NOT NULL` | The identifier of a workload replay client                                                               |
| `SCHEDULE_CAP_ID` | `NUMBER(38)` | `NOT NULL` | A unique identifier for a workload capture added to a replay schedule. `0` for a non-consolidated replay |
| `INSTANCE_NUMBER` | `NUMBER(38)` | `NOT NULL` | The instance that the replay client connects to                                                          |
