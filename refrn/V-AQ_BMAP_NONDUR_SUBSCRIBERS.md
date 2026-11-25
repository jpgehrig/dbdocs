## 7.16 V\$AQ_BMAP_NONDUR_SUBSCRIBERS

`V$AQ_BMAP_NONDUR_SUBSCRIBERS` can be used to get the available bit positions. The view is queried to get the free bit position during creation of a non-durable subscriber.

| Column     | Datatype   | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `QUEUE_ID` | `NUMBER`   | Queue ID                                                                                                                                                                                                                                                                                                                                                                         |
| `USED_POS` | `RAW(128)` | Stream of bits to identify used and available bit positions                                                                                                                                                                                                                                                                                                                      |
| `CON_ID`   | `NUMBER`   | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

[Oracle Database Advanced Queuing User's Guide](../adque/aq-introduction.md) for more information about Oracle Database Advanced Queueing
