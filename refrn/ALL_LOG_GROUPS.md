## 2.257 ALL_LOG_GROUPS

`ALL_LOG_GROUPS` describes the log group definitions on the tables accessible to the current user.

### Related Views

- `DBA_LOG_GROUPS` describes the log group definitions on all tables in the database.

- `USER_LOG_GROUPS` describes the log group definitions on the tables owned by the current user.

| Column           | Datatype        | NULL       | Description                                                                                                                                                                |
|:-----------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the log group definition                                                                                                                                          |
| `LOG_GROUP_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the log group definition                                                                                                                                           |
| `TABLE_NAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the table on which the log group is defined                                                                                                                        |
| `LOG_GROUP_TYPE` | `VARCHAR2(28)`  |            | Type of the log group:<br>• `ALL` `COLUMN` `LOGGING`<br>• `FOREIGN` `KEY` `LOGGING`<br>• `PRIMARY` `KEY` `LOGGING`<br>• `UNIQUE` `KEY` `LOGGING`<br>• `USER` `LOG` `GROUP` |
| `ALWAYS`         | `VARCHAR2(11)`  |            | Indicates whether the log group is an unconditional log group (`ALWAYS`) or a conditional log group (`CONDITIONAL`)                                                        |
| `GENERATED`      | `VARCHAR2(14)`  |            | Indicates whether the name of the supplemental log group was system generated (`GENERATED` `NAME`) or not (`USER` `NAME`)                                                  |

**See Also:**

- "[DBA_LOG_GROUPS](DBA_LOG_GROUPS.md)"

- "[USER_LOG_GROUPS](USER_LOG_GROUPS.md)"
