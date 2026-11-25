## 7.31 V\$AQ_SERVER_POOL

`V$AQ_SERVER_POOL` lists performance statistics for all the servers in the pool.

| Column                    | Datatype       | Description                                                                                                                                            |
|:--------------------------|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `COORDINATOR_ID`          | `NUMBER`       | ID of the coordinator                                                                                                                                  |
| `COORDINATOR_INSTANCE_ID` | `NUMBER`       | Instance of the coordinator                                                                                                                            |
| `PROCESS_ID`              | `VARCHAR2(24)` | Operating system process ID of the server                                                                                                              |
| `PROCESS_NAME`            | `VARCHAR2(48)` | Operating system process name of the server                                                                                                            |
| `JOB_NAME`                | `VARCHAR2(32)` | Name of the job handled                                                                                                                                |
| `POOL_STATE`              | `VARCHAR2(20)` | State of the pool:<br>• `REMOTE`<br>• `IDLE`<br>• `ACTIVE`                                                                                             |
| `CON_ID`                  | `NUMBER`       | The ID of the container to which the data pertains. The `CON_ID` value in this view is always 0. The rows pertain to the entire CDB or to the non-CDB. |

**See Also:**

[Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md) for more information about Oracle Database Advanced Queueing
