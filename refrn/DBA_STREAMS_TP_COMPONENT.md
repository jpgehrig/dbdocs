## 6.12 DBA_STREAMS_TP_COMPONENT

`DBA_STREAMS_TP_COMPONENT` displays information about each Replication component at each database.

| Column                   | Datatype         | NULL       | Description                                                                                                                       |
|:-------------------------|:-----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------|
| `COMPONENT_ID`           | `NUMBER`         | `NOT NULL` | ID of the Replication component                                                                                                   |
| `COMPONENT_NAME`         | `VARCHAR2(4000)` |            | Name of the Replication component                                                                                                 |
| `COMPONENT_DB`           | `VARCHAR2(128)`  |            | Database where the Replication component resides                                                                                  |
| `COMPONENT_TYPE`         | `VARCHAR2(20)`   |            | Type of the Replication component:<br>• `CAPTURE`<br>• `PROPAGATION SENDER`<br>• `PROPAGATION RECEIVER`<br>• `APPLY`<br>• `QUEUE` |
| `COMPONENT_CHANGED_TIME` | `DATE`           |            | Time that the Replication component was last changed                                                                              |
