Because Oracle OLAP is contained in the database and its resources are managed using the same tools, the management tasks of Oracle OLAP and the database converge. Nonetheless, you should address tasks such as database tuning in the specific context of data warehousing.

This chapter contains the following topics:

- Setting Database Initialization Parameters

- Storage Management

- Dictionary Views and System Tables

- Partitioned Cubes and Parallelism

- Analyzing Cubes and Dimensions

- Monitoring Analytic Workspaces

- About Backing Up and Recovering Analytic Workspaces

- About Copying Analytic Workspaces

- Cube Materialized Views

### 7.1 Setting Database Initialization Parameters

Table 7-1 identifies the parameters that affect the performance of Oracle OLAP. Alter your server parameter file or `init.ora` file to these values, then restart your database instance. You can monitor the effectiveness of these settings and adjust them as necessary.

**See Also:**

- [Oracle Database Performance Tuning Guide](../tgdba/configuring-database-for-performance.md) for information about tuning parameter settings

- [Oracle Database Reference](../refrn/basic-initialization-parameters.md) for descriptions of individual parameters

Table 7-1 Initial Settings for Database Parameters

| Parameter                | Default Value               | Recommended Setting                                                                                                                                                                                                                                                                                                                                    | Description                                                                                                                                                                                        |
|:-------------------------|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `JOB_QUEUE_PROCESSES`    | `1000`                      | If you reduce this value to limit the maximum number of job slaves running on an instance, then calculate the following number of processes for use by OLAP:<br>Number of CPUs, plus one additional process for every three CPUs; in a multi-core CPU, each core counts as a CPU<br>For example, `JOB_QUEUE_PROCESSES=5` for a four-processor computer | Controls the degree of parallelism in OLAP builds, as described in "Parallelism"                                                                                                                   |
| `PARALLEL_DEGREE_POLICY` | `MANUAL`                    | `AUTO` or `LIMITED`                                                                                                                                                                                                                                                                                                                                    | Controls how the degree of parallelism is determined<br>When set to `AUTO` or `LIMITED`, Oracle determines whether a SQL statement executes in parallel and, if so, the degree of parallelism used |
| `SESSIONS`               | Derived                     | 2.5 \* maximum number of simultaneous OLAP users                                                                                                                                                                                                                                                                                                       | Provides sufficient background processes for each user                                                                                                                                             |
| `UNDO_MANAGEMENT`        | `AUTO`<br>(`MANUAL` in 10g) | `AUTO`                                                                                                                                                                                                                                                                                                                                                 | Specifies use of an undo tablespace                                                                                                                                                                |
| `UNDO_TABLESPACE`        | Derived                     | Name of the undo tablespace, which must be defined previously                                                                                                                                                                                                                                                                                          | Identifies the undo tablespace defined for OLAP use, as shown in "Creating an Undo Tablespace"                                                                                                     |

#### To set the system parameters:

1.  Open the `init.ora` initialization file in a text editor.

2.  Add or change the settings in the file, as described in Table 7-1.

3.  Stop and restart the database.

    On Windows, use the Services utility to stop and restart `OracleService`.

    On Linux, use commands like the following. Be sure to identify the initialization file in the `STARTUP` command.

        SQLPLUS '/ AS SYSDBA'
        SHUTDOWN IMMEDIATE
        STARTUP pfile=$ORACLE_BASE/admin/orcl/pfile/init.ora.724200516420

### 7.2 Storage Management

Analytic workspaces are stored in the owner's default tablespace, unless the owner specifies otherwise. All tablespaces for OLAP use should specify `EXTENT MANAGEMENT LOCAL`. Tablespaces created using default parameters may use resources inefficiently. You should create undo, permanent, and temporary tablespaces that are appropriate for storing analytic workspaces.

#### 7.2.1 Creating an Undo Tablespace

Create an undo tablespace with the `EXTENT MANAGEMENT LOCAL` clause, as shown in this example:

    CREATE UNDO TABLESPACE olapundo DATAFILE '$ORACLE_BASE/oradata/undo.dbf'
         SIZE 64M REUSE AUTOEXTEND ON NEXT 8M
         MAXSIZE UNLIMITED EXTENT MANAGEMENT LOCAL;

After creating the undo tablespace, change your system parameter file to include the following settings, then restart the database as described in "Setting Database Initialization Parameters".

    UNDO_TABLESPACE=tablespace
    UNDO_MANAGEMENT=AUTO

#### 7.2.2 Creating Permanent Tablespaces for OLAP Use

Each dimensional object occupies at least one extent. A fixed extent size may waste most of the allocated space. For example, if an object is 64K and the extents are set to a uniform size of 1M (the default), then only a small portion of the extent is used.

Create permanent tablespaces with the `EXTENT MANAGEMENT LOCAL` and `SEGMENT SPACE MANAGEMENT AUTO` clauses, as shown in this example:

    CREATE TABLESPACE glo DATAFILE '$ORACLE_BASE/oradata/glo.dbf'
         SIZE 64M REUSE AUTOEXTEND ON NEXT 8M MAXSIZE UNLIMITED
         EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO;

#### 7.2.3 Creating Temporary Tablespaces for OLAP Use

Oracle OLAP uses the temporary tablespace to store all changes to the data in a cube, whether the changes are the result of a data load or data analysis. Saving the cube moves the changes into the permanent tablespace and clears the temporary tablespace.

This usage creates numerous extents within the tablespace. A temporary tablespace suitable for use by Oracle OLAP should specify the `EXTENT MANAGEMENT LOCAL` clause and a `UNIFORM SIZE` clause with a small size, as shown in this example:

    CREATE TEMPORARY TABLESPACE glotmp TEMPFILE '$ORACLE_BASE/oradata/glotmp.tmp'
         SIZE 50M REUSE AUTOEXTEND ON NEXT 5M MAXSIZE UNLIMITED
         EXTENT MANAGEMENT LOCAL UNIFORM SIZE 256K;

#### 7.2.4 Spreading Data Across Storage Resources

Oracle Database provides excellent storage management tools to simplify routine tasks. Automatic Storage Management (ASM) provides a simple storage management interface that virtualizes database storage into disk groups. You can manage a small set of disk groups, and ASM automates the placement of the database files within those disk groups.

ASM spreads data evenly across all available storage resources to optimize performance and utilization. After you add or drop disks, ASM automatically rebalances files across the disk group.

Because OLAP is part of Oracle Database, you can use ASM to manage both relational and dimensional data.

