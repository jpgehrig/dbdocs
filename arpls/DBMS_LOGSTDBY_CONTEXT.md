## 107  DBMS_LOGSTDBY_CONTEXT

As of Oracle Database 12c release 1 (12.1), SQL Apply processes have access to a context namespace called `LSBY_APPLY_CONTEXT`. You can use the procedures provided in the `DBMS_LOGSTDBY_CONTEXT` package to set and retrieve various parameters associated with `LSBY_APPLY_CONTEXT`. This is useful when writing skip procedures that are registered with SQL Apply using the `DBMS_LOGSTBDY.SKIP` and `DBMS_LOGSTDBY.SKIP_ERROR` procedures.

This chapter contains the following topics:

- Overview

- Security Model

- Summary of DBMS_LOGSTDBY_CONTEXT Subprograms

**See Also:**

[Oracle Data Guard Concepts and Administration](../sbydb/creating-oracle-data-guard-logical-standby.md) for more information about SQL Apply and logical standby databases

### 107.1 DBMS_LOGSTDBY_CONTEXT Overview

SQL Apply processes have access to a context namespace called `LSBY_APPLY_CONTEXT`.

The following table lists the predefined parameters associated with `LSBY_APPLY_CONTEXT` that you can set and retrieve by using the procedures provided in the `DBMS_LOGSTDBY_CONTEXT` package. The ability to set and retrieve the parameters in this way is useful when writing skip procedures that are registered with SQL Apply using the `DBMS_LOGSTBDY.SKIP` and `DBMS_LOGSTDBY.SKIP_ERROR` procedures.

Table 107-1 Predefined Parameters of Namespace LSBY_APPLY_CONTEXT

| Parameter        | Description                                                                                                                                   |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `STATEMENT`      | First 4000 bytes of the statement that the Apply process is processing.                                                                       |
| `STATEMENT_TYPE` | See [Table 105-15](DBMS_LOGSTDBY.md) for a list of various statement types.                                                                   |
| `PACKAGE_SCHEMA` | Schema that owns the PL/SQL package being processed (if applicable).                                                                          |
| `PACKAGE_NAME`   | Name of the PL/SQL package being processed (if applicable).                                                                                   |
| `PROCEDURE_NAME` | Name of the PL/SQL procedure being processed (if applicable).                                                                                 |
| `CURRENT_SCHEMA` | Current schema in effect when the DDL or PL/SQL procedure was executed at the primary.                                                        |
| `XIDUSN`         | XIDUSN of the transaction at the primary database.                                                                                            |
| `XIDSLT`         | XIDSLT of the transaction at the primary database.                                                                                            |
| `XIDSQN`         | XIDSQN of the transaction at the primary database.                                                                                            |
| `SCHEMA`         | Schema that owns the object being processed by SQL Apply (in the case of DML or DDL operations).                                              |
| `NAME`           | Object name being processed by SQL Apply (in case of DML or DDL operations).                                                                  |
| `CONTAINER_NAME` | Container where the target object or the PL/SQL procedure resides (in the case of a multitenant container database (CDB)).                    |
| `ERROR`          | Text of the original error encountered by the SQL Apply process (if applicable).                                                              |
| `NEW_ERROR`      | Text of the new error to be raised by the SQL Apply process (if applicable, See the DBMS_LOGSTDBY [SKIP_ERROR Procedure](DBMS_LOGSTDBY.md) ). |
| `NEW_STMT`       | Text of the replacement statement that SQL Apply must execute (If applicable, See the DBMS_LOGSTDBY [SKIP Procedure](DBMS_LOGSTDBY.md)).      |
| `SKIP_ACTION`    | The skip action to be performed by SQL Apply (See the DBMS_LOGSTDBY [SKIP Procedure](DBMS_LOGSTDBY.md)).                                      |

### 107.2 DBMS_LOGSTDBY_CONTEXT Security Model

The security model for the `DBMS_LOGSTDBY_CONTEXT` package is the same as for the `DBMS_LOGSTDBY` package.

**See Also:**

[DBMS_LOGSTDBY](DBMS_LOGSTDBY.md)

### 107.3 Summary of DBMS_LOGSTDBY_CONTEXT Subprograms

This table lists and briefly describes the `DBMS_LOGSTDBY_CONTEXT` package subprograms.

Table 107-2 DBMS_LOGSTDBY_CONTEXT Package Subprograms

| Subprogram                  | Description                                                            |
|:----------------------------|:-----------------------------------------------------------------------|
| CLEAR_ALL_CONTEXT Procedure | Clears all parameters contained within namespace `LSBY_APPLY_CONTEXT`. |
| CLEAR_CONTEXT Procedure     | Clears the specific parameter.                                         |
| GET_CONTEXT Procedure       | Retrieves the value for the specified parameter.                       |
| SET_CONTEXT Procedure       | Sets the named parameter with the specified value.                     |

#### 107.3.1 CLEAR_ALL_CONTEXT Procedure

This procedure clears all parameters contained within namespace `LSBY_APPLY_CONTEXT.`

##### Syntax

    DBMS_LOGSTDBY_CONTEXT.CLEAR_ALL_CONTEXT;

##### Parameters

None

#### 107.3.2 CLEAR_CONTEXT Procedure

This procedure clears the specific parameter.

##### Syntax

    DBMS_LOGSTDBY_CONTEXT.CLEAR_CONTEXT (
       name            IN VARCHAR2);

##### Parameters

Table 107-3 CLEAR_CONTEXT Procedure Parameters

| Parameter | Description                          |
|:----------|:-------------------------------------|
| `name`    | Name of the parameter to be cleared. |

#### 107.3.3 GET_CONTEXT Procedure

This procedure retrieves the value for the specified parameter.

##### Syntax

    DBMS_LOGSTDBY_CONTEXT.GET_CONTEXT (
       name            IN VARCHAR2,
       value           OUT VARCHAR2);

##### Parameters

Table 107-4 GET_CONTEXT Procedure Parameters

| Parameter | Description                            |
|:----------|:---------------------------------------|
| `name`    | Name of the parameter.                 |
| value     | The value retrieved for the parameter. |

#### 107.3.4 SET_CONTEXT Procedure

This procedure sets the named parameter with the specified value.

##### Syntax

    DBMS_LOGSTDBY_CONTEXT.SET_CONTEXT (
       name            IN VARCHAR2
       value           IN VARCHAR2);

##### Parameters

Table 107-5 SET_CONTEXT Procedure Parameters

| Parameter | Description                                      |
|:----------|:-------------------------------------------------|
| `name`    | Name of the parameter to be set.                 |
| value     | Value to be assigned to the parameter being set. |
