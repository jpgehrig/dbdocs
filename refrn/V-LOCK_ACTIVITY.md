## 8.41 V\$LOCK_ACTIVITY

`V$LOCK_ACTIVITY` is deprecated. The information that was provided in this view is now provided in the `V$INSTANCE_CACHE_TRANSFER` and `V$SEGMENT_STATISTICS` views.

| Column       | Datatype   | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FROM_VAL`   | `CHAR(4)`  | Global Cache Resource initial state; always `NULL`                                                                                                                                                                                                                                                                                                                               |
| `TO_VAL`     | `CHAR(1)`  | Global Cache Resource initial state; always `S`                                                                                                                                                                                                                                                                                                                                  |
| `ACTION_VAL` | `CHAR(21)` | Description of the conversion; always `Lock buffers for read`                                                                                                                                                                                                                                                                                                                    |
| `COUNTER`    | `NUMBER`   | Number of times the lock operation executed                                                                                                                                                                                                                                                                                                                                      |
| `CON_ID`     | `NUMBER`   | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[V\$INSTANCE_CACHE_TRANSFER](V-INSTANCE_CACHE_TRANSFER.md)"

- "[V\$SEGMENT_STATISTICS](V-SEGMENT_STATISTICS.md)"
