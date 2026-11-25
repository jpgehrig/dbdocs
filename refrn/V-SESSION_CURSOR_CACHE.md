## 9.20 V\$SESSION_CURSOR_CACHE

`V$SESSION_CURSOR_CACHE` displays information on cursor usage for the current session.

**Note:**

The `V$SESSION_CURSOR_CACHE` view is not a measure of the effectiveness of the `SESSION_CACHED_CURSORS` initialization parameter.

| Column      | Datatype | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:------------|:---------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MAXIMUM`   | `NUMBER` | Maximum number of cursors to cache. Once you hit this number, some cursors will need to be closed in order to open more. The value in this column is derived from the initialization parameter `SESSION_CACHED_CURSORS`.                                                                                                                                                         |
| `COUNT`     | `NUMBER` | Current number of cursors (whether they are in use or not)                                                                                                                                                                                                                                                                                                                       |
| `OPENS`     | `NUMBER` | Cumulative total of cursor opens minus one. This is because the cursor that is currently open and being used for this query is not counted in the `OPENS` statistic.                                                                                                                                                                                                             |
| `HITS`      | `NUMBER` | Cumulative total of cursor open hits                                                                                                                                                                                                                                                                                                                                             |
| `HIT_RATIO` | `NUMBER` | Ratio of the number of times an open cursor was found divided by the number of times a cursor was sought                                                                                                                                                                                                                                                                         |
| `CON_ID`    | `NUMBER` | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[SESSION_CACHED_CURSORS](SESSION_CACHED_CURSORS.md)"