ASM is highly recommended for analytic workspaces. A system managed with ASM is faster than a file system and easier to manage than raw devices. ASM optimizes the performance of analytic workspaces both on systems with Oracle RAC and those without Oracle RAC.

However, you do not need ASM to use Oracle OLAP. You can still spread your data across multiple disks, just by defining the tablespaces like in this example:

    CREATE TABLESPACE glo DATAFILE
         'disk1/oradata/glo1.dbf' SIZE 64M REUSE AUTOEXTEND ON NEXT 8M MAXSIZE 1024M
         EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO;

    ALTER TABLESPACE glo ADD DATAFILE
         'disk2/oradata/glo2.dbf' SIZE 64M REUSE AUTOEXTEND ON NEXT 8M MAXSIZE 1024M,
         'disk3/oradata/glo3.dbf' SIZE 64M REUSE AUTOEXTEND ON NEXT 8M
              MAXSIZE UNLIMITED;

### 7.3 Dictionary Views and System Tables

Oracle Database data dictionary views and system tables contain extensive information about analytic workspaces.

#### 7.3.1 Static Data Dictionary Views

Among the static views of the database data dictionary are several that provide information about analytic workspaces. Table 7-2 provides brief descriptions of them. All data dictionary views have corresponding `DBA` and `USER` views.

Table 7-2 Static Data Dictionary Views for OLAP

| View          | Description                                                                                           |
|:--------------|:------------------------------------------------------------------------------------------------------|
| `ALL_AWS`     | Describes all analytic workspaces accessible to the current user.                                     |
| `ALL_AW_OBJ`  | Describes the current objects in all analytic workspaces accessible to the current user.              |
| `ALL_AW_PROP` | Describes the properties defined in all analytic workspaces accessible to the current user.           |
| `ALL_AW_PS`   | Describes the page spaces currently in use by all analytic workspaces accessible to the current user. |

**See Also:**

- "[Querying the Data Dictionary](querying-dimensional-objects.md)" for a list of data dictionary views that describe OLAP dimensional objects

- [Oracle Database Reference](../refrn/ALL_AWS.md) for full descriptions of all data dictionary views

#### 7.3.2 System Tables

The `SYS` user owns several tables associated with analytic workspaces.

**Note:**

These tables are vital for the operation of Oracle OLAP. Do not delete them or attempt to modify them directly without being fully aware of the consequences.

Table 7-3 OLAP Tables Owned By SYS

