This chapter describes how to capture a database workload on the production system. The first step in using Database Replay is to capture the production workload.

This chapter contains the following sections:

- Prerequisites for Capturing a Database Workload

- Setting Up the Capture Directory

- Workload Capture Options

- Workload Capture Restrictions

- Enabling and Disabling the Workload Capture Feature

- Enterprise Manager Privileges and Roles

- Capturing a Database Workload Using Enterprise Manager

- Capturing Workloads from Multiple Databases Concurrently

- Monitoring a Workload Capture Using Enterprise Manager

- Importing a Workload External to Enterprise Manager

- Creating Subsets from an Existing Workload

- Copying or Moving a Workload to a New Location

- Capturing a Database Workload Using APIs

- Encrypting and Decrypting an Existing Workload Capture Using APIs

- Monitoring Workload Capture Using Views

**See Also:**

"[Workload Capture](introduction-to-database-replay.md)" for more information about how capturing a database workload fits within the Database Replay architecture

### Prerequisites for Capturing a Database Workload

Before starting a workload capture, you should have a strategy in place to restore the database on the test system. Before a workload can be replayed, the logical state of the application data on the replay system should be similar to that of the capture system when replay begins. To accomplish this, consider using one of the following methods:

- Recovery Manager (RMAN) `DUPLICATE` command

- Snapshot standby

- Data Pump Import and Export

This will allow you to restore the database on the replay system to the application state as of the workload capture start time.

If the database is protected by Database Vault, then you need to be authorized to use the `DBMS_WORKLOAD_CAPTURE` and `DBMS_WORKLOAD_REPLAY` packages in a Database Vault environment before you can use Database Replay.

**See Also:**

- [Oracle Database Vault Administrator’s Guide](../dvadm/dba-operations-in-an-oracle-database-vault-environment.md) for information about using Database Replay in a Database Vault environment

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-duplicating-databases.md) for information about duplicating databases with RMAN

- [Oracle Data Guard Concepts and Administration](../sbydb/managing-oracle-data-guard-physical-standby-databases.md) for information about managing snapshot standby databases

