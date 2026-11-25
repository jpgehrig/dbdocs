## 6.13 DBA_STREAMS_TP_COMPONENT_LINK

`DBA_STREAMS_TP_COMPONENT_LINK` displays information about how messages flow between Replication components.

| Column                       | Datatype         | NULL       | Description                                                                                                                                   |
|:-----------------------------|:-----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `SOURCE_COMPONENT_ID`        | `NUMBER`         | `NOT NULL` | ID of the source Replication component                                                                                                        |
| `SOURCE_COMPONENT_NAME`      | `VARCHAR2(4000)` |            | Name of the source Replication component                                                                                                      |
| `SOURCE_COMPONENT_DB`        | `VARCHAR2(128)`  |            | Database where the source Replication component resides                                                                                       |
| `SOURCE_COMPONENT_TYPE`      | `VARCHAR2(20)`   |            | Type of the source Replication component:<br>• `CAPTURE`<br>• `PROPAGATION SENDER`<br>• `PROPAGATION RECEIVER`<br>• `APPLY`<br>• `QUEUE`      |
| `DESTINATION_COMPONENT_ID`   | `NUMBER`         | `NOT NULL` | ID of the destination Replication component                                                                                                   |
| `DESTINATION_COMPONENT_NAME` | `VARCHAR2(4000)` |            | Name of the destination Replication component                                                                                                 |
| `DESTINATION_COMPONENT_DB`   | `VARCHAR2(128)`  |            | Database where the destination Replication component resides                                                                                  |
| `DESTINATION_COMPONENT_TYPE` | `VARCHAR2(20)`   |            | Type of the destination Replication component:<br>• `CAPTURE`<br>• `PROPAGATION SENDER`<br>• `PROPAGATION RECEIVER`<br>• `APPLY`<br>• `QUEUE` |
| `PATH_ID`                    | `NUMBER`         | `NOT NULL` | ID of the stream path                                                                                                                         |
| `POSITION`                   | `NUMBER`         |            | Position of the link within the stream path                                                                                                   |