| Table            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AW$`            | Maintains a record of all analytic workspaces in the database, recording its name, owner, and other information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `AW$AWCREATE`    | Stores the `AWCREATE` analytic workspace, which contains programs for using OLAP Catalog metadata in Oracle Database 10g Release 10.1.0.2 and earlier releases. It exists only for backward compatibility.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `AW$AWCREATE10G` | Stores the `AWCREATE10G` analytic workspace, which contains programs for using OLAP Catalog metadata in Oracle Database 10g Release 10.1.0.3. The OLAP Catalog is not used by later releases. It exists only for backward compatibility.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `AW$AWMD`        | Stores the `AWMD` analytic workspace, which contains programs for creating metadata catalogs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `AW$AWREPORT`    | Stores the `AWREPORT` analytic workspace, which contains a program named `AWREPORT` for generating a summary space report.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `AW$AWXML`       | Stores the `AWXML` analytic workspace, which contains programs for creating and managing analytic workspaces for Oracle Database 10g Release 10.1.0.4 and later.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `AW$EXPRESS`     | Stores the `EXPRESS` analytic workspace. It contains objects and programs that support basic operations. `EXPRESS` is used any time a session is open.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `AW_OBJ$`        | Describes the objects stored in analytic workspaces.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `AW_PRG$`        | Stores program data. Not currently used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `AW_PROP$`       | Stores analytic workspace object properties.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `AW_TRACK$`      | Stores tracking data about access to aggregate cells. Not currently used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `PS$`            | Maintains a history of all page spaces. A page space is an ordered series of bytes equivalent to a file. Oracle OLAP manages a cache of workspace pages. Pages are read from storage in a table and written into the cache in response to a query. The same page can be accessed by several sessions.<br>The information stored in `PS$` enables Oracle OLAP to discard pages that are no longer in use, and to maintain a consistent view of the data for all users, even when the workspace is being modified during their sessions. When changes to a workspace are saved, unused pages are purged and the corresponding rows are deleted from `PS$`. |

#### 7.3.3 Analytic Workspace Tables

Analytic workspaces are stored in tables in the Oracle database. The names of these tables always begin with `AW$`.

For example, if the `GLOBAL` user creates two analytic workspaces, one named `FINANCIALS` and the other named `MARKETING`, then these tables are created in the `GLOBAL` schema:

    AW$FINANCIALS
    AW$MARKETING

The tables store all of the object definitions and data.

#### 7.3.4 Maintenance Logs

The first time you load data into a cube or dimension using Analytic Workspace Manager, it creates several logs. These logs are stored in tables in the same schema as the analytic workspace:

- Cube Build Log: Contains information about what happened during a build. Use this log to determine whether the build produced the results you were expecting, and if not, why not. The log is continually updated whenever a cube or dimension is refreshed, whether by Analytic Workspace Manager, the database materialized view refresh subsystem, or a PL/SQL procedure. You can query the log at any time to evaluate the progress of the build and to estimate the time to completion. The default table name is `CUBE_BUILD_LOG`.

- Cube Dimension Compile Log: Contains errors that occur during the validation of the dimension hierarchies when OLAP is aggregating a cube. The default table name is `CUBE_DIMENSION_COMPILE`.

- Cube Operations Log: Contains messages and debugging information for all OLAP engine events. The default table name is `CUBE_OPERATIONS_LOG`.

- Cube Rejected Records Log: Identifies any records that were rejected because they did not meet the expected format. The default table name is `CUBE_REJECTED_RECORDS`.

These logs enable you to track the progress of long running processes, then use the results to profile performance characteristics. They provide information to help you diagnose and remedy problems that may occur during development and maintenance of a cube. They also help diagnose performance problems in querying cubes.

You can also run the \$ORACLE_HOME/olap/admin/utlolaplog.sql script to create the build log with some useful views.

The Maintenance Wizard in Analytic Workspace Manager displays the relevant rows from these tables during every build on the Maintenance Log page. You can query the tables directly in any SQL interface.

**See Also:**

`DBMS_CUBE_LOG` in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CUBE_LOG.md)

### 7.4 Partitioned Cubes and Parallelism

Cubes are often partitioned to improve build and maintenance times. For information about creating a partitioned cube, refer to "[Partitioning a Cube](creating-dimensions-and-cubes.md)". Partitioning and parallelism are discussed in the following topics:

- Querying Metadata for Cube Partitioning

- Creating and Dropping Partitions

- Parallelism

#### 7.4.1 Querying Metadata for Cube Partitioning

To discover the current partitioning, query the `ALL_CUBES` data dictionary view. The `PARTITION_DIMENSION_NAME`, `PARTITION_HIERARCHY_NAME`, and `PARTITION_LEVEL_NAME` columns display partitioning information. For example, the following query shows that the Units Cube is partitioned on the Time dimension, the Calendar hierarchy, and the Calendar Year level.

    SELECT partition_dimension_name, partition_hierarchy_name,
         partition_level_name FROM all_cubes
         WHERE owner='GLOBAL' AND cube_name='UNITS_CUBE';

    PARTITION_DIMENSION_NAME  PARTITION_HIERARCHY_NAME  PARTITION_LEVEL_NAME
    ------------------------- ------------------------- --------------------
    TIME                      CALENDAR                  CALENDAR_YEAR

#### 7.4.2 Creating and Dropping Partitions

The OLAP engine automatically creates and drops partitions as part of data maintenance, as members are added and deleted from the partitioning dimension.

For example, assume that in the sample Global analytic workspace, the Units cube is partitioned on the Time dimension, using the Calendar hierarchy, and at the Calendar Quarter level. The OLAP engine creates a partition for each Calendar Quarter and its children. The default top partition contains Calendar Years and all members of the Fiscal hierarchy. If Global has three years of data, then the Units cube has 13 partitions: Four bottom partitions for each Calendar Year, plus the top partition.

A data refresh typically creates new time periods and deletes old ones. Whenever a Calendar Quarter value is loaded into the Time dimension, a corresponding partition is added to the cube. Whenever a Calendar Quarter value is deleted from the Time dimension, the corresponding empty partition is deleted from the cube.

#### 7.4.3 Parallelism

You can improve the performance of data maintenance by enabling parallel processing. There are two levels of parallelism:

- Parallel job execution: Loading and aggregating the data using multiple processes.

- Parallel update: Moving the data from temporary to permanent tablespaces using multiple processes.

This number of parallel processes is controlled by these factors:

- The number of objects that can be aggregated in parallel. Each cube and each partition (including the top partition) can use a separate process.

  You can control the number of partitions in a cube on the Partitioning tab of the cube property sheet in Analytic Workspace Manager.

- The number of simultaneous database processes the user is authorized to run.

  This number is controlled by the `JOB_QUEUE_PROCESSES` parameter. If you have `SYS` privileges, you can obtain the current parameter setting with the following SQL command:

      SHOW PARAMETER JOB_QUEUE_PROCESSES

- For parallel update, the number of processes you allocate to the job. You can specify the number of processes in the Maintenance Wizard of Analytic Workspace Manager when specifying the task processing options, or on the Materialized View tab of the cube.

- The number of processes allocated to SQL to fetch rows from the relational source tables. When `PARALLEL_DEGREE_POLICY` is set to `AUTO` or `LIMITED`, the database can allocate additional processes for executing SQL statements.

Suppose that a cube is partitioned on the Quarter level of Time, and the cube contains three years of data. The cube has 3\*4=12 bottom partitions, `JOB_QUEUE_PROCESSES` is set to 8, and you set the parallelism option to 4 for the build. Oracle Database processes the cube in this way when `PARALLEL_DEGREE_POLICY` is set to its default value of `MANUAL`:

1.  Load and build the dimensions of the cube serially using a single process.

2.  Load and build the 12 bottom partitions in parallel using 4 processes. As soon as one process finishes, another begins until all 12 are complete.

    This cube could use the 8 processes allowed by `JOB_QUEUE_PROCESSES`, but it is limited to 4 by the build setting.

3.  Load and build the top partition.

When `PARALLEL_DEGREE_POLICY` is set to `AUTO` or `LIMITED`, Oracle Database may allocate more than the designated processes.

Example 7-1 Build Log for Global Units Cube

This example shows excerpts from `CUBE_BUILD_LOG` for a build of the Units cube and its dimensions. Partitioning on the Calendar Year level of the Time dimension created 10 bottom partitions for 1998 to 2007. `JOB_QUEUE_PROCESSES` is set to 2 and the parallelism option is set to 2 for the build also. The log shows that Oracle Database processed the Global in this way:

1.  Processed the four dimensions serially.

2.  Processed each partition of the Units cube

<!-- -->

    SLAVE_NUMBER STATUS     COMMAND              BUILD_OBJECT    PARTITION
    ------------ ---------- -------------------- --------------- ---------------
               0 STARTED    BUILD
               0 STARTED    ATTACH AW RW WAIT
               0 COMPLETED  ATTACH AW RW WAIT
               0 STARTED    FREEZE
               0 COMPLETED  FREEZE
               0 STARTED    LOAD NO SYNCH        TIME
               0 SQL        LOAD NO SYNCH        TIME
                   .
                   .
                   .
               0 SQL        LOAD NO SYNCH        PRODUCT
               0 SQL        LOAD NO SYNCH        PRODUCT
               0 COMPLETED  LOAD NO SYNCH        PRODUCT
               0 STARTED    COMPILE              PRODUCT
               0 COMPLETED  COMPILE              PRODUCT
               0 STARTED    COMPILE AGGMAP       UNITS_CUBE
               0 COMPLETED  COMPILE AGGMAP       UNITS_CUBE
               0 STARTED    COMPILE AGGMAP       PRICE_CUBE
               0 COMPLETED  COMPILE AGGMAP       PRICE_CUBE
               0 STARTED    UPDATE/COMMIT        PRODUCT
               0 COMPLETED  UPDATE/COMMIT        PRODUCT
               0 STARTED    UPDATE/COMMIT
               0 COMPLETED  UPDATE/COMMIT
               0 STARTED    REATTACH AW MULTI TH
                            AW

               0 COMPLETED  REATTACH AW MULTI TH
                            AW

               0 STARTED    SLAVE                UNITS_CUBE      P10:CY2007
               0 STARTED    SLAVE                UNITS_CUBE      P9:CY2006
               1 STARTED    BUILD                                P10:CY2007
               1 STARTED    ATTACH AW MULTI THAW UNITS_CUBE      P10:CY2007
               1 COMPLETED  ATTACH AW MULTI THAW UNITS_CUBE      P10:CY2007
               1 STARTED    ACQUIRE              UNITS_CUBE      P10:CY2007
               1 COMPLETED  ACQUIRE              UNITS_CUBE      P10:CY2007
               1 STARTED    LOAD                 UNITS_CUBE      P10:CY2007
               1 SQL        LOAD                 UNITS_CUBE      P10:CY2007
               1 COMPLETED  LOAD                 UNITS_CUBE      P10:CY2007
               1 STARTED    UPDATE/COMMIT        UNITS_CUBE      P10:CY2007
               1 COMPLETED  UPDATE/COMMIT        UNITS_CUBE      P10:CY2007
                   .
                   .
                   .
              10 STARTED    BUILD                                P1:CY1998
              10 STARTED    ATTACH AW MULTI THAW UNITS_CUBE      P1:CY1998
              10 COMPLETED  ATTACH AW MULTI THAW UNITS_CUBE      P1:CY1998
              10 STARTED    ACQUIRE              UNITS_CUBE      P1:CY1998
              10 COMPLETED  ACQUIRE              UNITS_CUBE      P1:CY1998
              10 STARTED    LOAD                 UNITS_CUBE      P1:CY1998
              10 SQL        LOAD                 UNITS_CUBE      P1:CY1998
              10 COMPLETED  LOAD                 UNITS_CUBE      P1:CY1998
              10 STARTED    SOLVE                UNITS_CUBE      P1:CY1998
              10 COMPLETED  SOLVE                UNITS_CUBE      P1:CY1998
              10 STARTED    UPDATE/COMMIT        UNITS_CUBE      P1:CY1998
              10 COMPLETED  UPDATE/COMMIT        UNITS_CUBE      P1:CY1998
              10 STARTED    DETACH AW            UNITS_CUBE      P1:CY1998
              10 COMPLETED  DETACH AW            UNITS_CUBE      P1:CY1998
              10 COMPLETED  BUILD                                P1:CY1998
               0 COMPLETED  SLAVE                UNITS_CUBE      P1:CY1998
               0 STARTED    REATTACH AW MULTI TH
                            AW

               0 COMPLETED  REATTACH AW MULTI TH
                            AW

               0 STARTED    SLAVE                UNITS_CUBE      P0
              11 STARTED    BUILD                                P0
              11 STARTED    ATTACH AW MULTI THAW UNITS_CUBE      P0
              11 COMPLETED  ATTACH AW MULTI THAW UNITS_CUBE      P0
              11 STARTED    ACQUIRE              UNITS_CUBE      P0
              11 COMPLETED  ACQUIRE              UNITS_CUBE      P0
              11 STARTED    LOAD                 UNITS_CUBE      P0
              11 COMPLETED  LOAD                 UNITS_CUBE      P0
              11 STARTED    SOLVE                UNITS_CUBE      P0
              11 COMPLETED  SOLVE                UNITS_CUBE      P0
              11 STARTED    UPDATE/COMMIT        UNITS_CUBE      P0
              11 COMPLETED  UPDATE/COMMIT        UNITS_CUBE      P0
              11 STARTED    DETACH AW            UNITS_CUBE      P0
              11 COMPLETED  DETACH AW            UNITS_CUBE      P0
              11 COMPLETED  BUILD                                P0
               0 COMPLETED  SLAVE                UNITS_CUBE      P0
               0 STARTED    REATTACH AW RW WAIT
               0 COMPLETED  REATTACH AW RW WAIT
               0 STARTED    ANALYZE              UNITS_CUBE
               0 COMPLETED  ANALYZE              UNITS_CUBE
               0 STARTED    THAW
               0 COMPLETED  THAW
               0 STARTED    DETACH AW
               0 COMPLETED  DETACH AW
               0 COMPLETED  BUILD

    268 rows selected.

Oracle Database allocates the specified number of processes regardless of whether all of them can be used simultaneously at any point in the job. For example, if your job can use up to three processes, but you specify five, then two of the processes allocated to your job cannot be used by it or by any other job.

If Oracle Database is installed with Real Application Clusters (Oracle RAC), then a script submitted to the job queue is distributed across all nodes in the cluster. The performance gains can be significant. For example, a job running on four nodes in a cluster may run up to four times faster than the same job running on a single computer.

### 7.5 Analyzing Cubes and Dimensions

If your application executes queries directly against a single cube, you do not need to generate optimizer statistics for the cube. These queries are automatically optimized within the analytic workspace.

Optimizer statistics are used to create execution plans for queries that join two cube views or join a cube view to a table or a view of a table. They are also used for cost-based rewrite to cube materialized views. You must generate the statistics only for these types of queries.

To generate optimizer statistics, use the `DBMS_AW_STATS` PL/SQL package. You can run this package in Analytic Workspace Manager as part of a cube script, in SQL\*Plus, or in any other SQL interface. Generating the statistics does not have a significant performance cost.

`DBMS_AW_STATS` has the following syntax:

    DBMS_AW_STATS.ANALYZE
         (object       IN VARCHAR2);

The argument can be either a cube or a dimension. Example 7-2 shows a sample script for generating statistics on the Units cube and its dimensions.

Example 7-2 Generating Statistics for the Units Cube

    BEGIN
         DBMS_AW_STATS.ANALYZE('units_cube');
         DBMS_AW_STATS.ANALYZE('time');
         DBMS_AW_STATS.ANALYZE('customer');
         DBMS_AW_STATS.ANALYZE('product');
         DBMS_AW_STATS.ANALYZE('channel');
    END;
    /

Although you cannot view the statistics directly, you can examine the execution plans, as described in "[Viewing Execution Plans](querying-dimensional-objects.md)".

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/generating-and-displaying-execution-plans.md)

### 7.6 Monitoring Analytic Workspaces

Oracle Database provides various tools to help you diagnose performance problems. As an Oracle DBA, you may find these tools useful in tuning the database:

- Oracle Enterprise Manager Cloud Control (Cloud Control) is a general database management and administration tool. In addition to facilitating basic tasks like adding users and modifying datafiles, Cloud Control presents a graphic overview of a database's current status. It also provides an interface to troubleshooting and performance tuning utilities.

- Automatic Workload Repository collects database performance statistics and metrics for analysis and tuning, shows the exact time spent in the database, and saves session information.

- Automatic Database Diagnostic Monitor watches database performance statistics to identify bottlenecks, analyze SQL statements, and offer suggestions to improve performance.

Oracle Database also provides system views to help you diagnose performance problems. The following topics identify views that are either specific to OLAP or provide database information that is pertinent to OLAP.

#### 7.6.1 Dynamic Performance Views

Each Oracle Database instance maintains fixed tables that record current database activity. These tables collect data on internal disk structures and memory structures. Among them are tables that collect data on Oracle OLAP.

These tables are available to users through a set of dynamic performance views. By monitoring these views, you can detect usage trends and diagnose system bottlenecks. Table 7-4 provides a brief description of each view. Global dynamic performance views (`GV$`) are also provided.

**See Also:**

[Oracle Database Reference](../refrn/dynamic-performance-views.md) for full descriptions of the OLAP dynamic performance views.

Table 7-4 OLAP Dynamic Performance Views

| View                | Description                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------|
| `V$AW_AGGREGATE_OP` | Lists the aggregation operators available in analytic workspaces.                        |
| `V$AW_ALLOCATE_OP`  | Lists the allocation operators available in analytic workspaces.                         |
| `V$AW_CALC`         | Collects information about the use of cache space and the status of dynamic aggregation. |
| `V$AW_LONGOPS`      | Collects status information about SQL fetches.                                           |
| `V$AW_SESSION_INFO` | Collects information about each active session.                                          |
| `V$AW_OLAP`         | Collects information about the status of active analytic workspaces.                     |

Table 7-5 describes some other dynamic performance views that are not specific to OLAP, but which you may want to use when tuning your database for OLAP.

Table 7-5 Selected Database Performance Views

| View         | Description                                                                                                                    |
|:-------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `V$LOG`      | Displays log file information from the control file.                                                                           |
| `V$LOGFILE`  | Contains information about redo log files.                                                                                     |
| `V$PGASTAT`  | Provides PGA memory usage statistics and statistics about the automatic PGA memory manager when `PGA_AGGREGATE_TARGET` is set. |
| `V$ROWCACHE` | Displays statistics for data dictionary activity. Each row contains statistics for one data dictionary cache.                  |
| `V$SYSSTAT`  | Lists system statistics.                                                                                                       |

#### 7.6.2 Basic Queries for Monitoring the OLAP Option

The following queries extract OLAP information from the data dictionary. You must have a privileged account to query the DBA views.

More complex queries are provided in a script that you can download from the Oracle OLAP website on the Oracle Technology Network. For descriptions of these scripts and download instructions, refer to "OLAP DBA Scripts".

##### 7.6.2.1 Is the OLAP Option Installed in the Database?

The OLAP option is provided with Oracle Database Enterprise Edition. To verify that the OLAP components have been installed, issue this SQL command:

    SELECT comp_name, version, status FROM DBA_REGISTRY
         WHERE comp_name LIKE '%OLAP%';

    COMP_NAME                VERSION                        STATUS
    ------------------------ ------------------------------ -----------
    OLAP Analytic Workspace  12.1.0.1.0                     VALID
    Oracle OLAP API          12.1.0.1.0                     VALID
    OLAP Catalog             12.1.0.1.0                     VALID

##### 7.6.2.2 What Analytic Workspaces Are in the Database?

The `DBA_AWS` view provides information about all analytic workspaces. Use the following SQL command to get a list of names, their owners, and the version:

    SELECT owner, aw_name, aw_version FROM DBA_AWS;

    OWNER      AW_NAME                        AW_VERSION
    ---------- ------------------------------ ----------
    SYS        EXPRESS                        12.0
    GLOBAL     GLOBAL                         12.0
    SYS        AWCREATE                       12.0
    SH         SH                             12.0
    SYS        AWMD                           12.0
    SYS        AWXML                          12.0
    SYS        AWREPORT                       12.0
    SYS        AWCREATE10G                    12.0

**See Also:**

"System Tables" for descriptions of the analytic workspaces owned by `SYS`.

##### 7.6.2.3 How Big Is the Analytic Workspace?

To find out the size in bytes of the tablespace extents for a particular analytic workspace, use the following SQL statements, replacing `GLOBAL` with the name of your analytic workspace.

    SELECT extnum, SUM(dbms_lob.getlength(awlob)) bytes FROM global.aw$global
         GROUP BY extnum;

        EXTNUM      BYTES
    ---------- ----------
             0  191776956

To see the size of the LOB table containing an analytic workspace, use a SQL command like the following, replacing `GLOBAL.AW$GLOBAL` with the qualified name of your analytic workspace.

    SELECT ROUND(SUM(dbms_lob.getlength(awlob))/1024,0) kb
         FROM global.aw$global;

            KB
    ----------
        187282

##### 7.6.2.4 When Were the Analytic Workspaces Created?

The `DBA_OBJECTS` view provides the creation date of the objects in your database. The following SQL command generates an easily readable report for analytic workspaces.

    SELECT owner, object_name, created, status FROM dba_objects
          WHERE object_name LIKE 'AW$%' AND object_name!='AW$'
          GROUP BY owner, object_name, created, status
          ORDER BY owner, object_name;

    OWNER      OBJECT_NAME     CREATED   STATUS
    ---------- --------------- --------- -------
    GLOBAL     AW$GLOBAL       20-SEP-12 VALID
    SYS        AW$AWCREATE     20-SEP-12 VALID
    SYS        AW$AWCREATE10G  20-SEP-12 VALID
    SYS        AW$AWMD         20-SEP-12 VALID
    SYS        AW$AWREPORT     20-SEP-12 VALID
    SYS        AW$AWXML        20-SEP-12 VALID
    SYS        AW$EXPRESS      20-SEP-12 VALID

    7 rows selected.

#### 7.6.3 OLAP DBA Scripts

You can download a file that contains several SQL scripts from the Oracle OLAP website on the Oracle Technology Network. These scripts typically extract information from two or more system views and generate a report that may be useful in monitoring and tuning a database. To download the file, use this URL:

[`http://www.oracle.com/technetwork/database/options/olap/olap-dba-scripts-393636.zip`](http://www.oracle.com/technetwork/database/options/olap/olap-dba-scripts-393636.zip)

