## 5.360 DBA_SQL_MANAGEMENT_CONFIG

`DBA_SQL_MANAGEMENT_CONFIG` displays the configuration parameters of the SQL management base.

You must have the `DBA` role in order to change the configuration parameter values.

| Column            | Datatype         | NULL       | Description                                                                                                                                                                                                             |
|:------------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARAMETER_NAME`  | `VARCHAR2(128)`  | `NOT NULL` | Name of the configuration parameter:<br>• `AUTO_CAPTURE_ACTION`<br>• `AUTO_CAPTURE_MODULE`<br>• `AUTO_CAPTURE_PARSING_SCHEMA_NAME`<br>• `AUTO_CAPTURE_SQL_TEXT`<br>• `PLAN_RETENTION_WEEKS`<br>• `SPACE_BUDGET_PERCENT` |
| `PARAMETER_VALUE` | `VARCHAR2(4000)` |            | Value of the configuration parameter                                                                                                                                                                                    |
| `LAST_MODIFIED`   | `TIMESTAMP(6)`   |            | Time the parameter value was last updated                                                                                                                                                                               |
| `MODIFIED_BY`     | `VARCHAR2(128)`  |            | User who last updated the parameter value                                                                                                                                                                               |
