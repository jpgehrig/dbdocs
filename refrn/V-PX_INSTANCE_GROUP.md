## 8.141 V\$PX_INSTANCE_GROUP

`V$PX_INSTANCE_GROUP` provides information about the instance groups being used for parallel operations by the current session.

| Column              | Datatype       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `QC_INSTANCE_GROUP` | `VARCHAR2(64)` | The instance group being used by this session for parallel operations. This value repeats for every row returned.                                                                                                                                                                                                                                                                |
| `WHY`               | `VARCHAR2(23)` | Where the current instance group name comes from, as follows:<br>SERVICE - the instance group being used is from the session's service name<br>PARALLEL_INSTANCE_GROUP - the instance group being used is being used because the PARALLEL_INSTANCE_GROUP initialization parameter has been set.<br>The value repeats for every row returned.                                     |
| `INSTANCE_NUMBER`   | `NUMBER`       | Instance number of the instance providing this instance group. There will be one row for each instance in the instance group that the Query Coordinator is using.                                                                                                                                                                                                                |
| `CON_ID`            | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[PARALLEL_INSTANCE_GROUP](PARALLEL_INSTANCE_GROUP.md)"