Table 7-6 describes these scripts. For more information, refer to the `README` file provided with the scripts.

Table 7-6 OLAP DBA Scripts

| SQL Script             | Description                                                                                                                     |
|:-----------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `aw_objects_in_cache`  | Identifies the objects in the buffer cache that are related to analytic workspaces.                                             |
| `aw_reads_writes`      | Tallies the reads from temporary and permanent tablespaces, the writes to cache, and the rows processed in analytic workspaces. |
| `aw_size`              | Displays the amount of disk space used by each analytic workspace.                                                              |
| `aw_tablespaces`       | Provides extensive information about the tablespaces used by analytic workspaces.                                               |
| `aw_users`             | Identifies the users of analytic workspaces.                                                                                    |
| `aw_wait_events`       | Describes the wait events experienced by users of analytic workspaces over the previous hour.                                   |
| `buffer_cache_hits`    | Calculates the buffer cache hit ratio.                                                                                          |
| `cursor_parameters`    | Indicates whether the database parameters that limit the number of open cursors are set too low.                                |
| `olap_pga_performance` | Determines how much PGA is in use, the size of the OLAP page pool, and the hit/miss ratio for OLAP pages for each user.         |
| `olap_pga_use`         | Determines how much PGA is consumed by the OLAP page pool to perform operations on analytic workspaces.                         |
| `session_resources`    | Identifies the use of cursors, PGA, and UGA for each open session.                                                              |
| `shared_pool_hits`     | Calculates the shared pool hit ratio.                                                                                           |

