## 90  DBMS_ILM_ADMIN

The `DBMS_ILM_ADMIN` package provides an interface to customize Automatic Data Optimization (ADO) policy execution. In combination with partitioning and compression, ADO policies can be used to help implement an Information Lifecycle Management (ILM) strategy.

This chapter contains the following topics:

- Overview

- Security Model

- Constants

- Summary of DBMS_ILM_ADMIN Subprograms

**See Also:**

- [Oracle Database VLDB and Partitioning Guide](../vldbg/ilm-strategy-heatmap-ado.md) for information about managing Automatic Data Optimization (ADO) with this package

- [DBMS_ILM](DBMS_ILM.md)

- [DBMS_HEAT_MAP](DBMS_HEAT_MAP.md)

### 90.1 DBMS_ILM_ADMIN Overview

To implement your ILM strategy, you can use Heat Map in Oracle Database to track data access and modification. You can also use Automatic Data Optimization (ADO) to automate the compression and movement of data between different tiers of storage within the database.

### 90.2 DBMS_ILM_ADMIN Security Model

This package runs under definer's rights. The user requires DBA privileges.

### 90.3 DBMS_ILM_ADMIN Constants

The table in this topic describes constants used by the `DBMS_ILM_ADMIN` package.

The value column refers to the numeric or character value that the constants resolve to.

Table 90-1 DBMS_ILM_ADMIN Constants

| Constant              | Value | Type     | Description                                                                                                                                                                                                                        |
|:----------------------|:------|:---------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ABS_JOBLIMIT`        | `12`  | `NUMBER` | Specifies the absolute number of concurrent ILM ADO jobs.                                                                                                                                                                          |
| `EXECUTION_INTERVAL`  | 1     | `NUMBER` | Determines the frequency with which ADO background evaluation occurs. Specified in minutes.                                                                                                                                        |
| `RETENTION_TIME `     | `2`   | `NUMBER` | Controls the amount of time ADO history should be maintained. Specified in days.                                                                                                                                                   |
| `EXECUTION_MODE `     | 4     | `NUMBER` | Controls whether ADO execution is online, offline. The value for this parameter should either be `DBMS_ILM_ADMIN`.`ILM_EXECUTION_OFFLINE` or `DBMS_ILM_ADMIN`.`ILM_EXECUTION_ONLINE`.                                              |
| `JOBLIMIT `           | `5`   | `NUMBER` | Controls the upper limit on number of ILM ADO jobs at any time. The maximum number of concurrent ADO jobs is `JOBLIMIT*`(number of instances)`*`(number of CPUs per instance).                                                     |
| `JOB_SIZELIMIT`       | `13`  | `NUMBER` | Specifies the size (in megabytes) of the data that is processed by a single ILM ADO row level compression job.                                                                                                                     |
| `ENABLED `            | `7`   | `NUMBER` | Provides a way to turn background ADO off or on                                                                                                                                                                                    |
| `TBS_PERCENT_USED `   | `8`   | `NUMBER` | Decides when a tablespace is considered full. Specified as a percentage of tablespace quota.                                                                                                                                       |
| `TBS_PERCENT_FREE `   | `9`   | `NUMBER` | Decides the targeted tablespace storage through ADO actions as a percentage of tablespace quota.                                                                                                                                   |
| `DEG_PARALLEL `       | `10`  | `NUMBER` | Decides the degree of parallelism to be used for ADO jobs                                                                                                                                                                          |
| `POLICY_TIME `        | 11    | `NUMBER` | Decides if ADO policies are treated as though they are specified in seconds rather than days. Can take value `ILM_POLICY_IN_SECONDS` (treat policy time in seconds) or `ILM_POLICY_IN_DAYS` (treat policy time in days - default). |
| `HEAT_MAP_SEG_READ`   | 1     | `NUMBER` | Segment read done                                                                                                                                                                                                                  |
| `HEAT_MAP_SEG_WRITE`  | 2     | `NUMBER` | Segment write done                                                                                                                                                                                                                 |
| `HEAT_MAP_SEG_SCAN`   | 4     | `NUMBER` | Full table scan done                                                                                                                                                                                                               |
| `HEAT_MAP_SEG_LOOKUP` | 8     | `NUMBER` | Index scan done                                                                                                                                                                                                                    |

The `DBMS_ILM_ADMIN` package uses the constants as parameter values shown in Table 90-2.

Table 90-2 DBMS_ILM_ADMIN Constants Used as Parameter Values

| Constant                 | Value | Type     | Description                                                                                                                                                                                                                                                                                                                                                                        |
|:-------------------------|:------|:---------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ILM_EXECUTION_OFFLINE`  | 1     | `NUMBER` | Specifies that the object may be offline while ADO action is performed.                                                                                                                                                                                                                                                                                                            |
| `ILM_EXECUTION_ONLINE `  | `2`   | `NUMBER` | Specifies that the object should be online while ADO action is performed                                                                                                                                                                                                                                                                                                           |
| `ILM_ENABLED `           | 1     | `NUMBER` | Indicates automatic ADO policy evaluation and execution is enabled                                                                                                                                                                                                                                                                                                                 |
| `ILM_DISABLED `          | `2`   | `NUMBER` | Indicates automatic ADO policy evaluation and execution is disabled                                                                                                                                                                                                                                                                                                                |
| `ILM_POLICY_IN_DAYS `    | `0`   | `NUMBER` | Indicates policy is specified in days. This is the default.                                                                                                                                                                                                                                                                                                                        |
| `ILM_POLICY_IN_SECONDS ` | `1`   | `NUMBER` | Indicates policy unit is changed from days to seconds. This could be used to test ADO policy evaluation quickly instead of waiting for the policy duration.<br>**Note:**<br>• Setting `ILM_POLICY_IN_SECONDS` does not compress the blocks within the specified seconds.<br>• Setting `ILM_POLICY_IN_SECONDS` is for test ADO and should not be set in the production environment. |

