## 5.103 DBA_ILMRESULTS

`DBA_ILMRESULTS` displays information on data movement-related Automatic Data Optimization jobs in the database.

### Related View

`USER_ILMRESULTS` displays information on data movement-related Automatic Data Optimization jobs for tasks created by the user.

**Note:**

Automatic Data Optimization is supported in Oracle Database 12c Release 2 multitenant environments.

| Column            | Datatype         | NULL | Description                                                                                                                                                                                                                   |
|:------------------|:-----------------|:-----|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TASK_ID`         | `NUMBER`         |      | Number that uniquely identifies a specific Automatic Data Optimization task                                                                                                                                                   |
| `JOB_NAME`        | `VARCHAR2(128)`  |      | Name of the Automatic Data Optimization job                                                                                                                                                                                   |
| `JOB_STATE`       | `VARCHAR2(35)`   |      | State of the job. Possible values:<br>• `JOB CREATED`<br>• `COMPLETED SUCCESSFULLY`<br>• `FAILED`<br>• `STOPPED`<br>• `JOB CREATION FAILED`<br>• `DEPENDENT OBJECTS BEING REBUILT`<br>• `FAILED TO REBUILD DEPENDENT OBJECTS` |
| `START_TIME`      | `TIMESTAMP(6)`   |      | Start time of the Automatic Data Optimization job                                                                                                                                                                             |
| `COMPLETION_TIME` | `TIMESTAMP(6)`   |      | Completion time of the Automatic Data Optimization job                                                                                                                                                                        |
| `COMMENTS`        | `VARCHAR2(4000)` |      | Additional information in cases where the Automatic Data Optimization job execution fails                                                                                                                                     |
| `STATISTICS`      | `CLOB`           |      | Job specific statistics, such as space saved via compression. This column is in the form of comma separated name / value pairs, with each pair representing a particular statistic name and value.                            |

**See Also:**

"[USER_ILMRESULTS](USER_ILMRESULTS.md)"
