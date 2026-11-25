## 122  DBMS_OUTLN

The `DBMS_OUTLN` package, synonymous with `OUTLN_PKG`, contains the functional interface for subprograms associated with the management of stored outlines.

**See Also:**

For more information about using the `DBMS_OUTLN` package, see [Oracle Database SQL Tuning Guide](../tgsql/overview-of-sql-plan-management.md).

**Note:**

Stored outlines will be desupported in a future release in favor of SQL plan management. In Oracle Database 11g Release 1 (11.1), stored outlines continue to function as in past releases. However, Oracle strongly recommends that you use SQL plan management for new applications. SQL plan management creates SQL plan baselines, which offer superior SQL performance and stability compared with stored outlines.If you have existing stored outlines, please consider migrating them to SQL plan baselines by using the [LOAD_PLANS_FROM_CURSOR_CACHE Functions](DBMS_SPM.md) or [LOAD_PLANS_FROM_SQLSET Function](DBMS_SPM.md) of the `DBMS_SPM` package. When the migration is complete, you should disable or remove the stored outlines.

This chapter contains the following topics:

- Overview

- Security Model

- Summary of DBMS_OUTLN Subprograms

### 122.1 DBMS_OUTLN Overview

A stored outline is the stored data that pertains to an execution plan for a given SQL statement. It enables the optimizer to repeatedly re-create execution plans that are equivalent to the plan originally generated along with the outline.The data stored in an outline consists, in part, of a set of hints that are used to achieve plan stability.

Stored outlines will be de-supported in a future release in favor of SQL plan management. As of 11g R1, stored outlines continue to function as in past releases, but Oracle strongly recommends that you use SQL plan management for new applications. SQL plan management creates SQL plan baselines, which offer superior SQL performance and stability compared with stored outlines.If you have existing stored outlines, please consider migrating them to SQL plan baselines by using the [LOAD_PLANS_FROM_CURSOR_CACHE Functions](DBMS_SPM.md) or the [LOAD_PLANS_FROM_SQLSET Function](DBMS_SPM.md) of the [DBMS_SPM](DBMS_SPM.md) package. When the migration is complete, you should disable or remove the stored outlines.

### 122.2 DBMS_OUTLN Security Model

`DBMS_OUTLN` contains management procedures that should be available to appropriate users only. `EXECUTE` privilege is not extended to the general user community unless the DBA explicitly does so.

PL/SQL functions that are available for outline management purposes can be executed only by users with `EXECUTE` privilege on the procedure (or package).

### 122.3 Summary of DBMS_OUTLN Subprograms

This table lists the `DBMS_OUTLN` subprograms and briefly describes them.

Table 122-1 DBMS_OUTLN Package Subprograms

| Subprogram                      | Description                                                                         |
|:--------------------------------|:------------------------------------------------------------------------------------|
| CLEAR_USED Procedure            | Clears the outline 'used' flag                                                      |
| CREATE_OUTLINE Procedure        | Generates outlines from the shared cursor identified by hash value and child number |
| DROP_BY_CAT Procedure           | Drops outlines that belong to a specified category                                  |
| DROP_UNUSED Procedure           | Drops outlines that have never been applied in the compilation of a SQL statement   |
| EXACT_TEXT_SIGNATURES Procedure | Updates outline signatures to those that compute based on exact text matching       |
| UPDATE_BY_CAT Procedure         | Changes the category of outlines in one category to a new category                  |
| UPDATE_SIGNATURES Procedure     | Updates outline signatures to the current version's signature                       |

#### 122.3.1 CLEAR_USED Procedure

This procedure clears the outline 'used' flag.

##### Syntax

    DBMS_OUTLN.CLEAR_USED (
       name    IN    VARCHAR2);

##### Parameters

Table 122-2 CLEAR_USED Procedure Parameters

| Parameter | Description          |
|:----------|:---------------------|
| `name`    | Name of the outline. |

#### 122.3.2 CREATE_OUTLINE Procedure

This procedure generates an outline by reparsing the SQL statement from the shared cursor identified by hash value and child number.

##### Syntax

    DBMS_OUTLN.CREATE_OUTLINE (
       hash_value    IN NUMBER,
       child_number  IN NUMBER,
       category      IN VARCHAR2 DEFAULT 'DEFAULT');

##### Parameters

Table 122-3 CREATE_OUTLINE Procedure Parameters

| Parameter      | Description                                      |
|:---------------|:-------------------------------------------------|
| `hash_value`   | Hash value identifying the target shared cursor. |
| `child_number` | Child number of the target shared cursor.        |
| `category`     | Category in which to create outline (optional).  |

#### 122.3.3 DROP_BY_CAT Procedure

This procedure drops outlines that belong to a particular category. While outlines are put into the `DEFAULT` category unless otherwise specified, users have the option of grouping their outlines into groups called categories.

##### Syntax

    DBMS_OUTLN.DROP_BY_CAT (
       cat VARCHAR2);

##### Parameters

Table 122-4 DROP_BY_CAT Procedure Parameters

| Parameter | Description                   |
|:----------|:------------------------------|
| `cat`     | Category of outlines to drop. |

##### Usage Notes

This procedure purges a category of outlines in a single call.

##### Examples

This example drops all outlines in the `DEFAULT` category:

    DBMS_OUTLN.DROP_BY_CAT('DEFAULT');

#### 122.3.4 DROP_UNUSED Procedure

This procedure drops outlines that have never been applied in the compilation of a SQL statement.

##### Syntax

    DBMS_OUTLN.DROP_UNUSED;

##### Usage Notes

You can use `DROP_UNUSED` for outlines generated by an application for one-time use SQL statements created as a result of dynamic SQL. These outlines are never used and take up valuable disk space.

#### 122.3.5 EXACT_TEXT_SIGNATURES Procedure

This procedure updates outline signatures to those that compute based on exact text matching.

##### Syntax

    DBMS_OUTLN.EXACT_TEXT_SIGNATURES;

##### Usage Notes

This procedure is relevant only for downgrading an outline to 8.1.6 or earlier.

#### 122.3.6 UPDATE_BY_CAT Procedure

This procedure changes the category of all outlines in one category to a new category.

##### Syntax

    DBMS_OUTLN.UPDATE_BY_CAT (
       oldcat    VARCHAR2 default 'DEFAULT',
       newcat    VARCHAR2 default 'DEFAULT');

##### Parameters

Table 122-5 UPDATE_BY_CAT Procedure Parameters

| Parameter | Description                       |
|:----------|:----------------------------------|
| `oldcat`  | The current category of outlines. |
| `newcat`  | The new category of outlines.     |

#### 122.3.7 UPDATE_SIGNATURES Procedure

This procedure updates outline signatures to the current version's signature.

##### Syntax

    DBMS_OUTLN.UPDATE_SIGNATURES;

##### Usage Notes

You should execute this procedure if you have imported outlines generated in an earlier release to ensure that the signatures are compatible with the current release's computation algorithm.
