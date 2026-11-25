## 8.159 V\$RECOVERY_PROGRESS

`V$RECOVERY_PROGRESS` can be used to track database recovery operations to ensure that they are not stalled, and also to estimate the time required to complete the operation in progress.

On non-coordinator instances, `V$RECOVERY_PROGRESS` is not populated.

On the coordinator instance (the instance where MRP0 was started to start recovery), `V$RECOVERY_PROGRESS` has the same set of rows as before, except the following rows in the `ITEM` column are always 0 (not used) with Multi-Instance Redo Apply:

- Active Apply

- Maximum Apply Rate

- Apply Time per Log

- Checkpoint Time per Log

- Recovery ID

`V$RECOVERY_PROGRESS` is a subview of `V$SESSION_LONGOPS`.

**Note:**

This view is populated on the instance where the MRP0 process is started if recovery is running in Multi-Instance Redo Apply mode. Not all the columns will be populated.

| Column       | Datatype        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-------------|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `START_TIME` | `DATE`          | Start time of the recovery operation                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `TYPE`       | `VARCHAR2(64)`  | Type of recovery operation being performed:<br>• `CRASH RECOVERY`<br>• `INSTANCE RECOVERY`<br>• `MEDIA RECOVERY`                                                                                                                                                                                                                                                                                                                                                                       |
| `ITEM`       | `VARCHAR2(32)`  | Item being measured.<br>When TYPE is CRASH RECOVERY or INSTANCE RECOVERY, the possible values are:<br>• `Log Files`<br>• `Redo Blocks`<br>When TYPE is MEDIA RECOVERY, the possible values are:<br>• `Active Apply Rate`<br>• `Average Apply Rate`<br>• `Maximum Apply Rate`<br>• `Redo Applied`<br>• `Log Files`<br>• `Last Applied Redo`<br>• `Active Time`<br>• `Elapsed Time`<br>• `Apply Time per Log`<br>• `Checkpoint Time per Log`<br>• `Standby Apply Lag`<br>• `Recovery ID` |
| `UNITS`      | `VARCHAR2(32)`  | The units of measurement for each item                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `SOFAR`      | `NUMBER`        | Amount of work done so far                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TOTAL`      | `NUMBER`        | Total amount of work expected                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `TIMESTAMP`  | `DATE`          | Timestamp of the last redo record applied                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMENTS`   | `VARCHAR2(248)` | Miscellaneous notes; currently displays the SCN for the last applied redo                                                                                                                                                                                                                                                                                                                                                                                                              |
| `CON_ID`     | `NUMBER`        | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data                                                                                                       |

**See Also:**

- "[V\$SESSION_LONGOPS](V-SESSION_LONGOPS.md)"

- "[Background Processes](background-processes.md)" for more information about the MRP0 process

- [Oracle Database Backup and Recovery User’s Guide](../bradv/introduction-backup-recovery.md) for more information about performing database recovery
