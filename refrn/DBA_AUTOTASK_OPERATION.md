## 4.173 DBA_AUTOTASK_OPERATION

`DBA_AUTOTASK_OPERATION` displays all automated maintenance task operations for each client.

| Column                   | Datatype                      | NULL | Description                                                                                            |
|:-------------------------|:------------------------------|:-----|:-------------------------------------------------------------------------------------------------------|
| `CLIENT_NAME`            | `VARCHAR2(64)`                |      | Name of the client                                                                                     |
| `OPERATION_NAME`         | `VARCHAR2(64)`                |      | Name of the operation                                                                                  |
| `OPERATION_TAG`          | `VARCHAR2(3)`                 |      | Tag for the operation                                                                                  |
| `PRIORITY_OVERRIDE`      | `VARCHAR2(7)`                 |      | User-specified priority at which the task executes:<br>• `URGENT`<br>• `HIGH`<br>• `MEDIUM`<br>• `LOW` |
| `ATTRIBUTES`             | `VARCHAR2(4000)`              |      | Attributes of the operation                                                                            |
| `USE_RESOURCE_ESTIMATES` | `VARCHAR2(5)`                 |      | Indicates whether resource usage estimates are used for the operation (`TRUE`) or not (`FALSE`)        |
| `STATUS`                 | `VARCHAR2(8)`                 |      | Job status:<br>• `ENABLED`<br>• `DISABLED`                                                             |
| `LAST_CHANGE`            | `TIMESTAMP(6) WITH TIME ZONE` |      | Timestamp of the last change                                                                           |
