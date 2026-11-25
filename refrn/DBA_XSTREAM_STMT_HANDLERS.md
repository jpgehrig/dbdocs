## 6.160 DBA_XSTREAM_STMT_HANDLERS

`DBA_XSTREAM_STMT_HANDLERS` displays information about all XStream statement DML handlers in the database.

| Column              | Datatype         | NULL       | Description                       |
|:--------------------|:-----------------|:-----------|:----------------------------------|
| `HANDLER_NAME`      | `VARCHAR2(128)`  | `NOT NULL` | Name of the statement handler     |
| `HANDLER_COMMENT`   | `VARCHAR2(4000)` |            | Comment of the statement handler  |
| `CREATION_TIME`     | `TIMESTAMP(6)`   |            | Timestamp for script creation     |
| `MODIFICATION_TIME` | `TIMESTAMP(6)`   |            | Timestamp for script modification |
