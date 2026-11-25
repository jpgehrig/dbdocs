## 4.175 DBA_AUTOTASK_STATUS

`DBA_AUTOTASK_STATUS` displays status information for automated maintenance.

| Column        | Datatype                      | NULL | Description                                                                                                                  |
|:--------------|:------------------------------|:-----|:-----------------------------------------------------------------------------------------------------------------------------|
| `STATUS`      | `VARCHAR2(8)`                 |      | Shows the status of automated maintenance. Possible values are:<br>• `ENABLED`<br>• `DISABLED`<br>• `ALLOWED`<br>• `INVALID` |
| `LAST_CHANGE` | `TIMESTAMP(6) WITH TIME ZONE` |      | Timestamp of last status change                                                                                              |
