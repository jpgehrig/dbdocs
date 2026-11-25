## 5.200 DBA_MVREF_STATS

`DBA_MVREF_STATS` shows the `REFRESH_ID` associated with each refresh run of each materialized view for the database. It also provides some basic timing statistics related to that materialized view’s refresh in that run.

### Related View

`USER_MVREF_STATS` shows the `REFRESH_ID` associated with each refresh run of each materialized view for the database that is accessible to the current user. It also provides some basic timing statistics related to that materialized view’s refresh in that run. This view does not display the `MV_OWNER` column.

| Column                  | Datatype         | NULL       | Description                                                                                                                                                                    |
|:------------------------|:-----------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MV_OWNER`              | `VARCHAR2(128)`  | `NOT NULL` | Owner of the materialized view                                                                                                                                                 |
| `MV_NAME`               | `VARCHAR2(128)`  | `NOT NULL` | Name of the materialized view                                                                                                                                                  |
| `REFRESH_ID`            | `NUMBER`         | `NOT NULL` | The refresh ID of the refresh run                                                                                                                                              |
| `REFRESH_METHOD`        | `VARCHAR2(30)`   |            | The refresh method used to refresh the materialized view:<br>• `FAST`<br>• `PCT`<br>• `COMPLETE`<br>• `OUT OF PLACE FAST`<br>• `OUT OF PLACE PCT`<br>• `OUT OF PLACE COMPLETE` |
| `REFRESH_OPTIMIZATIONS` | `VARCHAR2(4000)` |            | The refresh optimization, for example, a null refresh, or a primary key/foreign key that is applied during refresh of the materialize view                                     |
| `ADDITIONAL_EXECUTIONS` | `VARCHAR2(4000)` |            | The additional executions, for example, an index rebuild, or log operations involved during refresh of the materialized view                                                   |
| `START_TIME`            | `TIMESTAMP(6)`   |            | Start time of the refresh run                                                                                                                                                  |
| `END_TIME`              | `TIMESTAMP(6)`   |            | End time of the refresh run                                                                                                                                                    |
| `ELAPSED_TIME`          | `NUMBER`         |            | The length of time for the refresh run, in seconds                                                                                                                             |
| `LOG_SETUP_TIME`        | `NUMBER`         |            | Log setup time (in seconds) for the materialized view for a non-atomic refresh; `NULL` for an atomic refresh                                                                   |
| `LOG_PURGE_TIME`        | `NUMBER`         |            | Log purge time (in seconds) for the materialized view in the case of atomic refresh; `NULL` in the case of non-atomic refresh                                                  |
| `INITIAL_NUM_ROWS`      | `NUMBER`         |            | Initial number of rows in the materialized view (at the start of the refresh)                                                                                                  |
| `FINAL_NUM_ROWS`        | `NUMBER`         |            | Final number of rows in the materialized view (at the end of the refresh)                                                                                                      |

**See Also:**

"[USER_MVREF_STATS](USER_MVREF_STATS.md)"
