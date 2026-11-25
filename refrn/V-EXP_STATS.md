## 7.214 V\$EXP_STATS

`V$EXP_STATS` stores the expression tracking statistics of recently executed queries.

| Column    | Datatype | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:----------|:---------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `EXPID`   | `NUMBER` | Expression ID of the current expression                                                                                                                                                                                                                                                                                                                                          |
| `OBJNUM`  | `NUMBER` | The object number contained in the expression                                                                                                                                                                                                                                                                                                                                    |
| `DYNCOST` | `NUMBER` | Optimizer dynamic cost of evaluating the expression                                                                                                                                                                                                                                                                                                                              |
| `EVALCNT` | `NUMBER` | Number of times the expression has been evaluated                                                                                                                                                                                                                                                                                                                                |
| `CON_ID`  | `NUMBER` | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[ALL_EXPRESSION_STATISTICS](ALL_EXPRESSION_STATISTICS.md)"

- "[DBA_EXPRESSION_STATISTICS](DBA_EXPRESSION_STATISTICS.md)"

- "[ALL_EXPRESSION_STATISTICS](ALL_EXPRESSION_STATISTICS.md)"
