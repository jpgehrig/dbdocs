## 131 DBMS_PLSQL_CODE_COVERAGE

The `DBMS_PLSQL_CODE_COVERAGE` package provides an interface for the collection of code coverage data of PL/SQL applications at the basic block level.

This chapter contains the following topics:

- DBMS_PLSQL_CODE_COVERAGE Overview

- DBMS_PLSQL_CODE_COVERAGE Security Model

- Summary of DBMS_PLSQL_CODE_COVERAGE Subprograms

### 131.1 DBMS_PLSQL_CODE_COVERAGE Overview

The` DBMS_PLSQL_CODE_COVERAGE` package provides an interface for collecting code coverage information at the basic block level of PL/SQL applications. A basic block refers to a single entry single exit block of PL/SQL code. PL/SQL developers want to know how well their test infrastructure exercised their code. The coverage tables are created using the `CREATE_COVERAGE_TABLES` procedure.

A typical code coverage run in a session involves calls to :

- START_COVERAGE

- Run PL/SQL code

- STOP_COVERAGE

**See Also:**

- [Oracle Database Development Guide](../adfns/basic-block-coverage.md) for more information about using PL/SQL basic block coverage to maintain quality

- [Oracle Database PL/SQL Language Reference](../lnpls/COVERAGE-pragma.md) for the `COVERAGE PRAGMA` syntax and semantics

- [Oracle Database PL/SQL Language Reference](../lnpls/architecture-pl-sql.md) for more information about the PLSQL_OPTIMIZE_LEVEL compilation parameter

### 131.2 DBMS_PLSQL_CODE_COVERAGE Security Model

The user must have `EXECUTE` privilege on the DBMS_PLSQL_CODE_COVERAGE package.

The user must have `CREATE` privilege on the unit to collect coverage information about this unit.

Coverage information is not collected for wrapped units.

### 131.3 Summary of DBMS_PLSQL_CODE_COVERAGE Subprograms

This table lists the `DBMS_PLSQL_CODE_COVERAGE` subprograms and briefly describes them.

Table 131-1 DBMS_PLSQL_CODE_COVERAGE Package Subprograms

| Subprogram                       | Description                                                                      |
|:---------------------------------|:---------------------------------------------------------------------------------|
| CREATE_COVERAGE_TABLES Procedure | Creates coverage tables                                                          |
| START_COVERAGE Function          | Starts the coverage data collection in the user’s session and returns the RUN_ID |
| STOP_COVERAGE Procedure          | Ends the current coverage run                                                    |

#### 131.3.1 CREATE_COVERAGE_TABLES Procedure

This procedure creates the tables used for coverage data collection.

##### Syntax

    DBMS_PLSQL_CODE_COVERAGE.CREATE_COVERAGE_TABLES (
       FORCE_IT     IN BOOLEAN DEFAULT FALSE);

##### Parameters

| Parameter  | Description                                                                                                                                                                      |
|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FORCE_IT` | The default is to raise an error if the coverage tables already exists. If set to TRUE, the tables are dropped silently if the tables already exist, and new tables are created. |

##### Exceptions

Table 131-2 CREATE_COVERAGE_TABLES Exceptions

| Exception        | Description                                                     |
|:-----------------|:----------------------------------------------------------------|
| `COVERAGE_ERROR` | The `FORCE_IT` parameter is FALSE and the tables already exist. |

#### 131.3.2 START_COVERAGE Function

This function starts the coverage data collection in the user’s session and returns a unique identifier `RUN_ID` for the run.

##### Syntax

    DBMS_PLSQL_CODE_COVERAGE.START_COVERAGE (
       run_comment   IN VARCHAR2)
       RETURN NUMBER;

##### Parameters

| Parameter     | Description                                          |
|:--------------|:-----------------------------------------------------|
| `run_comment` | Allows the user to name a run and identify the test. |

#### 131.3.3 STOP_COVERAGE Procedure

This procedure ends the current coverage run.

##### Syntax

    DBMS_PLSQL_CODE_COVERAGE.STOP_COVERAGE;

##### Exceptions

Table 131-3 STOP_COVERAGE Exceptions

| Exception        | Description                                             |
|:-----------------|:--------------------------------------------------------|
| `COVERAGE_ERROR` | An error is raised if the coverage tables do not exist. |
