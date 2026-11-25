## 85  DBMS_HM

This package contains constants and procedure declarations for health check management. Health Monitor provides facilities to run a check store and retrieve the reports through `DBMS_HM` package

This chapter contains the following topics:

- Security Model

- Summary of DBMS_HM Subprograms

**See Also:**

Oracle Database Administrator's Guide for more information about ["Health Monitor"](../admin/diagnosing-and-resolving-problems.md)

### 85.1 DBMS_HM Security Model

Users must have `EXECUTE` privilege to run the procedures of `DBMS_HM` package.

### 85.2 Summary of DBMS_HM Subprograms

This table lists the `DBMS_CONNECTION_POOL` subprograms and briefly describes them.

Table 85-1 DBMS_HM Package Subprograms

| Subprogram              | Description                                         |
|:------------------------|:----------------------------------------------------|
| GET_RUN_REPORT Function | Returns the report for the specified checker run    |
| RUN_CHECK Procedure     | Runs the specified checker with the given arguments |

#### 85.2.1 GET_RUN_REPORT Function

This function returns the report for the specified checker run.

##### Syntax

    DBMS_HM.GET_RUN_REPORT (
        run_name      IN  VARCHAR2,
        type           IN  VARCHAR2 := 'TEXT',
        level          IN  VARCHAR2 := 'BASIC',)
      RETURN CLOB;

##### Parameters

Table 85-2 GET_RUN_REPORT Function Parameters

| Parameter  | Description                                                                                                           |
|:-----------|:----------------------------------------------------------------------------------------------------------------------|
| `run_name` | Name of the check's run                                                                                               |
| `type`     | Report format type. Possible values are `'HTML'`, `'XML'` and `'TEXT'`. Default report type is `'TEXT'`.              |
| `level`    | Details of report, possible value are `'BASIC'` and `'DETAIL'`. Caution: Currently only `'BASIC'` level is supported. |

#### 85.2.2 RUN_CHECK Procedure

This procedure runs the specified checker with the specified arguments.

You can specify a name for the run, the inputs needed and maximum time-out for the run. The run report will be maintained persistently in the database.

##### Syntax

    DBMS_HM.RUN_CHECK (
       check_name     IN  VARCHAR2,
       run_name       IN  VARCHAR2 := NULL,
       timeout        IN  NUMBER := NULL,
       input_params   IN  VARCHAR2 := NULL);

##### Parameters

Table 85-3 RUN_CHECK Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `check_name`   | Name of the check to be invoked. Check names and their parameters can be accessed from the `V$HM_CHECK` and `V$HM_CHECK_PARAM` views. Users can run all checks which are not internal in nature: `SELECT` name `FROM` `V$HM_CHECK` `WHERE` `INTERNAL_CHECK` `=` `'N'` retrieves the list of checks that can be run manually by users.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `run_name`     | Name with which external users can uniquely identify this check's run. If `NULL` value is passed, then HM creates a unique name and associates with this check's run.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `timeout`      | Maximum amount of time (in units of seconds), this checker run is allowed to run. HM will interrupt the run, if it the specified time elapses for the run. If `NULL` value is passed, HM doesn't impose any timeout limits on the run.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `input_params` | Input string: which consists of name, value pairs de-limited by a special character ';'.<br>Example ('Data Block Integrity Check' invocation may take following type of input parameters.<br>`'BLC_DF_NUM=1;BLC_BL_NUM=23456'`<br>Input parameters `BLC_DF_NUM` and `BLC_BL_NUM` have values '1' and '23456' respectively.<br>Every check will have well defined set of inputs associated with it. These Input parameters, their types, default values and descriptions can be obtained using `V$HM_CHECK_PARAM` view.<br>Example: The following query gets the list of parameters, their default values and descriptions for a 'Data Block Integrity Check'<br>`SELECT a.* FROM v$hm_check_param a, v$hm_check b`<br>`WHERE a.check_id = b.id`<br>`AND b.name = 'Data Block Integrity Check';` |