### 90.4 Summary of DBMS_ILM_ADMIN Subprograms

This table lists and briefly describes the `DBMS_ILM_ADMIN` package subprograms.

Table 90-3 DBMS_ILM_ADMIN Package Subprograms

| Subprogram                     | Description                                                                                                                                    |
|:-------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| CLEAR_HEAT_MAP_ALL Procedure   | Deletes all rows except the dummy row                                                                                                          |
| CLEAR_HEAT_MAP_TABLE Procedure | Clears all or some statistics for the heat map table, deleting rows for a given table or segment which match a given pattern, or all such rows |
| CUSTOMIZE_ILM Procedure        | Customizes environment for ILM execution by specifying the values for ILM execution related parameters                                         |
| DISABLE_ILM Procedure          | Turns off all background ILM scheduling                                                                                                        |
| ENABLE_ILM Procedure           | Turns on all background ILM scheduling                                                                                                         |
| SET_HEAT_MAP_ALL Procedure     | Updates or inserts heat map rows for all tables                                                                                                |
| SET_HEAT_MAP_START Procedure   | Sets the start date for collecting heat map data                                                                                               |
| SET_HEAT_MAP_TABLE Procedure   | Updates or inserts a row for the specified table or segment                                                                                    |

#### 90.4.1 CLEAR_HEAT_MAP_ALL Procedure

This procedure deletes all rows in `HEAT_MAP_STAT$` except the dummy row.

##### Syntax

    DBMS_ILM_ADMIN.CLEAR_HEAT_MAP_ALL;

#### 90.4.2 CLEAR_HEAT_MAP_TABLE Procedure

This procedure clears all or some statistics for the heat map table, deleting rows for a given table or segment which match a given pattern, or all such rows.

##### Syntax

    DBMS_ILM_ADMIN.CLEAR_HEAT_MAP_TABLE  (
       owner                   IN  VARCHAR2,
       tablename               IN  VARCHAR2,
       partition               IN  VARCHAR2 default '',
       access_date             IN  DATE DEFAULT NULL,
       segment_access_summary  IN  NUMBER DEFAULT NULL);