#### 7.6.4 Scripts for Monitoring Performance

Several of the scripts listed in "OLAP DBA Scripts" provide detailed information about the use of memory and other database resources by OLAP sessions. You can use these scripts as is, or you can use them as the starting point for developing your own scripts.

Example 7-3 shows the information returned by the `session_resources` script. It lists the use of resources such as cursors, PGA, and UGA.

Example 7-3 Querying Session Resources

    @session_resources

    USERNAME             NAME                                VALUE
    -------------------- ------------------------------ ----------
    GLOBAL:86            opened cursors cumulative             621
                         opened cursors current                 18
                         session cursor cache count             50
                         session cursor cache hits             432
                         session pga memory                5356368
                         session pga memory max           10468176
                         session stored procedure space          0
                         session uga memory                4230692
                         session uga memory max            7049780

    9 rows selected.

#### 7.6.5 Monitoring Disk Space

Several of the scripts listed in "OLAP DBA Scripts" provide detailed information about the use of disk space by analytic workspaces. Example 7-4 shows the information returned by the `aw_size` script. It lists all of the analytic workspaces in the database, the disk space they consume, and the tablespaces in which they are stored.

Example 7-4 Querying the Use of Disk Space By Analytic Workspaces

    @aw_size

    Analytic Workspace                            On Disk MB Tablespace
    ---------------------------------------- --------------- --------------------
    GLOBAL.GLOBAL                                     249.31 GLOBAL
    SYS.AWCREATE                                        7.81 SYSAUX
    SYS.AWCREATE10G                                     1.63 SYSAUX
    SYS.AWMD                                            8.00 SYSAUX
    SYS.AWREPORT                                        1.63 SYSAUX
    SYS.AWXML                                          18.00 SYSAUX
    SYS.EXPRESS                                         2.25 SYSAUX
                                             ---------------
    Total Disk:                                       288.63

    7 rows selected.

