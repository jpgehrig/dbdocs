## 7.201 V\$ENABLEDPRIVS

`V$ENABLEDPRIVS` displays the system privileges that have been granted to the current user directly or through the currently enabled roles.

| Column        | Datatype       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PRIV_NUMBER` | `NUMBER`       | Numeric identifier of the system privilege<br>The matching privilege name for each `PRIV_NUMBER` can be found in the table `SYSTEM_PRIVILEGE_MAP`.                                                                                                                                                                                                                               |
| `SCOPE`       | `VARCHAR2(11)` | Indicates the scope with which a privilege was granted. Possible values:<br>• `COMMON`<br>• `APPLICATION`<br>• `LOCAL`<br>• `NULL` (if connected to a non-CDB )                                                                                                                                                                                                                  |
| `CON_ID`      | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[SYSTEM_PRIVILEGE_MAP](SYSTEM_PRIVILEGE_MAP.md)"
