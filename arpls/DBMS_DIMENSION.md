## 65  DBMS_DIMENSION

`DBMS_DIMENSION` enables you to verify dimension relationships and provides an alternative to the Enterprise Manager Dimension Wizard for displaying a dimension definition.

**See Also:**

[Oracle Database Data Warehousing Guide](../dwhsg/index.md) for detailed conceptual and usage information about the `DBMS_DIMENSION` package

This chapter contains the following topics:

- Security Model

- Summary of DBMS_DIMENSION Subprograms

### 65.1 DBMS_DIMENSION Security Model

Security on this package can be controlled by granting `EXECUTE` to selected users or roles.

A user can validate or describe all the dimensions in his own schema. To validate or describe a dimension in another schema, you must have either an object privilege on the dimension or one of the following system privileges: `CREATE ANY DIMENSION`, `ALTER ANY DIMENSION`, and `DROP ANY DIMENSION`.

### 65.2 Summary of DBMS_DIMENSION Subprograms

This table lists the `DBMS_DIMENSION` subprograms and briefly describes them.

Table 65-1 DBMS_DIMENSION Package Subprograms

| Subprogram                   | Description                                                                                                               |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------------|
| DESCRIBE_DIMENSION Procedure | Prints out the definition of the input dimension, including dimension owner and name, levels, hierarchies, and attributes |
| VALIDATE_DIMENSION Procedure | Verifies that the relationships specified in a dimension are correct                                                      |

#### 65.2.1 DESCRIBE_DIMENSION Procedure

This procedure displays the definition of the dimension, including dimension name, levels, hierarchies, and attributes. It displays the output using the `DBMS_OUTPUT` package.

##### Syntax

    DBMS_DIMENSION.DESCRIBE_DIMENSION (
       dimension  IN VARCHAR2);

##### Parameters

Table 65-2 DESCRIBE_DIMENSION Procedure Parameter

| Parameter   | Description                                                        |
|:------------|:-------------------------------------------------------------------|
| `dimension` | The owner and name of the dimension in the format of `owner.name`. |

#### 65.2.2 VALIDATE_DIMENSION Procedure

This procedure verifies that the relationships specified in a dimension are valid. The rowid for any row that is found to be invalid will be stored in the table `DIMENSION_EXCEPTIONS` in the user's schema.

##### Syntax

    DBMS_DIMENSION.VALIDATE_DIMENSION (
       dimension               IN VARCHAR2,
       incremental             IN BOOLEAN := TRUE,
       check_nulls             IN BOOLEAN := FALSE,
       statement_id            IN VARCHAR2 := NULL );

##### Parameters

Table 65-3 VALIDATE_DIMENSION Procedure Parameters

| Parameter      | Description                                                                                                                                                                                              |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `dimension`    | The owner and name of the dimension in the format of `owner.name`.                                                                                                                                       |
| `incremental`  | If `TRUE`, check only the new rows for tables of this dimension. If `FALSE`, check all the rows.                                                                                                         |
| `check_nulls`  | If `TRUE`, then all level columns are verified to be non-null.<br>If `FALSE`, this check is omitted. Specify `FALSE` when non-`NULL`ness is guaranteed by other means, such as `NOT` `NULL` constraints. |
| `statement_id` | A client-supplied unique identifier to associate output rows with specific invocations of the procedure.                                                                                                 |
