## 6.161 DBA_XSTREAM_STMTS

`DBA_XSTREAM_STMTS` displays information about the statements in all XStream statement DML handlers in the database.

| Column               | Datatype        | NULL       | Description                          |
|:---------------------|:----------------|:-----------|:-------------------------------------|
| `HANDLER_NAME`       | `VARCHAR2(128)` | `NOT NULL` | Name of the statement handler        |
| `EXECUTION_SEQUENCE` | `NUMBER`        | `NOT NULL` | Execution sequence of the statement  |
| `STATEMENT`          | `CLOB`          |            | Text of the SQL statement            |
| `CREATION_TIME`      | `TIMESTAMP(6)`  |            | Timestamp for statement creation     |
| `MODIFICATION_TIME`  | `TIMESTAMP(6)`  |            | Timestamp for statement modification |