### 7.7 About Backing Up and Recovering Analytic Workspaces

You can backup and recover analytic workspaces using the same tools and procedures as the rest of your database.

Oracle Recovery Manager (RMAN) is a powerful tool that simplifies, automates, and improves the performance of backup and recovery operations. RMAN enables one time backup configuration, automatic management of backups, and archived logs based on a user-specified recovery window, restartable backups and restores, and test restore/recovery.

RMAN implements a recovery window to control when backups expire. This lets you establish a period during which it is possible to discover logical errors and fix the affected objects by doing a database or tablespace point-in-time recovery. RMAN also automatically expires backups that are no longer required to restore the database to a point-in-time within the recovery window. Control file auto backup also allows for restoring or recovering a database, even when an RMAN repository is not available.

### 7.8 About Copying Analytic Workspaces

You can copy analytic workspaces in several different ways, either to replicate them on another computer or to back them up.

- Data Pump. Analytic workspaces are copied with the other objects in a schema or database export. Use the `expdp`/`impdp` database utilities.

  **Tip:**

  Verify that the target schema of an import has the OLAP_XS_ADMIN privilege. Otherwise, the analytic workspace will not be created with the necessary permissions.

- Transportable Tablespaces. Analytic workspaces are copied with the other objects to a transportable tablespace. However, you can only transport the tablespace to the same platform (for example, from Linux to Linux, Solaris to Solaris, or Windows to Windows) because the OLAP `DECIMAL` data type is hardware dependent. Use the `expdp`/`impdp` database utilities. Transportable tablespaces are much faster than dump files.

The owner of an analytic workspace can export the schema to a dump file. Only users with the `EXP_FULL_DATABASE` privilege or a privileged user (such as `SYS` or a user with the `DBA` role) can export the full database or create a transportable tablespace.

**See Also:**

- "[Saving and Re-Creating Dimensional Objects with Object Definitions](creating-dimensions-and-cubes.md)" for information about XML templates

