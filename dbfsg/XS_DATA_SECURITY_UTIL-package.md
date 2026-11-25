## 11.5 XS_DATA_SECURITY_UTIL Package

The `XS_DATA_SECURITY_UTIL` package is a utility package that schedules automatic refreshment for static ACL to a user table and changes the ACL refreshment mode to on-commit or on-demand refresh.

This section includes the following topics:

- Security Model

- Constants

- Summary of XS_DATA_SECURITY_UTIL Subprograms

### 11.5.1 Security Model

The `XS_DATA_SECURITY_UTIL` package is created in the `SYS` schema. You need `EXECUTE` privileges on the package to be able to run the programs contained in this package.

### 11.5.2 Constants

The following are valid values for ACLMV refresh modes:

    ACLMV_ON_DEMAND  CONSTANT VARCHAR2(9) := 'ON DEMAND';
    ACLMV_ON_COMMIT  CONSTANT VARCHAR2(9) := 'ON COMMIT';

The following are types of refresh on static ACLMV:

    XS_ON_COMMIT_MV  CONSTANT BINARY_INTEGER := 0;
    XS_ON_DEMAND_MV  CONSTANT BINARY_INTEGER := 1;
    XS_SCHEDULED_MV  CONSTANT BINARY_INTEGER := 2;

The following are types of static ACLMV:

    XS_SYSTEM_GENERATED_MV  CONSTANT BINARY_INTEGER := 0;
    XS_USER_SPECIFIED_MV    CONSTANT BINARY_INTEGER := 1;

### 11.5.3 Summary of XS_DATA_SECURITY_UTIL Subprograms

Table 11-7 Summary of XS_DATA_SECURITY_UTIL Subprograms

| Subprogram                            | Brief Description                                                   |
|:--------------------------------------|:--------------------------------------------------------------------|
| SCHEDULE_STATIC_ACL_REFRESH Procedure | Schedules automatic refreshment for static ACL to a user table      |
| ALTER_STATIC_ACL_REFRESH Procedure    | Changes the ACL refreshment mode to on-commit or on-demand refresh. |

This section describes the following XS_DATA_SECURITY_UTIL subprograms:

#### 11.5.3.1 SCHEDULE_STATIC_ACL_REFRESH Procedure

The `SCHEDULE_STATIC_ACL_REFRESH` procedure is used to invoke or schedule automatic refresh for static ACL to a user table. It can start the refresh immediately if `NULL` value is passed into the `start_date` and `repeat_interval` parameters.

To find the status of all latest static ACL refresh jobs done for tables or views available for the current user, query the [ALL_XDS_LATEST_ACL_REFSTAT](real-application-security-data-dictionary-views.md), [DBA_XDS_LATEST_ACL_REFSTAT](real-application-security-data-dictionary-views.md), and [USER_XDS_LATEST_ACL_REFSTAT](real-application-security-data-dictionary-views.md) data dictionary views. All static ACL refresh job status history can be found in [ALL_XDS_ACL_REFSTAT](real-application-security-data-dictionary-views.md), [DBA_XDS_ACL_REFSTAT](real-application-security-data-dictionary-views.md), and [USER_XDS_ACL_REFSTAT](real-application-security-data-dictionary-views.md) data dictionary views.

##### Syntax

    XS_DATA_SECURITY_UTIL.SCHEDULE_STATIC_ACL_REFRESH (
      schema_name      IN VARCHAR2 DEFAULT NULL,
      table_name       IN VARCHAR2,
      start_date       IN TIMESTAMP WITH TIME ZONE DEFAULT NULL,
      repeat_interval  IN VARCHAR2 DEFAULT NULL,
      comments         IN VARCHAR2 DEFAULT NULL );

##### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `schema_name`     | Specifies the name for the schema to which the table belongs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `table_name `     | The table name which is used with above schema name to uniquely identify a table for the static ACL refreshment.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `start_date`      | This attribute specifies the first date on which this refresh is scheduled to run. If the function is called repeatedly, then the latest given `start_date` and `repeat_interval` is used to schedule the job. Each execution result of ACL refresh done by immediate call, on-commit, or refresh job is added into `XDS_ACL_REFSTAT`.<br>If `start_date` and `repeat_interval` are left `NULL`, then the refresh is launched immediately and any existing refresh schedule is erased. For immediate refresh, no row will be added into `XDS_ACL_REFRESH`, as it does not change refresh mode.                                                                        |
| `repeat_interval` | This attribute specifies how often the refresh should repeat. You can specify the repeat interval by using `DBMS_SCHEDULER` package calendaring syntax or using PL/SQL expressions. See [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SCHEDULER.md) for more information about using calendering syntax.<br>The expression specified is evaluated to determine the next time the refresh should run. If `repeat_interval` is not specified, the job runs only once at the specified start date.<br>The `start_date` and `repeat_interval` are used to create a refresh job by using `DBMS_SCHEDULER` package with `end_date` default as `NULL`. |
| `Comments`        | This attribute specifies a comment about the job. By default, this attribute is `NULL`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

##### Examples

    SYS.XS_DATA_SECURITY_UTIL.SCHEDULE_STATIC_ACL_REFRESH('aclmvuser', 'sales', SYSTIMESTAMP, 'freq=hourly; interval=2');

#### 11.5.3.2 ALTER_STATIC_ACL_REFRESH Procedure

The `ALTER_STATIC_ACL_REFRESH` procedure is used to change the ACL refresh mode to on-commit or on-demand refresh.

##### Syntax

    XS_DATA_SECURITY_UTIL.ALTER_STATIC_ACL_REFRESH (
      schema_name      IN VARCHAR2 DEFAULT NULL,
      table_name       IN VARCHAR2,
      refresh_mode     IN VARCHAR2);

##### Parameters

| Parameter      | Description                                                                                                                   |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------|
| `schema_name`  | Specifies the name for the schema that the table belongs to.                                                                  |
| `table_name `  | The table name, which is used with the schema name to uniquely identify a table for altering the static ACL refreshment mode. |
| `refresh_mode` | `ON COMMIT` or `ON DEMAND`                                                                                                    |

##### Examples

    SYS.XS_DATA_SECURITY_UTIL.ALTER_STATIC_ACL_REFRESH('aclmvuser','sales', refresh_mode=>'ON COMMIT');
