## 5.251 DBA_PRIV_CAPTURES

`DBA_PRIV_CAPTURES` lists the privilege analysis policies in the database.

| Column        | Datatype         | NULL       | Description                                                                                                                                                                                                                                                       |
|:--------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`        | `VARCHAR2(128)`  | `NOT NULL` | Name of the privilege analysis policy                                                                                                                                                                                                                             |
| `DESCRIPTION` | `VARCHAR2(1024)` |            | Description of the privilege analysis                                                                                                                                                                                                                             |
| `TYPE`        | `VARCHAR2(16)`   |            | Type of the privilege analysis policy.<br>Possible values:<br>• `G_DATABASE`: Database wide privilege analysis<br>• `G_ROLE`: Role privilege analysis<br>• `G_CONTEXT`: Context privilege analysis<br>• `G_ROLE_AND_CONTEXT`: Role and context privilege analysis |
| `ENABLED`     | `VARCHAR2(1)`    |            | Enabling status of the privilege analysis                                                                                                                                                                                                                         |
| `ROLES`       | `ROLE_ID_LIST`   |            | List of roles whose privileges to analyze if the privilege analysis type is `G_ROLE` or `G_ROLE_AND_CONTEXT`                                                                                                                                                      |
| `CONTEXT`     | `VARCHAR2(4000)` |            | Context condition if the privilege analysis type is `G_CONTEXT` or `G_ROLE_AND_CONTEXT`                                                                                                                                                                           |
| `RUN_NAME`    | `VARCHAR2(128)`  |            | Displays run name information for each run                                                                                                                                                                                                                        |

**See Also:**

[Oracle Database Security Guide](../dbseg/performing-privilege-analysis-identify-privilege-use.md) for more information about privilege analysis
