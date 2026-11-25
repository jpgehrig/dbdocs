## 69  DBMS_EDITIONS_UTILITIES

The `DBMS_EDITIONS_UTILITIES` package provides helper functions for edition-related operations.

The chapter contains the following topics:

- Overview

- Security Model

- Exceptions

- Summary of DBMS_EDITIONS_UTILITIES Subprograms

### 69.1 DBMS_EDITIONS_UTILITIES Overview

The `DBMS_EDITIONS_UTILITIES` package implements an interface which provides helper functions for edition-related operations.

### 69.2 DBMS_EDITIONS_UTILITIES Security Model

This package is owned by `SYS` with execute access granted to `PUBLIC`. It runs with invoker's rights, that is, with the security profile of the caller.

### 69.3 DBMS_EDITIONS_UTILITIES Exceptions

The table in this topic lists exception messages created by DBMS_EDITIONS_UTILITIES.

Table 69-1 DBMS_EDITIONS_UTILITIES Error Messages

| Error       | Description             |
|:------------|:------------------------|
| `ORA-38817` | Insufficient privileges |
| `ORA-942`   | Missing table           |

### 69.4 Summary of DBMS_EDITIONS_UTILITIES Subprograms

This table lists and describes the `DBMS_EDITIONS_UTILITIES` package subprograms.

Table 69-2 DBMS_EDITIONS_UTILITIES Package Subprograms

| Subprogram                               | Description                                                                                                                                   |
|:-----------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| CLEAN_UNUSABLE_EDITIONS Procedure        | Drops covered objects in unusable editions, and drops empty unusable editions if possible.                                                    |
| SET_EDITIONING_VIEWS_READ_ONLY Procedure | Given the schema name and table name, this procedure sets the corresponding editioning views in all editions to `READ` `ONLY` or `READ/WRITE` |
| SET_NULL_COLUMN_VALUES_TO_EXPR Procedure | For use only during an edition-based redefinition (EBR) exercise                                                                              |

#### 69.4.1 CLEAN_UNUSABLE_EDITIONS Procedure

Drops all covered objects in any unusable editions and drops empty unusable editions.

##### Syntax

The `CLEAN_UNUSABLE_EDITIONS` procedure executes immediately and in its entirety.

    DBMS_EDITIONS_UTILITIES.CLEAN_UNUSABLE_EDITIONS ( );

##### Usage Notes

The `COMPATIBLE` parameter must be set to 12.2.0 or higher for this procedure to execute.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/DROP-EDITION.md) for information about `DROP EDITION`

- [Oracle Database Development Guide](../adfns/editions.md) for more information about using edition-based redefinition

#### 69.4.2 SET_EDITIONING_VIEWS_READ_ONLY Procedure

Given the schema name and table name, this procedure sets the corresponding editioning views in all editions to `READ` `ONLY` or `READ/WRITE`.

##### Syntax

    DBMS_EDITIONS_UTILITIES.SET_EDITIONING_VIEWS_READ_ONLY (
       table_name IN VARCHAR2,
       owner      IN VARCHAR2 DEFAULT NULL,
       read_only  IN BOOLEAN  DEFAULT TRUE);

##### Parameters

Table 69-3 SET_EDITIONING_VIEWS_READ_ONLY Procedure Parameters

| Parameter    | Description                                                                                                  |
|:-------------|:-------------------------------------------------------------------------------------------------------------|
| `table_name` | Base table of the editioning views                                                                           |
| `owner`      | Base table schema. The default (or `NULL`) is the current schema.                                            |
| `read_only`  | `TRUE` to set the views to read-only; `FALSE` (or `NULL`) sets the views to `READ/WRITE`. Default is `TRUE`. |

##### Usage Notes

The user must have the following privileges:

- Owner of the table, or have the `ALTER` `ANY` `TABLE` system privileges

- `USE` object privilege on all the editions for which the views are defined

#### 69.4.3 SET_NULL_COLUMN_VALUES_TO_EXPR Procedure

This procedure replaces `NULL` values in a replacement column with the value of an expression.

The expression evaluation cost is deferred to future updates and queries. The procedure is intended for use only during an edition-based redefinition (EBR) exercise.

**See Also:**

- [Oracle Database Development Guide](../adfns/editions.md) regarding transforming pre- to post-upgrade representation

##### Syntax

    DBMS_EDITIONS_UTILITIES.SET_NULL_COLUMN_VALUES_TO_EXPR;
       table_name    IN  VARCHAR2,
       column_name   IN  VARCHAR2,
       expression    IN  VARCHAR2);

##### Parameters

Table 69-4 SET_NULL_COLUMN_VALUES_TO_EXPR Procedure Parameters

| Parameter     | Description                                                                       |
|:--------------|:----------------------------------------------------------------------------------|
| `table_name`  | A potentially schema-qualified table name                                         |
| `column_name` | Name of the column to be updated                                                  |
| `expression`  | An expression composed of columns in the same table, constants, and SQL functions |
