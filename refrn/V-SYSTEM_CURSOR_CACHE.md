## 9.99 V\$SYSTEM_CURSOR_CACHE

`V$SYSTEM_CURSOR_CACHE` displays system wide information on cursor usage.

**See Also:**

"[V\$SESSION_CURSOR_CACHE](V-SESSION_CURSOR_CACHE.md)"

| Column      | Datatype | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:------------|:---------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OPENS`     | `NUMBER` | Cumulative total of cursor opens                                                                                                                                                                                                                                                                                                                                                 |
| `HITS`      | `NUMBER` | Cumulative total of cursor open hits                                                                                                                                                                                                                                                                                                                                             |
| `HIT_RATIO` | `NUMBER` | Ratio of the number of times an open cursor was found divided by the number of times a cursor was sought                                                                                                                                                                                                                                                                         |
| `CON_ID`    | `NUMBER` | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |
