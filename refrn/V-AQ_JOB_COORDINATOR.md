## 7.21 V\$AQ_JOB_COORDINATOR

`V$AQ_JOB_COORDINATOR` lists performance statistics per coordinator, for every AQ coordinator controlled by the Oracle Database Advanced Queueing primary coordinator.

| Column             | Datatype       | Description                                                                                                                                            |
|:-------------------|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `COORDINATOR_ID`   | `NUMBER`       | ID of the coordinator                                                                                                                                  |
| `PROCESS_ID`       | `VARCHAR2(24)` | Operating system process ID of the coordinator                                                                                                         |
| `PROCESS_NAME`     | `VARCHAR2(48)` | Operating system process name of the coordinator                                                                                                       |
| `JOB_NAME`         | `VARCHAR2(32)` | Name of the job handled                                                                                                                                |
| `JOB_TYPE`         | `NUMBER`       | Type of job handled                                                                                                                                    |
| `SERVER_COUNT`     | `NUMBER`       | Number of servers active                                                                                                                               |
| `MAX_SERVER_COUNT` | `NUMBER`       | Maximum server fanout achieved                                                                                                                         |
| `CON_ID`           | `NUMBER`       | The ID of the container to which the data pertains. The `CON_ID` value in this view is always 0. The rows pertain to the entire CDB or to the non-CDB. |

**See Also:**

[Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md) for more information about Oracle Database Advanced Queueing
