## 7.174 V\$DBFILE

`V$DBFILE` displays all data files making up the database. This view is retained for historical compatibility. Use of `V$DATAFILE` is recommended instead.

| Column   | Datatype        | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:---------|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FILE#`  | `NUMBER`        | File identifier                                                                                                                                                                                                                                                                                                                                                                  |
| `NAME`   | `VARCHAR2(513)` | Name of the file                                                                                                                                                                                                                                                                                                                                                                 |
| `CON_ID` | `NUMBER`        | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[V\$DATAFILE](V-DATAFILE.md)"