- [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for information about using Data Pump

### Setting Up the Capture Directory

Determine the location and set up a directory where the captured workload will be stored. Before starting the workload capture, ensure that the directory is empty and has ample disk space to store the workload. If the directory runs out of disk space during a workload capture, the capture will stop. To estimate the amount of disk space that is required, you can run a test capture on your workload for a short duration (such as a few minutes) to extrapolate how much space you will need for a full capture. To avoid potential performance issues, you should also ensure that the target replay directory is mounted on a separate file system.

For Oracle RAC, consider using a shared file system. Alternatively, you can set up one capture directory path that resolves to separate physical directories on each instance, but you will need to consolidate the files created in each of these directories into a single directory. For captures on an Oracle RAC database, Enterprise Manager only supports Oracle RAC configured with a shared file system. The entire content of the local capture directories on each instance (not only the capture files) must be copied to the shared directory before it can be used for preprocessing. For example, assume that you are:

- Running an Oracle RAC environment in Linux with two database instances named `host1` and `host2`

- Using a capture directory object named `CAPDIR` that resolves to `/$ORACLE_HOME/rdbms/capture` on both instances

- Using a shared directory that resides in `/nfs/rac_capture`

You will need to login into each host and run the following command:

    cp -r /$ORACLE_HOME/rdbms/capture/* /nfs/rac_capture

After this is done for both instances, the `/nfs/rac_capture` shared directory is ready to be preprocessed or masked.

### Workload Capture Options

Proper planning before workload capture is required to ensure that the capture will be accurate and useful when replayed in another environment.

Before capturing a database workload, carefully consider the following options:

- Restarting the Database

- Using Filters with Workload Capture

#### Restarting the Database

While this step is not required, Oracle recommends that the database be restarted before capturing the workload to ensure that ongoing and dependent transactions are allowed to be completed or rolled back before the capture begins. If the database is not restarted before the capture begins, transactions that are in progress or have yet to be committed will not be fully captured in the workload. Ongoing transactions will thus not be replayed properly, because only the part of the transaction whose calls were captured will be replayed. This may result in undesired replay divergence when the workload is replayed. Any subsequent transactions with dependencies on the incomplete transactions may also generate errors during replay. On a busy system, it is normal to see some replay divergence, but the replay can still be used to perform meaningful analysis of a system change if the diverged calls do not make up a significant portion of the replay in terms of DB time and other such key attributes.

Before restarting the database, determine an appropriate time to shut down the production database before the workload capture when it is the least disruptive. For example, you may want to capture a workload that begins at 8:00 a.m. However, to avoid service interruption during normal business hours, you may not want to restart the database during this time. In this case, you should consider starting the workload capture at an earlier time, so that the database can be restarted at a time that is less disruptive.

Once the database is restarted, it is important to start the workload capture before any user sessions reconnect and start issuing any workload. Otherwise, transactions performed by these user sessions will not be replayed properly in subsequent database replays, because only the part of the transaction whose calls were executed after the workload capture is started will be replayed. To avoid this problem, consider restarting the database in `RESTRICTED` mode using `STARTUP RESTRICT`, which will only allow the `SYS` user to login and start the workload capture. By default, once the workload capture begins, any database instance that are in `RESTRICTED` mode will automatically switch to `UNRESTRICTED` mode, and normal operations can continue while the workload is being captured.

Only one workload capture can be performed at any given time. If you have a Oracle Real Application Clusters (Oracle RAC) configuration, workload capture is performed for the entire database. Once you enable capture for one of the Oracle RAC nodes, workload capture is started on all database instances (the workload capture process is Oracle RAC aware). Although it is not required, restarting all instances in a Oracle RAC configuration before workload capture is recommended to avoid capturing ongoing transactions.

##### To restart all instances in a Oracle RAC configuration before workload capture:

1.  Shut down all the instances.
2.  Restart all the instances.
3.  Start workload capture.
4.  Connect the application and start the user workload.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/starting-up-and-shutting-down.md) for information about restricting access to an instance at startup

#### Using Filters with Workload Capture

By default, all user sessions are recorded during workload capture. You can use workload filters to specify which user sessions to include in or exclude from the workload during workload capture. There are two types of workload filters: inclusion filters and exclusion filters. You can use either inclusion filters or exclusion filters in a workload capture, but not both.

Inclusion filters enable you to specify user sessions that will be captured in the workload. This is useful if you want to capture only a subset of the database workload.

Exclusion filters enable you to specify user sessions that will not be captured in the workload. This is useful if you want to filter out session types that do not need to captured in the workload, such as those that monitor the infrastructure—like Oracle Enterprise Manager (EM) or Statspack—or other such processes that are already running on the test system. For example, if the system where the workload will be replayed is running EM, replaying captured EM sessions on the system will result in duplication of workload. In this case, you may want to use exclusion filters to filter out EM sessions.

### Workload Capture Restrictions

Certain types of user sessions and client requests may sometimes be captured in a workload, but they are not supported by Database Replay. Capturing these session and request types in a workload may result in errors during workload replay.

The following types of user sessions and client requests are not supported by Database Replay:

- Direct path load of data from external files using utilities such as SQL\*Loader

- Non-PL/SQL based Advanced Queuing (AQ)

- Flashback queries

- Oracle Call Interface (OCI) based object navigations

- Non SQL-based object access

- Distributed transactions

  Any distributed transactions that are captured will be replayed as local transactions.

- XA transactions

  XA transactions are not captured or replayed. All local transactions are captured.

- `JAVA_XA` transactions

  If the workload uses the `JAVA_XA` package, `JAVA_XA` function and procedure calls are captured as normal PL/SQL workload. To avoid problems during workload replay, consider dropping the `JAVA_XA` package on the replay system to enable the replay to complete successfully.

- Database Resident Connection Pooling (DRCP)

- Workloads using OUT binds

- Multi-threaded Server (MTS) and shared server sessions with synchronization mode set to `OBJECT_ID`

- Migrated sessions

  The workload is captured for migrated sessions. However, user logins or session migration operations are not captured. Without a valid user login or session migration, the replay may cause errors because the workload may be replayed by a wrong user.

Typically, Database Replay refrains from capturing these types of non-supported user sessions and client requests. Even when they are captured, Database Replay will not replay them. Therefore, it is usually not necessary to manually filter out non-supported user sessions and client requests. In cases where they are captured and found to cause errors during replay, consider using workload capture filters to exclude them from the workload.

**See Also:**

- "Using Filters with Workload Capture" for information about using workload capture filters

- "[Using Filters with Workload Replay](replaying-a-database-workload.md)" for information about using workload replay filters

### Enabling and Disabling the Workload Capture Feature

Database Replay supports capturing a database workload on a system running Oracle Database 10g Release 2 that can be used to test database upgrades to Oracle Database 11g and subsequent releases. By default, the workload capture feature is not enabled in Oracle Database 10g Release 2 (10.2). You can enable or disable this feature by specifying the `PRE_11G_ENABLE_CAPTURE` initialization parameter.

**Note:**

It is only necessary to enable the workload capture feature if you are capturing a database workload on a system running Oracle Database 10g Release 2.

If you are capturing a database workload on a system running Oracle Database 11g Release 1 or a later release, it is not necessary to enable the workload capture feature because it is enabled by default. Furthermore, the `PRE_11G_ENABLE_CAPTURE` initialization parameter is only valid with Oracle Database 10g Release 2 (10.2) and cannot be used with subsequent releases.

To enable the workload capture feature on a system running Oracle Database 10g Release 2, run the `wrrenbl.sql` script at the SQL prompt:

    @$ORACLE_HOME/rdbms/admin/wrrenbl.sql

The `wrrenbl.sql` script calls the `ALTER SYSTEM` SQL statement to set the `PRE_11G_ENABLE_CAPTURE` initialization parameter to `TRUE`. If a server parameter file (spfile) is being used, the `PRE_11G_ENABLE_CAPTURE` initialization parameter will be modified for the currently running instance and recorded in the spfile, so that the new setting will persist when the database is restarted. If a spfile is not being used, the `PRE_11G_ENABLE_CAPTURE` initialization parameter will only be modified for the currently running instance, and the new setting will not persist when the database is restarted. To make the setting persistent without using a spfile, you will need to manually specify the parameter in the initialization parameter file (`init.ora`).

To disable workload capture, run the `wrrdsbl.sql` script at the SQL prompt:

    @$ORACLE_HOME/rdbms/admin/wrrdsbl.sql

The `wrrdsbl.sql` script calls the `ALTER SYSTEM` SQL statement to set the `PRE_11G_ENABLE_CAPTURE` initialization parameter to `FALSE`. If a server parameter file (spfile) is being used, the `PRE_11G_ENABLE_CAPTURE` initialization parameter will be modified for the currently running instance and also recorded in the spfile, so that the new setting will persist when the database is restarted. If a spfile is not being used, the `PRE_11G_ENABLE_CAPTURE` initialization parameter will only be modified for the currently running instance, and the new setting will not persist when the database is restarted. To make the setting persistent without using a spfile, you will need to manually specify the parameter in the initialization parameter file (`init.ora`).

**Note:**

The `PRE_11G_ENABLE_CAPTURE` initialization parameter can only be used with Oracle Database 10g Release 2 (10.2). This parameter is not valid in subsequent releases. After upgrading the database, you will need to remove the parameter from the server parameter file (spfile) or the initialization parameter file (`init.ora`); otherwise, the database will fail to start up.

### Enterprise Manager Privileges and Roles

The Database Replay resource type privileges enable you to view or operate any Database Replay entities. Additionally, you need the target operator privilege for the target from which the workload was captured to access the entities associated with the workload. For a target that does not exist anymore, the Enterprise Manager user who owns the entities or the Enterprise Manager super user can still access the entities.

The two security roles discussed in the following sections make it easier to grant or revoke privileges related to Database Replay entities.

#### Database Replay Viewer Role

Users who have the Database Replay Viewer role can view any Database Replay entity. By default, no Enterprise Manager user is granted this role. However, the EM_ALL_VIEWER role includes this role by default.

The Database Replay Viewer role consists of the Database Replay Viewer (resource type) privilege.

#### Database Replay Operator Role

The Database Replay Operator role includes the Database Replay Viewer role and thus its privileges. Users who have the Database Replay Operator role can also edit and delete any Database Replay entity. By default, no Enterprise Manager user is granted this role. However, the EM_ALL_OPERATOR role includes this role by default.

The Database Replay Operator role consists of the following privileges:

- Database Replay Operator (resource type privilege)

- Create new Named Credential (resource type privilege)

- Create new job (resource type privilege)

- Connect to any viewable target (target type privilege)

- Execute Command Anywhere (target type privilege)

To capture or replay a workload on a database target, an Enterprise Manager user needs all the privileges granted by the Database Replay Operator role plus the target operator privilege for the database target.

### Capturing a Database Workload Using Enterprise Manager

This section describes how to capture a database workload using Enterprise Manager. The primary tool for capturing database workloads is Oracle Enterprise Manager.

For information about the prerequisites, see "Prerequisites for Capturing a Database Workload".

**Tip:**

If Oracle Enterprise Manager is unavailable, you can capture database workloads using APIs, as described in "Capturing a Database Workload Using APIs".

#### To capture a database workload using Enterprise Manager:

1.  From the Enterprise menu of the Enterprise Manager Cloud Control console, select Quality Management, then Database Replay.
    If the Database Login page appears, log in as a user with administrator privileges.

    The Database Replay page appears.

    ![Description of dbr.gif follows](img/dbr.gif)
    [Description of the illustration dbr.gif](img_text/dbr.md)
2.  From the Database Replay page, click the Captured Workloads tab, then click Create in the toolbar.
    The Create Capture: Plan Environment page appears.

    ![Description of dbr_capture_plan_env.gif follows](img/dbr_capture_plan_env.gif)
    [Description of the illustration dbr_capture_plan_env.gif](img_text/dbr_capture_plan_env.md)
3.  Verify that you have met both prerequisites described on this page, then enable both checkboxes and click Next.
    The Create Capture: Database page appears.

    ![Description of dbr_capture_databases.gif follows](img/dbr_capture_databases.gif)
    [Description of the illustration dbr_capture_databases.gif](img_text/dbr_capture_databases.md)
4.  Click Add.
    The Add pop-up appears.
5.  Provide a capture name, provide an optional description, then click the Target Database search icon.
    The Search and Select: Targets pop-up appears.

    ![Description of dbr_capture_select_db.gif follows](img/dbr_capture_select_db.gif)
    [Description of the illustration dbr_capture_select_db.gif](img_text/dbr_capture_select_db.md)
6.  Select a Target Type, optionally provide a configuration search, choose a target database from the list, then click Select.
    The Add pop-up reappears with added sections for Database Credential and Database Host Credential.

    ![Description of dbr_capture_add_db.gif follows](img/dbr_capture_add_db.gif)
    [Description of the illustration dbr_capture_add_db.gif](img_text/dbr_capture_add_db.md)
7.  Provide database credentials, database host credentials, a Database Capture Intermediate Storage Location, then click OK.
    - After the Capture, the files are copied to the storage location, unless you use the intermediate storage location as the final storage location.

      **Note:**

      For captures on an Oracle RAC database, Enterprise Manager only supports Oracle RAC configured with a shared file system.

    The selected target database now appears in the list of databases in the Select Production Databases table.
8.  Click Next.
    The Create Capture: Options page appears.

    ![Description of dbr_capture_options.gif follows](img/dbr_capture_options.gif)
    [Description of the illustration dbr_capture_options.gif](img_text/dbr_capture_options.md)
9.  Select the workload capture options:
    - Under the SQL Performance Analyzer section, select whether to capture SQL statements into a SQL tuning set during workload capture.

      While Database Replay provides an analysis of how a change affects your entire system, you can use a SQL tuning set in conjunction with the SQL Performance Analyzer to gain a more SQL-centric analysis of how the change affects SQL statements and execution plans.

      By capturing a SQL tuning set during workload capture and another SQL tuning set during workload replay, you can use the SQL Performance Analyzer to compare these SQL tuning sets to each other without having to re-execute the SQL statements. This enables you to obtain a SQL Performance Analyzer report and compare the SQL performance, before and after changes, while running Database Replay.

      **Note:**

      Capturing SQL statements into a SQL Tuning Set is the default, and is the recommended workload capture option. Capturing SQL statements into a SQL Tuning Set is not available for Oracle RAC.

      **Tip:**

      For information about comparing SQL tuning sets using SQL Performance Analyzer reports, see "[Generating SQL Performance Analyzer Reports Using APIs](analyzing-captured-and-replayed-workloads.md)".

    - Under the Workload Filters section, select whether to use exclusion filters by selecting Exclusion in the Filter Mode list, or inclusion filters by selecting Inclusion in the Filter Mode list.

      To add filters, click Add and enter the filter name, session attribute, and value in the corresponding fields.

      **Tip:**

      For more information, see "Using Filters with Workload Capture".

    After selecting the desired workload capture options, click Next.

    The Create Capture: Storage page appears.

    ![Description of dbr_capture_storage.gif follows](img/dbr_capture_storage.gif)
    [Description of the illustration dbr_capture_storage.gif](img_text/dbr_capture_storage.md)
10. Click the Storage Host icon, choose a target from the list, then click Select.
    The Storage page now requests Host Credentials and a Storage Location.
11. Provide Host Credentials, click Browse to select a Storage Location, select the location and click OK, then click Next.
    The Create Capture: Schedule page appears.

    ![Description of dbr_capture_schedule.gif follows](img/dbr_capture_schedule.gif)
    [Description of the illustration dbr_capture_schedule.gif](img_text/dbr_capture_schedule.md)
12. Schedule the starting time and duration for the capture, schedule the exporting of AWR data, then click Next.
    - The default capture duration is 5 minutes. Change the capture duration to capture representative activity over a time period of interest that needs to be tested.

    The Create Capture: Review page appears.

    ![Description of dbr_capture_review.gif follows](img/dbr_capture_review.gif)
    [Description of the illustration dbr_capture_review.gif](img_text/dbr_capture_review.md)
13. If all of the parameters appear as you have intended, click Submit to start the capture job.
    - The "Capture SQL statements into a SQL Tuning Set during workload capture" option is enabled by default. Uncheck this option if you do not want to compare SQL tuning sets at the end of the Replay.

    The Database Replay page reappears, displays a message that the capture was created successfully, and displays the status of the capture in the Captures list, such as "Scheduled."
14. For detailed information about the capture, double-click the name of the capture.
    The Capture Summary page appears, and displays several attributes, including the average active sessions, a workload comparison, and related concurrent captures, if any.

**Tip:**

After capturing a workload on the production system, you need to preprocess the captured workload, as described in [Preprocessing a Database Workload](preprocessing-a-database-workload.md).

### Capturing Workloads from Multiple Databases Concurrently

Concurrent capture refers to capturing the workload on multiple databases simultaneously.

#### To capture a concurrent database replay workload:

1.  From the Enterprise menu of the Enterprise Manager Cloud Control console, select Quality Management, then Database Replay.

    If the Database Login page appears, log in as a user with administrator privileges.

    The Database Replay page appears.

2.  From the Database Replay page, click the Captured Workloads tab, then click Create in the toolbar.

    The Create Capture: Plan Environment page appears.

3.  Make sure that you have met both prerequisites described on this page, then enable both checkboxes and click Next.

    The Create Capture: Database page appears.

    **Tip:**

    For information about the prerequisites, see "Prerequisites for Capturing a Database Workload".

4.  Click Add.

    The Add pop-up appears.

5.  Provide a Capture name, provide an optional description, then click the Target Database search icon.

    The Search and Select: Targets pop-up appears.

6.  Choose a target database from the list, then click Select.

    The Add pop-up reappears with added sections for Database Credential and Database Host Credential.

7.  Provide database credentials, database host credentials, a Database Capture Intermediate Storage Location, then click OK.

    - After the Capture, the files are copied to the storage location, unless you use the intermediate storage location as the final storage location.

    The selected target database now appears in the list of databases in the Select Production Databases table.

8.  Add another database for concurrent capture:

    1.  Follow the instructions in steps 4 through 7.

        The Create Capture: Database page reappears, and displays the additional database for capture along with the first database you specified in steps 4 through 7.

    2.  Provide a name and optional description for the concurrent capture, then click Next.

        The Create Capture: Options page appears.

9.  Select the workload capture options:

    - Under the SQL Performance Analyzer section, select whether to capture SQL statements into a SQL tuning set during workload capture.

      While Database Replay provides an analysis of how a change affects your entire system, you can use a SQL tuning set in conjunction with the SQL Performance Analyzer to gain a more SQL-centric analysis of how the change affects SQL statements and execution plans.

      By capturing a SQL tuning set during workload capture and another SQL tuning set during workload replay, you can use the SQL Performance Analyzer to compare these SQL tuning sets to each other without having to re-execute the SQL statements. This enables you to obtain a SQL Performance Analyzer report and compare the SQL performance, before and after changes, while running Database Replay.

      **Note:**

      Capturing SQL statements into a SQL tuning set is the default and recommended workload capture option.

    - Under the Workload Filters section, select whether to use exclusion filters by selecting Exclusion in the Filter Mode list, or inclusion filters by selecting Inclusion in the Filter Mode list.

      To add filters, click Add and enter the filter name, session attribute, and value in the corresponding fields.

    After selecting the desired workload capture options, click Next.

    The Create Capture: Storage page appears.

10. Click the Storage Host icon, choose a target from the list, then click Select.

    The Storage page now requests Host Credentials and a Storage Location.

11. Provide Host Credentials, click Browse to select a Storage Location, then click Next.

    The Create Capture: Schedule page appears.

12. Schedule the starting time and duration for the capture, schedule the exporting of AWR data, then click Next.

    - The default capture duration is 5 minutes. Change the capture duration to capture representative activity over a time period of interest that needs to be tested.

    The Create Capture: Review page appears.

13. If all of the parameters appear as you have intended, click Submit to start the Capture job.

    - The "Capture SQL statements into a SQL Tuning Set during workload capture" option is enabled by default. Uncheck this option if you do not want to compare SQL tuning sets at the end of the Replay.

    The Database Replay page reappears, displays a message that the capture was created successfully, and displays the status of the capture in the Captures list, such as "Scheduled."

14. For detailed information about the capture, double-click the name of the capture.

    The Capture Summary page appears, and displays several attributes, including the average active sessions, a workload comparison, and related concurrent captures.

### Monitoring a Workload Capture Using Enterprise Manager

This section describes how to monitor workload capture using Enterprise Manager. The primary tool for monitoring workload capture is Oracle Enterprise Manager. Using Enterprise Manager, you can:

- Monitor or stop an active workload capture

- View a completed workload capture

**Tip:**

If Oracle Enterprise Manager is unavailable, you can monitor workload capture using views, as described in "Monitoring Workload Capture Using Views".

This section contains the following topics:

- Monitoring an Active Workload Capture

- Stopping an Active Workload Capture

- Viewing a Completed Workload Capture

#### Monitoring an Active Workload Capture

This section describes how to monitor an active workload capture using Enterprise Manager.

##### To monitor an active workload capture:

1.  From the Enterprise menu of the Enterprise Manager Cloud Control console, select Quality Management, then Database Replay.
    If the Database Login page appears, log in as a user with administrator privileges.

    The Database Replay page appears.
2.  From the Captured Workloads tab of the Database Replay page for a capture that has a Status other than Completed, click the name of the desired capture from the Capture table.
    The Summary tab of the Database Replay page appears, showing detailed statistics, a chart for average active sessions that updates dynamically while the capture is in progress, a comparison of data for captured elements versus the same elements not captured, and related concurrent captures, if any.

    - The Not Captured data shown in the Active Average Sessions chart shows the database activity (database sessions) that is not being captured.

    - The values for the Total column in the Comparison section shows all of the captured and uncaptured activity in the database. Filtering, as determined by the Workload Filters you provided in the Options step of the Create Capture wizard, is primarily why some activity is captured or not. Additionally, background activities, database scheduler jobs, and unreplayable calls are not captured.

    - You can click the refresh icon in the upper right corner to update the capture while it is running.
3.  To return to the Database Replay page, click the Database Replay breadcrumb.

#### Stopping an Active Workload Capture

This section describes how to stop an active workload capture using Enterprise Manager.

##### To stop an active workload capture:

1.  From the Enterprise menu of the Enterprise Manager Cloud Control console, select Quality Management, then Database Replay.
    If the Database Login page appears, log in as a user with administrator privileges.

    The Database Replay page appears.
2.  From the Captured Workloads tab of the Database Replay page for a capture that has a Status of Draft, click the name in the Capture table of the capture you want to stop.
    The Capture Summary page appears.
3.  Click the Stop Capture button.
    The button label changes to Stopping Capture. When the process completes, the Status changes to Stopped.

#### Viewing a Completed Workload Capture

This section describes how to manage a completed workload capture using Enterprise Manager.

##### To view a completed workload capture:

1.  From the Enterprise menu of the Enterprise Manager Cloud Control console, select Quality Management, then Database Replay.
    If the Database Login page appears, log in as a user with administrator privileges.

    The Database Replay page appears.
2.  From the Capture Workloads tab of the Database Replay page, click the name of a capture that has a Status of Completed.
    The contents of the Summary tab of the Database Replay page appears as for a capture in progress, except the Average Active Sessions chart shows aggregated data for the capture time period, rather than dynamic data recorded during the capture.

    ![Description of dbr_capture_view.gif follows](img/dbr_capture_view.gif)
    [Description of the illustration dbr_capture_view.gif](img_text/dbr_capture_view.md)
    The Average Active Sessions chart provides a graphic display of the captured session activity compared to the uncaptured session activity (such as background activities or filtered sessions). This chart appears only when Active Session History (ASH) data is available for the capture period.

    Under Comparison, various statistics for the workload capture are displayed:

    - Capture column

      Displays the statistics for the captured session activity.

    - Total column

      Displays the statistics for the total session activity.

    - Percentage of Total column

      Displays the percentage of total session activity that has been captured in the workload.
3.  To return to the Database Replay page, click the Database Replay breadcrumb.

**Tip:**

See [Analyzing Captured and Replayed Workloads](analyzing-captured-and-replayed-workloads.md) for information about accessing workload capture reports.

### Importing a Workload External to Enterprise Manager

You can import a workload captured through the PL/SQL interface or through a different Enterprise Manager instance into Enterprise Manager to manage it as you would for a workload originally created within Enterprise Manager. The workload can be in the process of being captured, or the Capture can be completed and the workload stored on a file system. You can also preprocess and replay the workload as you would ordinarily do for a workload created within Enterprise Manager.

This feature is available for Cloud Control Database plug-in 12.1.0.5 and later releases.

#### To import a database workload external to Enterprise Manager:

1.  From the Database Replay page, click the Captured Workloads tab, then click Import in the toolbar.

    The Import Workload: Source page appears.

2.  Select one of the three choices available to import a captured workload, then click Next:

    - Import a completed captured workload from a directory in the file system

      This option typically applies for a workload created using an API, in which you now want to import it to Enterprise Manager for subsequent processing. In this case, Enterprise Manager may not even be managing the Capture database.

    - Import a completed captured workload from a database target

      In this case, Enterprise Manager is probably already managing the Capture database. The Capture could have been done on this database, or it could have been loaded in as would be the case for the option above.

    - Attach to a Capture running in a database target

      This option is similar to the option above, except this a Capture that is still in progress, rather than one that has already completed.

    The Import Workload: Database page appears.

3.  Click the search icon next to the Database Target field and select a database from the pop-up that appears.

    **Note:**

    The target version of the database loading the workload must be at least as high as the one you used to capture the workload. For instance, if you captured using Oracle Database 12x, the database you select to read the Capture must be at least version 12x.

    - The system now requests database and host credentials.

    - In the previous step, if you chose to import a completed captured workload from a directory in the file system, the system also requires a workload location.

    - A consolidated Replay has a different directory structure in which there are at least two capture directories. Consequently, if the workload directory contains a consolidated Replay, you need to enable the check box so that Enterprise Manager can be aware of the consolidated Replay during the import operation.

4.  Provide the requisite input for the step above, then click Next.

    The Import Workload: Workload page appears.

    - If you chose "Import a completed captured workload from a directory in the file system" in step 2, this page provides a Load Workload button.

    - If you chose “Import a completed captured workload from a database target" or “Attach to a Capture running in a database target" in step 2, this page provides a Discover Workload button.

5.  Click either Load Workload or Discover Workload, depending on which button is available in accordance with your selection in step 2.

    The system displays workloads, if found, in the Discovered Workloads table.

6.  Either click Next to load the workload, or select one of the workloads, then click Next to continue importing the workload.

    The Import Workload: Replay page appears only under the following conditions:

    - You chose "Import a completed captured workload from a directory in the file system" in step 2.

    - The workload contains one or more Replays.

7.  Optional: Select one or more Replays, if desired, provide a Replay Task Name, then click Next.

    The Import Workload: Review page appears.

8.  If everything appears as you have intended, click Submit.

    The Database Replay page reappears and displays a message stating that the job was submitted successfully. The Status column for your loaded or imported workload in the Captured Workload table will show In Progress.

    **Tip:**

    You can check on the job's progress by clicking on the captured workload name that you just submitted in the Review step. A Capture Summary page appears, and you can click the Database Replay Import Job link to see the progress of the job execution steps.

### Creating Subsets from an Existing Workload

For cases in which you have captured a large workload covering a long period of time, you may only want to replay a portion of it to accelerate testing. The Database Replay Workload Subsetting feature enables you to create new workloads by extracting portions of an existing captured workload.

Enterprise Manager provides a wizard to extract a subset of data from an existing workload that you can use for Replay on a test system. Each extracted subset is a legitimate workload that can be replayed on its own or with other workloads in a consolidated Replay.

To perform a Replay, you need to preprocess the workloads.

This feature is available for Cloud Control Database plug-in 12.1.0.5 and later releases.

#### To extract subsets from a workload:

1.  From the Captured Workloads tab of the Database Replay page, select a workload for which you want to extract a subset, then click Subset.

    The Subset Workload: Define page appears, showing an Active Sessions History chart for the workload.

2.  Select a starting and ending time for the subset you want to extract from the workload:

    1.  Click Add above the Subsets table at the bottom of the page.

        The Create Subset pop-up appears.

    2.  Select either snapshot or calendar times, provide start and end times, then click OK.

        **Note:**

        Snapshot time is the preferred choice, because not all performance data may be available for the calendar time you select.

        Your selected time period now appears in the Active Sessions chart as a greyed-out segment.

    3.  Optional: Define one or more additional subsets with different time periods than those you selected in the step above.

    4.  Optional: In the Advanced Parameters section, indicate whether you want to include incomplete calls after the subset workload ends. The default is to include incomplete calls when the subset workload begins.

        - These parameters enable you to include the calls outside of your defined boundaries. For example, when you specify a starting and ending time as the boundaries for a transaction, the transaction may have started before your indicated start time, and may also have continued after your indicated end time.

3.  Click Next.

    The Subset Workload: Database page appears.

4.  Click the search icon next to the Database Target field and select a database for subsetting from the Search and Select: Targets pop-up that appears.

    The system now requests database and host credentials.

5.  Provide the requisite input for the step above, then click Next.

    The Subset Workload: Location page appears.

    - If the source host and staged database host are the same, the location is pre-populated, so you do not need to provide the location for the source workload files.

    - If the source host and staged database host are not the same, do the following:

      1.  Choose whether you want to access the workload files from the host name shown in the Host field, or whether you want to copy the files from the source host to the Destination Host shown.

          Access Directly means that the database to be used to subset the workload can access the original workload directly using the specified file system location. This is typically the case when the original workload is stored at a network shared location.

          Access Copy means that the two hosts are not in the shared network path. You need to provide the source host credentials so that Enterprise Manager can copy the original workload from its current location to the specified location on the subset database host.

      2.  Depending on your choice above, either provide the directory location containing the workload files, or provide the location for the destination host.

6.  In the Subset field, specify the storage location for each subset, then click Next.

    The Subset Workload: Schedule page appears.

7.  Indicate when you want to start the subset job, then click Next.

    The Subset Workload: Review page appears.

8.  If everything appears as you have intended, click Submit.

    The Database Replay page reappears and displays a message stating that the job was submitted successfully. The Status column for your subset in the Replay Tasks table will show In Progress.

    **Tip:**

    You can check on the job's progress by clicking on the subset name that you just submitted in the Review step. A Capture Summary page appears, and you can click the Database Replay Subset Job link to see the progress of the job execution steps.

### Copying or Moving a Workload to a New Location

You can use the copy function for two purposes. The purposes are:

- Duplicate the Capture files from the source to another host and location.

- Move the Capture files to a new host and location, and delete the source files from the original location.

This feature is available for Cloud Control Database plug-in 12.1.0.5 and later releases.

#### To copy a workload to a new location:

1.  From the Captured Workloads tab of the Database Replay page, select a workload you want to copy to a new location, then click Copy.

    The Copy Workload page appears, and displays the current source location of the workload directory you selected.

2.  Provide or change credentials for the storage host, if necessary. The system automatically picks up the previously defined credentials for the current storage host.

3.  Leave the After Copy radio button enabled, which is "Keep original workload in the source location."

4.  Select the Storage Host for the new location of the workload directory.

5.  Provide credentials for the new storage host.

6.  Select the directory for the new Destination Location for the workload.

7.  Schedule the job, then click Submit.

    The Database Replay page reappears and displays a message stating that the job was submitted and that the storage location has been updated successfully.

    **Tip:**

    You can check on the job's progress by going to the Job Activity page, searching for the job name that appeared in the submit message, then clicking its link to access the Job Run page.

### Capturing a Database Workload Using APIs

This section describes how to capture a database workload using APIs. You can also use Oracle Enterprise Manager to capture database workloads, as described in "Capturing a Database Workload Using Enterprise Manager".

Capturing a database workload using the `DBMS_WORKLOAD_CAPTURE` package involves:

- Defining Workload Capture Filters

- Starting a Workload Capture

- Stopping a Workload Capture

- Exporting AWR Data for Workload Capture

- Importing AWR Data for Workload Capture

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_CAPTURE.md) for information about the `DBMS_WORKLOAD_CAPTURE` package

#### Defining Workload Capture Filters

This section describes how to add and remove workload capture filters. For information about using workload filters with workload capture, see "Using Filters with Workload Capture".

##### To add filters to a workload capture:

- Use the `ADD_FILTER` procedure:

      BEGIN
        DBMS_WORKLOAD_CAPTURE.ADD_FILTER (
                                 fname => 'user_ichan',
                                 fattribute => 'USER',
                                 fvalue => 'ICHAN');
      END;
      /

  In this example, the `ADD_FILTER` procedure adds a filter named user_ichan, which can be used to filter out all sessions belonging to the user name ICHAN.

  The `ADD_FILTER` procedure in this example uses the following parameters:

  - The `fname` required parameter specifies the name of the filter that will be added.

  - The `fattribute` required parameter specifies the attribute on which the filter will be applied. Valid values include PROGRAM, MODULE, ACTION, SERVICE, INSTANCE_NUMBER, and USER.

  - The `fvalue` required parameter specifies the value for the corresponding attribute on which the filter will be applied. It is possible to use wildcards such as % with some of the attributes, such as modules and actions.

##### To remove filters from a workload capture:

- Use the `DELETE_FILTER` procedure:

      BEGIN
        DBMS_WORKLOAD_CAPTURE.DELETE_FILTER (fname => 'user_ichan');
      END;
      /

  In this example, the `DELETE_FILTER` procedure removes the filter named user_ichan from the workload capture.

  The `DELETE_FILTER` procedure in this example uses the `fname` required parameter, which specifies the name of the filter to be removed. The `DELETE_FILTER` procedure will not remove filters that belong to completed captures; it only applies to filters of captures that have yet to start.

#### Starting a Workload Capture

This section describes how to start a workload capture.

Before starting a workload capture, you must first complete the prerequisites for capturing a database workload. The prerequisites are described in "Prerequisites for Capturing a Database Workload". You should also review the workload capture options, as described in "Workload Capture Options".

It is important to have a well-defined starting point for the workload so that the replay system can be restored to that point before initiating a replay of the captured workload. To have a well-defined starting point for the workload capture, it is preferable not to have any active user sessions when starting a workload capture. If active sessions perform ongoing transactions, those transactions will not be replayed properly in subsequent database replays, since only that part of the transaction whose calls were executed after the workload capture is started will be replayed. To avoid this problem, consider restarting the database in restricted mode using `STARTUP RESTRICT` before starting the workload capture. Once the workload capture begins, the database will automatically switch to unrestricted mode and normal operations can continue while the workload is being captured. For more information about restarting the database before capturing a workload, see "Restarting the Database".

##### To start a workload capture:

- Use the `START_CAPTURE` procedure:

      BEGIN
        DBMS_WORKLOAD_CAPTURE.START_CAPTURE (name => 'dec10_peak',
                                 dir => 'dec10',
                                 duration => 600,
                                 capture_sts => TRUE,
                                 sts_cap_interval => 300,
                                 plsql_mode => 'extended',
                                 encryption => 'AES256');
      END;
      /

  In this example, a workload named `dec10_peak` will be captured for 600 seconds and stored in the file system directory pointed to by the database directory object named `dec10`. A SQL tuning set will also be captured in parallel with the workload capture.

  The `START_CAPTURE` procedure in this example uses the following parameters:

  - The `name` required parameter specifies the name of the workload that will be captured.

  - The `dir` required parameter specifies a directory object pointing to the directory where the captured workload will be stored.

  - The `duration` parameter specifies the number of seconds before the workload capture will end. If a value is not specified, the workload capture will continue until the `FINISH_CAPTURE` procedure is called.

  - The `capture_sts` parameter specifies whether to capture a SQL tuning set in parallel with the workload capture. If this parameter is set to `TRUE`, you can capture a SQL tuning set during workload capture, then capture another SQL tuning set during workload replay, and use SQL Performance Analyzer to compare the SQL tuning sets without having to re-execute the SQL statements. This enables you to obtain a SQL Performance Analyzer report and compare the SQL performance—before and after the change—while running Database Replay. You can also export the resulting SQL tuning set with its AWR data using the `EXPORT_AWR` procedure, as described in "Exporting AWR Data for Workload Capture".

    This feature is not supported for Oracle RAC. Workload capture filters that are defined using `DBMS_WORKLOAD_CAPTURE` do not apply to the SQL tuning set capture. The default value for this parameter is `FALSE`.

  - The `sts_cap_interval` parameter specifies the duration of the SQL tuning set capture from the cursor cache in seconds. The default value is 300. Setting the value of this parameter below the default value may cause additional overhead with some workloads and is not recommended.

  - The optional `plsql_mode` parameter determines how PL/SQL is handled by DB Replay during capture and replays.

    These two values can be set for the `plsql_mode` parameter:

    - `top_level`: Only top-level PL/SQL calls are captured and replayed, which is how DB Replay handled PL/SQL prior to Oracle Database 12c Release 2 (12.2.0.1). This is the default value.

    - `extended`: Both top-level PL/SQL calls and SQL called from PL/SQL are captured. When the workload is replayed, the replay can be done at either top-level or extended level.

  <!-- -->

  - The `encryption` parameter specifies the algorithm used for encrypting capture files.

    The following encryption standards can be used for the `encryption` parameter:

    - NULL - Capture files are not encrypted (the default value)

    - `AES128` - Capture files are encrypted using AES128

    - `AES192` - Capture files are encrypted using AES192

    - `AES256` - Capture files are encrypted using AES256

    **Note:**

    To run `START_CAPTURE` with encryption, you must set the password using the `oracle.rat.database_replay.encryption` (case-sensitive) identifier. The password is stored in a software keystore. For more information about creating a software keystore, see [Oracle Database Advanced Security Guide](../asoag/configuring-transparent-data-encryption.md).

##### Example: Setting up a password-based software keystore:

The following statement creates a password-based software keystore:

    ADMINISTER KEY MANAGEMENT CREATE KEYSTORE 'MYKEYSTORE' IDENTIFIED BY password;

The following statements open the password-based software keystore and create a backup of the password-based software keystore:

    ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY password;

    ADMINISTER KEY MANAGEMENT SET KEY IDENTIFIED BY password WITH BACKUP;

The following statement adds secret `secret_key,` with the tag `DBREPLAY,` for client `'oracle.rat.database_replay.encryption'` to the password-based software keystore. It also creates a backup of the password-based software keystore before adding the secret:

    ADMINISTER KEY MANAGEMENT ADD SECRET secret_key FOR CLIENT 'oracle.rat.database_replay.encryption' USING TAG 'DBREPLAY'
    IDENTIFIED BY password WITH BACKUP;

The following statement closes the password-based software keystore:

    ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE IDENTIFIED BY password;

**Note:**

The software keystore must be kept open before running database capture and database replay.

#### Stopping a Workload Capture

This section describes how to stop a workload capture.

##### To stop a workload capture:

- Use the `FINISH_CAPTURE` procedure:

      BEGIN
        DBMS_WORKLOAD_CAPTURE.FINISH_CAPTURE ();
      END;
      /

  In this example, the `FINISH_CAPTURE` procedure finalizes the workload capture and returns the database to a normal state.

**Tip:**

After capturing a workload on the production system, you need to preprocess the captured workload, as described in [Preprocessing a Database Workload](preprocessing-a-database-workload.md).

#### Exporting AWR Data for Workload Capture

Exporting AWR data enables detailed analysis of the workload. This data is also required if you plan to run the Replay Compare Period report or the AWR Compare Period report on a pair of workload captures or replays.

##### To export AWR data:

- Use the `EXPORT_AWR` procedure:

      BEGIN
        DBMS_WORKLOAD_CAPTURE.EXPORT_AWR (capture_id => 2);
      END;
      /

  In this example, the AWR snapshots that correspond to the workload capture with a capture ID of 2 are exported, along with any SQL tuning set that may have been captured during workload capture.

  The `EXPORT_AWR` procedure uses the `capture_id` required parameter, which specifies the ID of the capture whose AWR snapshots will be exported. The value of the `capture_id` parameter is displayed in the `ID` column of the `DBA_WORKLOAD_CAPTURES` view.

  **Note:**

  This procedure works only if the corresponding workload capture was performed in the current database and the AWR snapshots that correspond to the original capture time period are still available.

**See Also:**

[Oracle Database Reference](../refrn/DBA_WORKLOAD_CAPTURES.md) for information about the `DBA_WORKLOAD_CAPTURES` view

#### Importing AWR Data for Workload Capture

After AWR data is exported from the capture system, you can import the AWR data into another system, such as a test system where the captured workload will be replayed. Importing AWR data enables detailed analysis of the workload. This data is also required if you plan to run the Replay Compare Period report or the AWR Compare Period report on a pair of workload captures or replays.

##### To import AWR data:

- Use the `IMPORT_AWR` function, as shown in the following example:

      CREATE USER capture_awr
      SELECT DBMS_WORKLOAD_CAPTURE.IMPORT_AWR (capture_id => 2,
                                               staging_schema => 'capture_awr')
        FROM DUAL;

  In this example, the AWR snapshots that correspond to the workload capture with a capture ID of 2 are imported using a staging schema named `capture_awr`.

  The `IMPORT_AWR` procedure in this example uses the following parameters:

  - The `capture_id` required parameter specifies the ID of the capture whose AWR snapshots will be imported. The value of the `capture_id` parameter is displayed in the `ID` column of the `DBA_WORKLOAD_CAPTURES` view.

  - The `staging_schema` required parameter specifies the name of an existing schema in the current database which will be used as a staging area while importing the AWR snapshots from the capture directory to the `SYS` `AWR` schema.

**Note:**

This function fails if the schema specified by the `staging_schema` parameter contains any tables with the same name as any of the AWR tables.

**See Also:**

[Oracle Database Reference](../refrn/DBA_WORKLOAD_CAPTURES.md) for information about the `DBA_WORKLOAD_CAPTURES` view

### Encrypting and Decrypting an Existing Workload Capture Using APIs

This section describes how to encrypt and decrypt an existing workload capture using APIs.

During a workload capture, a variety of information such as connection strings, SQL text, and bind values are saved. This information can be encrypted if it contains sensitive data. You can enable encryption during workload capture as described in Starting a Workload Capture.

#### Encrypting an Existing Workload Capture

This section describes how to encrypt an existing workload capture.

##### To encrypt an existing workload capture:

- Use the `ENCRYPT_CAPTURE` procedure:

      BEGIN
        DBMS_WORKLOAD_CAPTURE.ENCRYPT_CAPTURE(src_dir => 'dec10',
                                              dst_dir => 'dec10_enc',
                                              encryption => 'AES128');
      END;
      /

  The `ENCRYPT_CAPTURE` procedure in this example uses the following parameters:

  - The `src_dir` parameter points to the directory that contains the workload capture to be encrypted.

  - The `dst_dir` parameter points to the directory where the encrypted capture is saved after encryption.

  - The `encryption` parameter specifies the algorithm used for encrypting the workload capture.

**Note:**

Before running `DBMS_WORKLOAD_CAPTURE.ENCRYPT_CAPTURE`, you must store the `oracle.rat.database_replay.encryption` (case-sensitive) identifier in a software keystore.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_CAPTURE.md)

#### Decrypting an Encrypted Workload Capture

This section describes how to decrypt an encrypted workload capture.

An encrypted workload capture can be decrypted by using the `DBMS_WORKLOAD_CAPTURE.DECRYPT_CAPTURE` procedure.

##### To decrypt an encrypted workload capture:

- Use the `DECRYPT_CAPTURE` procedure:

      BEGIN
        DBMS_WORKLOAD_CAPTURE.DECRYPT_CAPTURE(src_dir => 'dec10_enc',
                                              dst_dir => 'dec10');
      END;
      /

  The `DECRYPT_CAPTURE` procedure in this example uses the following parameters:

  - The `src_dir` parameter points to the directory that contains the encrypted capture.

  - The `dst_dir` parameter points to the directory where the decrypted capture is saved after decryption.

**Note:**

Before running `DBMS_WORKLOAD_CAPTURE.DECRYPT_CAPTURE`, you must store the `oracle.rat.database_replay.encryption` (case-sensitive) identifier in a software keystore.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_CAPTURE.md)

### Monitoring Workload Capture Using Views

This section summarizes the views that you can display to monitor workload capture. You can also use Oracle Enterprise Manager to monitor workload capture, as described in "Monitoring a Workload Capture Using Enterprise Manager".

To access these views, you need DBA privileges:

- The `DBA_WORKLOAD_CAPTURES` view lists all the workload captures that have been captured in the current database.

- The `DBA_WORKLOAD_FILTERS` view lists all workload filters used for workload captures defined in the current database.

**See Also:**

- [Oracle Database Reference](../refrn/DBA_WORKLOAD_CAPTURES.md) for information about the `DBA_WORKLOAD_CAPTURES` view

- [Oracle Database Reference](../refrn/DBA_WORKLOAD_FILTERS.md) for information about the `DBA_WORKLOAD_FILTERS` view