- [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for information about Oracle Data Pump and the `expdp`/`impdp` commands

### 7.9 About Saving Dimensional Object Definitions

You can save object definitions in an external file for transferring them to another database or saving a backup copy. You can also save objects definitions to a table to make them available in the Oracle Database. You can save the definitions either in an XML template or in an EIF file. Both files are platform independent.

#### 7.9.1 About XML Templates

Templates are XML documents that describe dimensional objects. You can save the XML descriptions of all the objects in an analytic workspace or just selected objects, and re-create them later in the same database or in a database on another computer or platform. You can use templates to back up your work while developing a dimensional model of your data or to distribute the design to other users.

You can save the XML definitions of the following types of objects:

- Analytic workspace: Saves all dimensional objects and all user-defined OLAP DML programs and objects.

- Dimension: Saves the dimension and its levels, hierarchies, attributes, and mappings.

- Cube: Saves the cube and its measures, calculated measures, dimensions, mappings, and all user-defined OLAP DML programs and objects associated with the cube.

- Measure Folder: Saves a list of the measures in the measure folder. It does not save the objects.

Templates store metadata, not data. You can store templates in a small text file or in a database table. When re-creating objects from a template, you must have access to the source data.

**See Also:**

- "[Saving and Re-Creating Dimensional Objects with Object Definitions](creating-dimensions-and-cubes.md)"

#### 7.9.2 About EIF Files

You can export objects in an analytic workspace to an EIF file. EIF files are specially formatted files for copying analytic workspaces. You can use EIF files to:

- Backup individual analytic workspaces

- Copy an analytic workspace to another database

EIF files are upwardly compatible among releases of Oracle Database. An EIF file saves the definitions of OLAP DML objects and optionally saves the data also. When you create an EIF file, you can save only the data that you have permission to access.

EIF files do not save object security rules.

You can export and import EIF files for analytic workspaces. You can use EIF files at a more granular level, such as saving just your custom programs, using the OLAP DML.

**See Also:**

- "[Saving and Re-Creating Dimensional Objects with Object Definitions](creating-dimensions-and-cubes.md)"

### 7.10 Cube Materialized Views

A cube materialized view is an Oracle OLAP cube that has been enhanced with the capabilities of a materialized view at build time. Cube materialized views are discussed in the following topics:

- Acquiring Information From the Data Dictionary

- Initiating a Data Refresh

- Refresh Methods

- Using Query Rewrite

- Acquiring Additional Information About Cube Materialized Views

**See Also:**

"[Adding Materialized View Capability to a Cube](creating-dimensions-and-cubes.md)"

#### 7.10.1 Acquiring Information From the Data Dictionary

The data dictionary contains numerous static views that provide information about materialized views. They list cube materialized views along with all other materialized views.

**See Also:**

[Oracle Database Reference](../refrn/ALL_MVIEWS.md) for complete descriptions of the data dictionary views

##### 7.10.1.1 Identifying Cube Materialized Views

`USER_MVIEWS` contains a row for each materialized view owned by the current user. The following query lists the materialized views owned by the `GLOBAL` user. The `CB$` prefix identifies a cube materialized view.

    SELECT mview_name, refresh_mode "MODE", refresh_method "METHOD",
         last_refresh_date "DATE", staleness FROM user_mviews;

    MVIEW_NAME               MODE     METHOD   DATE            STALENESS
    ------------------------ -------- -------- --------------- ----------
    CB$CUSTOMER_MARKET       DEMAND   COMPLETE 20-SEP-12       UNKNOWN
    CB$CHANNEL_PRIMARY       DEMAND   COMPLETE 20-SEP-12       UNKNOWN
    CB$CUSTOMER_SHIPMENTS    DEMAND   COMPLETE 20-SEP-12       UNKNOWN
    CB$PRODUCT_PRIMARY       DEMAND   COMPLETE 20-SEP-12       UNKNOWN
    CB$TIME_CALENDAR         DEMAND   COMPLETE 20-SEP-12       UNKNOWN
    CB$TIME_FISCAL           DEMAND   COMPLETE 20-SEP-12       UNKNOWN
    CB$UNITS_CUBE            DEMAND   FORCE    20-SEP-12       UNKNOWN

    7 rows selected.

The example shows the cube materialized views defined by Analytic Workspace Manager: One for each dimension hierarchy and one for each cube.

##### 7.10.1.2 Identifying the Refresh Logs

Oracle Database can maintain a set of logs on the master tables for the cube materialized views. These logs support incremental (fast) refresh of the cube. The script generated by the Relational Schema Advisor creates a log for each fact and dimension table to record any changes to the data. The following query lists the materialized view logs owned by the `GLOBAL` user:

    SELECT master, log_table FROM user_mview_logs;

    MASTER                         LOG_TABLE
    ------------------------------ ------------------------------
    CHANNEL_DIM                    MLOG$_CHANNEL_DIM
    CUSTOMER_DIM                   MLOG$_CUSTOMER_DIM
    PRODUCT_DIM                    MLOG$_PRODUCT_DIM
    TIME_DIM                       MLOG$_TIME_DIM
    UNITS_FACT                     MLOG$_UNITS_FACT

#### 7.10.2 Initiating a Data Refresh

You can initiate a data refresh of a cube materialized view in several different ways using Analytic Workspace Manager or a PL/SQL package:

- Automatic Refresh: On the Materialized View tab for a cube, you can create a regular schedule for the materialized view refresh subsystem, as described in "[Adding Materialized View Capability to a Cube](creating-dimensions-and-cubes.md)".

- Maintenance Wizard: The Maintenance Wizard is available for refreshing all cubes and dimensions, including cube materialized views.

- `DBMS_CUBE`: The `DBMS_CUBE` PL/SQL package is available for refreshing all cubes, cube dimensions, and cube materialized views.

- `DBMS_MVIEW`: The `DBMS_MVIEW` PL/SQL package contains several procedures for use with cube materialized views.

##### 7.10.2.1 Using DBMS_CUBE

You can use `DBMS_CUBE` to create and populate an analytic workspace or to maintain any cube, including cube materialized views.

The following command initiates a complete refresh of `UNITS_CUBE`, which is enabled as a cube materialized view. It automatically refreshes any stale dimensions before refreshing the cube.

    EXECUTE dbms_cube.build('GLOBAL.UNITS_CUBE');

You can determine the refresh method from `USER_MVIEWS`, as shown in "Identifying Cube Materialized Views".

##### 7.10.2.2 Using DBMS_MVIEW

You can use `DBMS_MVIEW` to refresh all types of materialized views. These refresh procedures can be used with cube materialized views:

- `REFRESH` refreshes a list of one or more materialized views.

- `REFRESH_ALL_MVIEWS` refreshes all materialized views that meet certain criteria.

- `REFRESH_DEPENDENT` refreshes all materialized views that depend on a particular master table and meet certain criteria.

Dimensions must be refreshed before the cube. An error is raised during refresh of a cube materialized view if any of its associated dimension materialized views are stale. The procedures in `DBMS_MVIEW` can refresh multiple materialized views in one call, but they do not guarantee the refresh order. To control the refresh order, call `DBMS_MVIEW.REFRESH` for the cube materialized view separately from its dimension materialized views.

The following command initiates a refresh of the materialized view for the `CHANNEL_PRIMARY` hierarchy.

    EXECUTE dbms_mview.refresh('CB$CHANNEL_PRIMARY', 'C');

#### 7.10.3 Refresh Methods

In Analytic Workspace Manager, you can specify the `COMPLETE`, `FAST`, or `FORCE` methods for refreshing a cube. Two additional methods, `FAST_PCT` and `FAST_SOLVE`, are invoked by the materialized view subsystem. They are not separate choices.

##### 7.10.3.1 Refresh Method Descriptions

Table 7-7 describes the refresh methods that are supported on cube materialized views.

Table 7-7 Refresh Methods For Cube Materialized Views

| Refresh Method | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `COMPLETE`     | Deletes and recreates the cube.<br>This option supports arbitrarily complex mappings from the source tables to the cube.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `FAST`         | Loads and re-aggregates only changed values, based on the materialized view logs or, after direct path loading, on the ALL_SUMDELTA data dictionary view.<br>The source for the refresh is the incremental differences that have been captured in the materialized view logs, rather than the original mapped sources. These differences are used to incrementally rebuild the cube. Only cells that are affected by the changed values are re-aggregated.<br>This option supports only simple mappings for cube materialized views, that is, where no expressions (other than table.column), views, or aggregations occur in the query defining the mapping.<br>The materialized view subsystem determines whether to perform a `FAST` or a `FAST_PCT` refresh. See Oracle Database Data Warehousing Guide for information about the methodology. |
| `FAST_PCT`     | Loads and re-aggregates data only from changed partitions. This method works best when the source table and the cube are partitioned on the same dimension.<br>`FAST_PCT` does not use change logs. The materialized view subsystem determines whether to perform a `FAST` or a `FAST_PCT` refresh. See for information about the methodology.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `FAST_SOLVE`   | Loads and re-aggregates only changed values, based on the original mapped data source.<br>`FAST_SOLVE` is a type of refresh only for cube materialized views. It incrementally re-aggregates the cube even when the refresh source is the original mapped source instead of the materialized view logs. The aggregation subsystem identifies the differences and then incrementally re-aggregates the cube.<br>This option is supported for arbitrarily complex mappings from the source tables to the cube. To discover whether a `FAST_SOLVE` refresh has occurred, review the `CUBE_BUILD_LOG` table as shown in "Fast Solve Refreshes". Or review the `LAST_REFRESH_TYPE` column of `ALL_MVIEWS`; a `FAST_SOLVE` refresh appears as `FAST_CS`.                                                                                                 |
| `FORCE`        | Loads and re-aggregates values using the best method possible.<br>When a `COMPLETE` refresh is not necessary, the materialized view system first attempts a `FAST` refresh. If it cannot `FAST` refresh a cube materialized view, it performs a `FAST_SOLVE` refresh.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### 7.10.3.2 Fast Solve Refreshes

The build log lists the `CLEAR LEAVES` command when the `FAST SOLVE` method was used. Example 7-5 shows the rows of `CUBE_BUILD_LOG` concerned with building `UNITS_CUBE`.

**See Also:**

"Maintenance Logs"

Example 7-5 Identifying a FAST SOLVE Refresh

    SELECT build_object, status, command FROM cube_build_log
         WHERE build_object='UNITS_CUBE'
         AND build_id=8;

    BUILD_OBJECT STATUS     COMMAND
    ------------ ---------- -------------------------
    UNITS_CUBE   STARTED    COMPILE AGGMAP
    UNITS_CUBE   COMPLETED  COMPILE AGGMAP
    UNITS_CUBE   STARTED    UPDATE
    UNITS_CUBE   COMPLETED  UPDATE
    UNITS_CUBE   STARTED    CLEAR LEAVES
    UNITS_CUBE   COMPLETED  CLEAR LEAVES
    UNITS_CUBE   STARTED    LOAD
    UNITS_CUBE   COMPLETED  LOAD
    UNITS_CUBE   STARTED    SOLVE
    UNITS_CUBE   COMPLETED  SOLVE
    UNITS_CUBE   STARTED    UPDATE
    UNITS_CUBE   COMPLETED  UPDATE
    UNITS_CUBE   STARTED    ANALYZE
    UNITS_CUBE   COMPLETED  ANALYZE

    14 rows selected.

#### 7.10.4 Using Query Rewrite

Query rewrite changes a query to select data from the materialized views instead of calculating the result set from the master tables. The transformation is fully transparent to the client, and requires no mention of the materialized views in the SQL statement. In the case of cube materialized views, the query is written against the tables or views of a star or snowflake schema, and it is transformed into a query against a cube materialized view. This transformation can result in significant improvements in run-time performance.

Query rewrite requires optimizer statistics on the cubes and dimensions. You can discover whether a query is rewritten by generating and examining its execution plan.

Oracle Database uses two initialization parameters to control query rewrite:

- `QUERY_REWRITE_ENABLED`: Enables or disables query rewrite globally for the database.

- `QUERY_REWRITE_INTEGRITY`: Determines the degree to which query rewrite monitors the consistency of materialized views with the source data. The `trusted` or `stale tolerated` settings are recommended when using rewrite to cube materialized views.

Administration of cube materialized views is the same as any other materialized view except that the cube materialized views must be in the same schema as the analytic workspace. Users require the `GLOBAL QUERY REWRITE` privilege to have rewrite to materialized views that are in schemas other than their own. However, the owner can access the materialized views from any schema without additional privileges.

**See Also:**

- "Analyzing Cubes and Dimensions" for information about optimizer statistics

- [Viewing Execution Plans](querying-dimensional-objects.md) for information about execution plans

- [Oracle Database Reference](../refrn/QUERY_REWRITE_ENABLED.md) for complete descriptions of the initialization parameters

#### 7.10.5 Acquiring Additional Information About Cube Materialized Views

Oracle Database has numerous PL/SQL packages for managing materialized views. Cube materialized views are optimized to provide the best performance, so you have no need to use most of these packages. Few design decisions remain for you to make. For this reason, the `TUNE_MVIEW` procedure of `DBMS_ADVISOR` is disabled for cube materialized views.

However, there are a few packages that you may find useful, as shown in Table 7-8.

Table 7-8 PL/SQL Packages for Cube Materialized Views

| Package                                      | Description                                                                                                                                                                                                                                                                                      |
|:---------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [`DBMS_METADATA`](../arpls/DBMS_METADATA.md) | Returns the metadata for an object.                                                                                                                                                                                                                                                              |
| [`DBMS_MVIEW`](../arpls/DBMS_MVIEW.md)       | Executes data refreshes. See "Initiating a Data Refresh".<br>You can use the `EXPLAIN_REWRITE` and `EXPLAIN_MVIEW` procedures to obtain information about cube materialized views. `EXPLAIN_MVIEW` is particular useful for evaluating and explaining the `FAST` refresh capabilities of a cube. |
| [`DBMS_XPLAN`](../arpls/DBMS_XPLAN.md)       | Displays an execution plan. See "[Viewing Execution Plans](querying-dimensional-objects.md)".                                                                                                                                                                                                    |