##### Parameters

Table 90-4 CLEAR_HEAT_MAP_TABLE Procedure Parameters

| Parameter                | Description                                                                               |
|:-------------------------|:------------------------------------------------------------------------------------------|
| `owner`                  | Table owner                                                                               |
| `tablename`              | Table name                                                                                |
| `partition`              | Name of the subobject, defaults to `NULL`                                                 |
| `access_date`            | Date for the entry in `HEAT_MAP_STAT$` to be removed                                      |
| `segment_access_summary` | Summary of segment access constants indicating access operations performed on the segment |

#### 90.4.3 CUSTOMIZE_ILM Procedure

This procedure customizes environment for ILM execution by specifying the values for ILM execution related parameters. These values take effect for the next background scheduling.

##### Syntax

    DBMS_ILM_ADMIN.CUSTOMIZE_ILM  (
       parameter            IN       NUMBER,
       value                IN       NUMBER);

##### Parameters

Table 90-5 CUSTOMIZE_ILM Procedure Parameters

| Parameter   | Description                                                        |
|:------------|:-------------------------------------------------------------------|
| `parameter` | One of the parameter constants defined in `DBMS_ILM_ADMIN` package |
| `value`     | Value of parameter                                                 |

#### 90.4.4 DISABLE_ILM Procedure

This procedure turns off all background ILM scheduling.

##### Syntax

    DBMS_ILM_ADMIN.DISABLE_ILM;

#### 90.4.5 ENABLE_ILM Procedure

This procedure turns on all background ILM scheduling.

##### Syntax

    DBMS_ILM_ADMIN.ENABLE_ILM;

#### 90.4.6 SET_HEAT_MAP_ALL Procedure

This procedure sets an HTTP request header. The request header is sent to the Web server as soon as it is set.

##### Syntax

    DBMS_ILM_ADMIN.SET_HEAT_MAP_ALL  (
       access_date            IN DATE,
       segment_access_summary IN NUMBER);

##### Parameters

Table 90-6 SET_HEAT_MAP_ALL Procedure Parameters

| Parameter                | Description                                                                               |
|:-------------------------|:------------------------------------------------------------------------------------------|
| `access_date`            | Date for the entry in `HEAT_MAP_STAT$` to be added                                        |
| `segment_access_summary` | Summary of segment access constants indicating access operations performed on the segment |

#### 90.4.7 SET_HEAT_MAP_START Procedure

This procedure sets the start date for collecting heat map data.

##### Syntax

    DBMS_ILM_ADMIN.SET_HEAT_MAP_START  (
       start_date  IN   DATE);

##### Parameters

Table 90-7 SET_HEAT_MAP_START Procedure Parameters

| Parameter    | Description                                                |
|:-------------|:-----------------------------------------------------------|
| `start_date` | Indicates the new date from which all statistics are valid |

#### 90.4.8 SET_HEAT_MAP_TABLE Procedure

This procedure updates or inserts a row for the specified table or segment.

##### Syntax

    DBMS_ILM_ADMIN.SET_HEAT_MAP_TABLE  (
       owner                  IN VARCHAR2,
       tablename              IN VARCHAR2,
       partition              IN VARCHAR2 DEFAULT '',
       access_date            IN DATE DEFAULT NULL,
       segment_access_summary IN NUMBER DEFAULT NULL);

##### Parameters

Table 90-8 SET_HEAT_MAP_TABLE Procedure Parameters

| Parameter                | Description                                                                               |
|:-------------------------|:------------------------------------------------------------------------------------------|
| `owner`                  | Table owner                                                                               |
| `tablename`              | Table name                                                                                |
| `partition`              | Name of the subobject, defaults to `NULL`                                                 |
| `access_date`            | Date for the entry in `HEAT_MAP_STAT$` to be added                                        |
| `segment_access_summary` | Summary of segment access constants indicating access operations performed on the segment |
