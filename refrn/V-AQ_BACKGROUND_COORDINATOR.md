## 7.15 V\$AQ_BACKGROUND_COORDINATOR

`V$AQ_BACKGROUND_COORDINATOR` lists performance statistics for the Oracle Database Advanced Queueing primary background coordinator process (AQPC).

| Column             | Datatype       | Description                                                                                                                                            |
|:-------------------|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PROCESS_ID`       | `VARCHAR2(24)` | Operating system process ID of the primary                                                                                                             |
| `PROCESS_NAME`     | `VARCHAR2(48)` | Operating system name of the primary                                                                                                                   |
| `NUM_JOBS`         | `NUMBER`       | Number of jobs started                                                                                                                                 |
| `JOB_LATENCY`      | `NUMBER`       | Job start latency                                                                                                                                      |
| `NUM_COORDINATORS` | `NUMBER`       | Number of primaries started                                                                                                                            |
| `CON_ID`           | `NUMBER`       | The ID of the container to which the data pertains. The `CON_ID` value in this view is always 0. The rows pertain to the entire CDB or to the non-CDB. |

**See Also:**

[Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md) for more information about Oracle Database Advanced Queueing
