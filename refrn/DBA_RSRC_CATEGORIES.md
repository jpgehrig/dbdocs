## 5.301 DBA_RSRC_CATEGORIES

`DBA_RSRC_CATEGORIES` displays all resource consumer group categories.

| Column      | Datatype         | NULL | Description                                                                                         |
|:------------|:-----------------|:-----|:----------------------------------------------------------------------------------------------------|
| `NAME`      | `VARCHAR2(128)`  |      | Name of the consumer group category                                                                 |
| `COMMENTS`  | `VARCHAR2(2000)` |      | Text comment on the consumer group category                                                         |
| `STATUS`    | `VARCHAR2(128)`  |      | Indicates whether the consumer group category is part of the pending area (`PENDING`) or not (NULL) |
| `MANDATORY` | `VARCHAR2(3)`    |      | Indicates whether the consumer group category is mandatory (`YES`) or not (`NO`)                    |
