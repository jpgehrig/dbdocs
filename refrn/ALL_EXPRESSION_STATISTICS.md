## 2.180 ALL_EXPRESSION_STATISTICS

`ALL_EXPRESSION_STATISTICS` provides expression usage tracking statistics for tables that are accessible to the current user.

### Related Views

- `DBA_EXPRESSION_STATISTICS` provides expression usage tracking statistics for all the tables in the database.

- `USER_EXPRESSION_STATISTICS` provides expression usage tracking statistics for tables owned by the current user. This view does not display the `OWNER` column.

| Column             | Datatype         | NULL       | Description                                                                                                                               |
|:-------------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`            | `VARCHAR2(128)`  | `NOT NULL` | Owner of the table                                                                                                                        |
| `TABLE_NAME`       | `VARCHAR2(128)`  | `NOT NULL` | Name of the table contained in the expression                                                                                             |
| `EXPRESSION_ID`    | `NUMBER`         |            | Expression ID of the current expression                                                                                                   |
| `SNAPSHOT`         | `VARCHAR2(10)`   |            | Type of snapshot for the expression:<br>• `LATEST`: Latest snapshot<br>• `CUMULATIVE`: Cumulative snapshot<br>• `WINDOW`: Window snapshot |
| `EVALUATION_COUNT` | `NUMBER`         |            | Number of times the expression has been evaluated                                                                                         |
| `FIXED_COST`       | `NUMBER`         | `NOT NULL` | Optimizer fixed cost of evaluating the expression                                                                                         |
| `DYNAMIC_COST`     | `NUMBER`         |            | Optimizer dynamic cost of evaluating the expression                                                                                       |
| `EXPRESSION_TEXT`  | `VARCHAR2(4000)` | `NOT NULL` | Text of the expression                                                                                                                    |
| `CREATED`          | `DATE`           | `NOT NULL` | Time this expression is first evaluated                                                                                                   |
| `LAST_MODIFIED`    | `DATE`           |            | Time this expression is last evaluated                                                                                                    |

**See Also:**

- "[DBA_EXPRESSION_STATISTICS](DBA_EXPRESSION_STATISTICS.md)"

- "[USER_EXPRESSION_STATISTICS](USER_EXPRESSION_STATISTICS.md)"

- "[V\$EXP_STATS](V-EXP_STATS.md)"
