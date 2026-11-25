## 20 DBMS_APP_CONT_REPORT

This procedure generates a report of ACCHK trace collected while `ACCHK_SET(TRUE)`.

This chapter contains the following topics:

- DBMS_APP_CONT_REPORT Security Model

- Summary of DBMS_APP_CONT_REPORT Subprograms

### 20.1 DBMS_APP_CONT_REPORT Security Model

Applications must have the `EXECUTE` privilege on the `DBMS_APP_CONT_REPORT` package.

### 20.2 Summary of DBMS_APP_CONT_REPORT Subprograms

This topic lists the `DBMS_APP_CONT_REPORT` subprograms in alphabetical order and briefly describes them.

Table 20-1 DBMS_APP_CONT_REPORT Package Subprograms

| Subprogram             | Description                                                                               |
|:-----------------------|:------------------------------------------------------------------------------------------|
| ACCHK_REPORT Procedure | This procedure provides a report of your run. The data is derived from the `acchk` views. |

#### 20.2.1 ACCHK_REPORT Procedure

This procedure generates a report of your run. The data is derived from the `acchk` views.

##### Syntax

    DBMS_APP_CONT_REPORT.ACCHK_REPORT (
       level                    IN VARCHAR2,
       service_name             IN VARCHAR2);

##### Parameters

Table 20-2 ACCHK_REPORT Procedure Parameters

| Parameter      | Description                                                                                                                                                                               |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `level`        | These are constants.<br>• `SUMMARY`-summary report only (default)<br>• `WARNING`-summary and warnings<br>• `FULL`-summary and all workload capture, including where there are no warnings |
| `service_name` | The service name qualifier (Optional).<br>The value `NULL` applies to all `service_names`.                                                                                                |

##### Procedure Exceptions

The exceptions of `DBMS_APP_CONT_REPORT.ACCHK_REPORT` procedure are as follows:

- `20000`-Invalid report level parameter.

##### Example

    SET SERVEROUTPUT ON FORMAT WRAPPED 
    SET LINESIZE 180
    DBMS_APP_CONT_REPORT.ACCHK_REPORT(DBMS_APP_CONT_REPORT.FULL);

    SET SERVEROUTPUT ON FORMAT WRAPPED 
    SET LINESIZE 180
    DBMS_APP_CONT_REPORT.ACCHK_REPORT(DBMS_APP_CONT_REPORT.WARNING);

    SET SERVEROUTPUT ON FORMAT WRAPPED 
    SET LINESIZE 180
    DBMS_APP_CONT_REPORT.ACCHK_REPORT(DBMS_APP_CONT_REPORT.SUMMARY);
