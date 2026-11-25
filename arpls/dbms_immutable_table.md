## 91 DBMS_IMMUTABLE_TABLE

Immutable tables are read-only tables that protect data against unauthorized modification. They also prevent against accidental data modifications that may be caused by human errors. The `DBMS_IMMUTABLE_TABLE` package allows you to delete the expired rows in an immutable table.

This chapter contains the following topics:

- DBMS_IMMUTABLE_TABLE Overview
- DBMS_IMMUTABLE_TABLE Security Model
- Summary of DBMS_IMMUTABLE_TABLE Subprograms

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md)

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md)

- [Oracle Database Reference](../refrn/index.md)

### 91.1 DBMS_IMMUTABLE_TABLE Overview

Immutable tables are `read-only` tables that protect data against unauthorized modification. Immutable tables also prevent against accidental data modifications that may be caused by human errors. You must specify a retention period for the immutable table and for rows within the immutable table. An immutable table can be dropped if it contains no rows or if the specified retention period for the table has lapsed. Rows can be deleted from an immutable table only after the specified retention period for rows in the table has elapsed. Except for increasing the retention periods, you cannot modify the definition of an immutable table.

### 91.2 DBMS_IMMUTABLE_TABLE Security Model

The `DBMS_IMMUTABLE_TABLE` package is owned by `SYS` and is installed as part of database installation. The routines in the package are run with invoker's rights and hence run with the privileges of the current user.

### 91.3 Summary of DBMS_IMMUTABLE_TABLE Subprograms

This table lists the `DBMS_IMMUTABLE_TABLE` subprograms in alphabetical order and briefly describes them.

Table 91-1 DBMS_IMMUTABLE_TABLE Package Subprograms

| Subprogram                    | Description                              |
|:------------------------------|:-----------------------------------------|
| DELETE_EXPIRED_ROWS Procedure | This procedure deletes the expired rows. |

#### 91.3.1 DELETE_EXPIRED_ROWS Procedure

This procedure deletes some or all of the expired rows from the immutable table. This procedure does not commit.

##### Syntax

    DBMS_IMMUTABLE_TABLE.DELETE_EXPIRED_ROWS(
       schema_name                  IN VARCHAR2,
       table_name                   IN VARCHAR2,
       before_timestamp             IN TIMESTAMP WITH TIME ZONE DEFAULT NULL,
       number_of_rows_deleted       OUT NUMBER);

##### Parameters

Table 91-2 DELETE_EXPIRED_ROWS Procedure Parameters

| Parameter                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `schema_name`            | The name of the schema.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `table_name`             | The name of the immutable table.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `before_timestamp`       | If the parameter is `NULL`, all expired rows in the table are deleted. If the parameter is not `NULL` and older than the timestamp calculated based on current time and row retention time, rows with timestamps less than the parameter value are deleted. If the parameter is younger than the timestamp calculated based on the current time and row retention time, the calculated timestamp is used, and all expired rows are deleted.<br>The default value is `NULL`. |
| `number_of_rows_deleted` | The number of rows deleted.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
