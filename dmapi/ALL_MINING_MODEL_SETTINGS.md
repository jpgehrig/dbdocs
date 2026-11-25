`ALL_MINING_MODEL_SETTINGS` describes the settings of the mining models accessible to the current user.

Mining models are schema objects created by Oracle Data Mining.

### Related Views

- `DBA_MINING_MODEL_SETTINGS` describes the settings of all mining models in the database.

- `USER_MINING_MODEL_SETTINGS` describes the settings of the mining models owned by the current user. This view does not display the `OWNER` column.

| Column          | Datatype         | NULL       | Description                                                                                              |
|:----------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)`  | `NOT NULL` | Owner of the mining model                                                                                |
| `MODEL_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | Name of the mining model                                                                                 |
| `SETTING_NAME`  | `VARCHAR2(30)`   | `NOT NULL` | Name of the setting                                                                                      |
| `SETTING_VALUE` | `VARCHAR2(4000)` | –          | Value of the setting                                                                                     |
| `SETTING_TYPE`  | `VARCHAR2(7)`    | –          | Indicates whether the default value (`DEFAULT`) or a user-specified value (`INPUT`) is used by the model |

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](DBMS_DATA_MINING.md) for descriptions of model settings

**Related Topics**

- [DBA_MINING_MODEL_SETTINGS](../refrn/DBA_MINING_MODEL_SETTINGS.md)
- [USER_MINING_MODEL_SETTINGS](../refrn/USER_MINING_MODEL_SETTINGS.md)
