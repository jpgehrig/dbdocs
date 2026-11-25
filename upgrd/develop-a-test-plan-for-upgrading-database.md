## Develop a Test Plan for Upgrading Oracle Database

Review these topics to understand how to create a series of carefully designed tests to validate all stages of the upgrade process.

Oracle recommends that you perform rigorous tests of your database and applications. When you run and complete tests successfully, you help to ensure that you understand the process of upgrading the production database, so that the upgrade process is predictable and successful. Oracle strongly recommends that you perform as much testing as possible before upgrading a production database. Do not underestimate the importance of a complete and repeatable testing process.

You can choose to perform tests manually, or you can use utilities to assist your tests, such as Oracle Real Application Testing features like Database Replay or SQL Performance Analyzer. In either case, the types of tests that you perform are the same.

Your test plan must include these types of tests:

- Upgrade Testing
  When you upgrade Oracle Database to a new release, Oracle strongly recommends that you create, test, and validate an upgrade plan.
- Minimal Testing
  You can find application startup or invocation problems when you perform minimal testing of applications on a test new release environment.
- Functional Testing After Upgrades
  Perform functional testing of the upgraded Oracle Database after the upgrade is complete.
- High Availability Testing
  To ensure that you can continue to meet your service level agreements, plan to perform High Availability testing on your upgraded Oracle Database system.
- Integration Testing to Ensure Applications are Compatible
  Integration testing for Oracle Database examines the interactions among components of the system.
- Performance Testing an Upgraded Oracle Database
  Plan performance testing comparisons between your earlier release and upgraded Oracle Database.
- Volume and Load Stress Testing for Oracle Database Upgrades
  To perform volume and load stress testing of the entire upgraded Oracle Database under high volume and loads, use Database Replay.
- Test Plan Guidelines for Oracle Database Upgrade Planning
  Perform planned tests on your current database and on the test database that you upgraded to the new Oracle Database release.

**Parent topic:** [Tasks to Prepare for Oracle Database Upgrades](tasks-to-prepare-for-oracle-database-upgrades.md)

### Upgrade Testing

When you upgrade Oracle Database to a new release, Oracle strongly recommends that you create, test, and validate an upgrade plan.

Upgrade testing for Oracle Database entails planning and testing the upgrade path from your current Oracle Database software to the new Oracle Database release. Oracle strongly recommends that you plan and test your upgrade, whether you use Oracle Database Upgrade Assistant (DBUA), perform a manual upgrade, or use the AutoUpgrade utility. Planning and testing also applies if you use data migration methods, such as Oracle Data Pump Export/Import, or other data-copying methods. Regardless of the upgrade or data migration method you choose, you must plan, test, and validate changes.

**Parent topic:** Develop a Test Plan for Upgrading Oracle Database

### Minimal Testing

You can find application startup or invocation problems when you perform minimal testing of applications on a test new release environment.

Minimal testing for Oracle Database entails moving all or part of an application from the current database to the new database, and running the application without enabling any new database features. It is possible that minimal testing does not reveal problems that appear in an actual production environment. However, minimal testing immediately reveals any application startup or invocation problems.

**Parent topic:** Develop a Test Plan for Upgrading Oracle Database

### Functional Testing After Upgrades

Perform functional testing of the upgraded Oracle Database after the upgrade is complete.

Functional testing for Oracle Database is a set of tests in which new and existing features and functions of the system are tested after the upgrade. Functional testing includes all database, networking, and application components. The objective of functional testing is to verify that each component of the system functions as it did before upgrading and to verify that new functions are working properly.

**Parent topic:** Develop a Test Plan for Upgrading Oracle Database

### High Availability Testing

To ensure that you can continue to meet your service level agreements, plan to perform High Availability testing on your upgraded Oracle Database system.

High Availability testing for Oracle Database ensures that the upgraded database system meets these recovery business requirements:

- Recovery Time Objective (RTO)
- Recovery Point Objective (RPO)

Oracle recommends the following test procedures for high availability testing:

- Create node or instance failures during stress testing. Node or instance failures help to evaluate the Oracle RAC recovery capability.
- Test fallback plans and procedures to ensure that you can minimize downtime on upgraded databases.
- Check database performance and stability, and resolve performance problems. Resolving performance problems helps to ensure that the upgrade process runs within the time that you have allocated.

**Parent topic:** Develop a Test Plan for Upgrading Oracle Database

### Integration Testing to Ensure Applications are Compatible

Integration testing for Oracle Database examines the interactions among components of the system.

Oracle recommends that you carry out the following tests as part of your integration testing:

- To ensure that Pro\*C/C++ applications are compatible with the upgraded database, test Pro\*C/C++ application clients with the upgraded Oracle Database

- Test graphical user interfaces.

- Test all applications that interact directly or indirectly with the database. Subtle changes in an upgraded Oracle Database, such as data types, data in the data dictionary (additional rows in the data dictionary, object type changes, and so on) can affect front-end applications, even if those applications are not directly connected to the upgraded Oracle Database instance.

- Test and stress-test any Oracle Net or Oracle Net Services connections between components.

**Related Topics**

- [C++ Applications](../lnpcc/C-Plus-Plus-Applications.md)
- [Upgrade Considerations for Oracle Net Services](../netrf/upgrade-considerations-for-oracle-net-services.md)

**Parent topic:** Develop a Test Plan for Upgrading Oracle Database

### Performance Testing an Upgraded Oracle Database

Plan performance testing comparisons between your earlier release and upgraded Oracle Database.

Performance testing of the upgraded Oracle Database compares the performance of various SQL statements in the new database with the performance of those same statements in the current database. Before upgrading, analyze the performance profile of applications under your current Oracle Database release. Specifically, analyze and understand the calls that applications make to the database server.

Oracle strongly recommends that you set up a testing system with the same storage, data, and other characteristics as your production system.

- Database Replay and Performance Testing
  Use the Database Replay feature to perform real-world testing of a database upgrade on your production workload before actually upgrading the production database.
- SQL Performance Analyzer
  Use the SQL Performance Analyzer to forecast the impact of system changes on a SQL workload.
- SQL Plan Management
  Review this topic to understand how to carry out SQL plan managements after upgrades to avoid performance regressions.

**Parent topic:** Develop a Test Plan for Upgrading Oracle Database

#### Database Replay and Performance Testing

Use the Database Replay feature to perform real-world testing of a database upgrade on your production workload before actually upgrading the production database.

The Database Replay feature captures the actual database workload on the production system, and replays it on the test system. Database Replay also provides analysis and reporting to highlight potential problems; for example, errors encountered, divergence in performance, and so forth. In addition, all the regular Enterprise Manager performance monitoring and reporting tools such as Automatic Database Diagnostic Monitor, Automatic Workload Repository (AWR), and Active Session History are available to address any problems.

**Note:**

You can change the stored procedure logic in the database. However, the stored PL/SQL procedures that implement the application logic must maintain the same interfaces as before the upgrade. If an upgrade affects the stored procedures of an application, replaying the workload may not be possible. Using Database Replay tool with the same interfaces provides you with good diagnostics to see if the new application logic in the server is performing as expected after the upgrade.

**See Also:**

- [Oracle Database Testing Guide](../ratug/introduction-to-database-replay.md) for information about how to capture and replay workloads

- [Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for more information on the Automatic Workload Repository

**Parent topic:** Performance Testing an Upgraded Oracle Database

#### SQL Performance Analyzer

Use the SQL Performance Analyzer to forecast the impact of system changes on a SQL workload.

SQL Performance Analyzer enables you to evaluate the effect of an upgrade on your SQL workloads. SQL Performance Analyzer finds possible issues by identifying the SQL statements affected by the upgrade. It then measures the performance divergence of SQL workloads before the upgrade, and after the upgrade. The analysis enables you to assess the overall effect of the upgrade on SQL performance. You can then take measures to avoid any negative outcome from SQL workload changes before they can affect users.

**See Also:**

[Oracle Database Testing Guide](../ratug/introduction-to-sql-performance-analyzer.md) for further information, and examples of using the SQL Performance Analyzer to perform analysis on potential database changes

**Parent topic:** Performance Testing an Upgraded Oracle Database

#### SQL Plan Management

Review this topic to understand how to carry out SQL plan managements after upgrades to avoid performance regressions.

A database upgrade that installs a new optimizer version usually results in plan changes for a small percentage of SQL statements. Most plan changes result in no performance change or improvement. However, certain plan changes may cause performance regressions. SQL plan management prevents performance regressions resulting from sudden changes to the execution plan of a SQL statement by providing components for capturing, selecting, and evolving SQL plan information. SQL plan management is a preventative mechanism that records and evaluates the execution plans of SQL statements over time, and builds SQL plan baselines composed of a set of existing plans that are proven efficient after repeated use. SQL plan management uses the SQL plan baselines to preserve the performance of corresponding SQL statements, regardless of changes occurring in the system.

With SQL plan management, the optimizer automatically manages execution plans and ensures that only known or verified plans are used. When SQL Plan management finds a new plan for a SQL statement, it does not use this plan until the database verifies that the new plan has comparable or better performance than the current plan. If you seed SQL plan management with your current execution plans, then those plans becomes the SQL plan baseline for each statement. The optimizer uses these plans after the upgrade. If the Oracle Database 12c optimizer determines that a different plan can result in better performance, then the new plan is queued for verification and is not used until it has been confirmed to have comparable or better performance than the current plan.

There are several ways to seed or populate a SQL Management Base (SMB) with execution plans:

##### Bulk Load a SQL Management Base from the Cursor Cache

Bulk loading of execution plans or SQL plan baselines from the cursor cache is useful when upgrading a database from Oracle Database 11g to the latest release of Oracle Database. The cursor cache is a shared SQL area, and SQL plans that are bulk loaded are automatically accepted and added to existing or new plan histories as SQL plan baselines.

1.  In the source release of Oracle Database, use the `DBMS_SPM.LOAD_PLAN_FROM_CURSOR_CACHE` procedure or Oracle Enterprise Manager to load all of the execution plans in the cursor cache into the SQL Management Base.

2.  Upgrade the database.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/managing-sql-plan-baselines.md) for more information on how to load plans from the shared SQL area using PL/SQL or Oracle Enterprise Manager

##### Bulk Load a SQL Management Base with a SQL Tuning Set (STS)

Bulk loading of execution plans or SQL plan baselines may be done with a SQL Tuning Set. This is useful when upgrading from Oracle Database 10g, where no SQL Management Base (SMB) exists to directly load from the cursor cache, or to load historic plans from the Automatic Workload Repository.

1.  In the source release of Oracle Database, create an STS that includes the execution plan for each of the SQL statements.

2.  Load the STS into a staging table and export the staging table into a dump file.

3.  Import the staging table from a dump file into the new release of Oracle and unload the STS.

4.  Use Oracle Enterprise Manager or `DBMS_SPM.LOAD_PLANS_FROM_SQLSET` to load the execution plans into the SQL Management Base.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/managing-sql-plan-baselines.md) for the complete procedure for bulk loading execution plans or SQL plan baselines

##### Unpack Existing SQL Plan Baselines from a Staging Table

You can test and tune all of your critical SQL queries on an Oracle Database test environment and then move those SQL execution plans to your Oracle Database production environment. Alternatively, you can take plans for SQL queries from your pre-upgrade Oracle Database production environment and move them to your post-upgrade production environment.

1.  On the Oracle Database 12c test system, after completing all testing and tuning, use the `DBMS_SPM.LOAD_PLAN_FROM_CURSOR_CACHE` procedure or Enterprise Manager to load all of the execution plans in the cursor cache into the SQL Management Base.

2.  Create a staging table using the `DBMS_SPM.CREATE_STGTAB_BASELINE` procedure.

3.  Pack the SQL plan baselines you created in step 1 into the staging table using the `DBMS_SPM.PACK_STGTAB_BASELINE` function.

4.  Export the staging table into a flat file using Data Pump.

5.  Transfer this flat file to the target system.

6.  Import the staging table from the flat file using Data Pump.

7.  Unpack the SQL plan baselines from the staging table into the SQL Management Base on the target system using the `DBMS_SPM.UNPACK_STGTAB_BASELINE` function.

- Why Perform SQL Plan Management?
  To prevent users from encountering performance regressions after an Oracle Database upgrade, carry out SQL plan management.
- Bulk Load a SQL Management Base from the Cursor Cache
  Bulk loading of execution plans or SQL plan baselines from the cursor cache is useful when upgrading an earlier release to the latest release of Oracle Database.
- Bulk Load a SQL Management Base with a SQL Tuning Set (STS)
  Bulk loading of execution plans or SQL plan baselines is useful to load historic plans from the Automatic Workload Repository.
- Unpack Existing SQL Plan Baselines from a Staging Table
  Test your critical SQL queries and execution plans by using `DBMS_SPM.LOAD_PLAN_FROM_CURSOR_CACHE` to create a staging table that you can migrate for testing.

**See Also:**

- [Oracle Database SQL Tuning Guide](../tgsql/managing-sql-plan-baselines.md) for more information about loading plans from a staging table

- [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for information about using Data Pump

**Parent topic:** Performance Testing an Upgraded Oracle Database

##### Why Perform SQL Plan Management?

To prevent users from encountering performance regressions after an Oracle Database upgrade, carry out SQL plan management.

An Oracle Database upgrade that installs a new optimizer version usually results in plan changes for a small percentage of SQL statements. Most plan changes result in no performance change or improvement. However, certain plan changes can cause performance regressions. SQL plan management prevents performance regressions resulting from sudden changes to the execution plan of a SQL statement by providing components for capturing, selecting, and evolving SQL plan information. SQL plan management is a preventative mechanism that records and evaluates the execution plans of SQL statements over time, and builds SQL plan baselines composed of a set of existing plans that are proven efficient after repeated use. SQL plan management uses the SQL plan baselines to preserve the performance of corresponding SQL statements, regardless of changes occurring in the system.

With SQL plan management, the optimizer automatically manages execution plans and ensures that only known or verified plans are used. When SQL Plan management finds a new plan for a SQL statement, it does not use this plan until the database verifies that the new plan has comparable or better performance than the current plan. If you seed SQL plan management with your current execution plans, then those plans becomes the SQL plan baseline for each statement. The optimizer uses these plans after the upgrade. If the upgraded Oracle Database optimizer determines that a different plan can result in better performance, then the new plan is queued for verification. The new plan is not used until it has been confirmed to have comparable or better performance than the current plan.

**Parent topic:** SQL Plan Management

##### Bulk Load a SQL Management Base from the Cursor Cache

Bulk loading of execution plans or SQL plan baselines from the cursor cache is useful when upgrading an earlier release to the latest release of Oracle Database.

The cursor cache is a shared SQL area. SQL plans that are bulk-loaded are automatically accepted and added to existing or new plan histories as SQL plan baselines.

1.  In the source release of Oracle Database, use the `DBMS_SPM.LOAD_PLAN_FROM_CURSOR_CACHE` procedure or Oracle Enterprise Manager to load all of the execution plans in the cursor cache into the SQL Management Base.

2.  Upgrade the database.

**Related Topics**

- [Loading Plans from the Shared SQL Area](../tgsql/managing-sql-plan-baselines.md)

**Parent topic:** SQL Plan Management

##### Bulk Load a SQL Management Base with a SQL Tuning Set (STS)

Bulk loading of execution plans or SQL plan baselines is useful to load historic plans from the Automatic Workload Repository.

Bulk loading of execution plans or SQL plan baselines may be done with a SQL Tuning Set. This is useful when you want to load historic plans from your earlier Oracle Database Automatic Workload Repository.

1.  In the source release of Oracle Database, create an STS that includes the execution plan for each of the SQL statements.

2.  Load the STS into a staging table and export the staging table into a dump file.

3.  Import the staging table from a dump file into the new release of Oracle and unload the STS.

4.  Use Oracle Enterprise Manager or `DBMS_SPM.LOAD_PLANS_FROM_SQLSET` to load the execution plans into the SQL Management Base.

**Related Topics**

- [Loading Plans from a SQL Tuning Set](../tgsql/managing-sql-plan-baselines.md)

**Parent topic:** SQL Plan Management

##### Unpack Existing SQL Plan Baselines from a Staging Table

Test your critical SQL queries and execution plans by using `DBMS_SPM.LOAD_PLAN_FROM_CURSOR_CACHE` to create a staging table that you can migrate for testing.

You can test and tune all of your critical SQL queries on an Oracle Database test environment and then move those SQL execution plans to your Oracle Database production environment. Alternatively, you can take plans for SQL queries from your pre-upgrade Oracle Database production environment and move them to your post-upgrade production environment.

1.  On the new Oracle Database release test system, after completing all testing and tuning, use the `DBMS_SPM.LOAD_PLAN_FROM_CURSOR_CACHE` procedure or Enterprise Manager to load all of the execution plans in the cursor cache into the SQL Management Base.

2.  Create a staging table using the `DBMS_SPM.CREATE_STGTAB_BASELINE` procedure.

3.  Pack the SQL plan baselines you created in step 1 into the staging table using the `DBMS_SPM.PACK_STGTAB_BASELINE` function.

4.  Export the staging table into a flat file, using Oracle Data Pump.

5.  Transfer this flat file to the target system.

6.  Import the staging table from the flat file using Oracle Data Pump.

7.  Unpack the SQL plan baselines from the staging table into the SQL Management Base on the target system using the `DBMS_SPM.UNPACK_STGTAB_BASELINE` function.

**Related Topics**

- [Loading Plans from a Staging Table](../tgsql/managing-sql-plan-baselines.md)
- [Overview of Oracle Data Pump](../sutil/oracle-data-pump-overview.md)

**Parent topic:** SQL Plan Management

### Volume and Load Stress Testing for Oracle Database Upgrades

To perform volume and load stress testing of the entire upgraded Oracle Database under high volume and loads, use Database Replay.

Oracle Replay can assist you to uncover load issues before you move an upgraded Oracle Database release to production. **Volume** describes the amount of data being manipulated. **Load** describes the level of concurrent demand on the system. So when you capture and replay a real production system volume and load, you can emulate that load on your upgraded Oracle Database, and observe how it performs under various volumes and loads.

Volume and load stress testing is crucial. However, it is commonly overlooked. After upgrades, Oracle has found that some customers do not conduct any kind of volume or load stress testing. Instead, customers often rely on benchmarks that do not characterize business applications. Benchmarks are valuable: Oracle recommends that you conduct benchmarks of your applications. Benchmarking can help you to uncover problems relating to functions, performance, and integration. However, using benchmarks cannot replace volume and load stress testing.

Load testing involves running an application load against the new Oracle Database release, using an environment with the same data and infrastructure. When you run a load test, you are ensuring that your applications do not encounter problems, such as new errors, or performance issues under the load conditions that you think are likely to occur during production. Many times, problems manifest only under certain load conditions, and are normally not seen in functional testing. The Database Replay feature is ideal for such load testing. Database Replay enables you to capture the system workload from a production environment, and replay it in identical fashion on the test system.

**Related Topics**

- [Introduction to Database Replay](../ratug/introduction-to-database-replay.md)

**Parent topic:** Develop a Test Plan for Upgrading Oracle Database

### Test Plan Guidelines for Oracle Database Upgrade Planning

Perform planned tests on your current database and on the test database that you upgraded to the new Oracle Database release.

- Compare the test results, noting anomalies.

- Repeat the test upgrade as many times as necessary until issues are resolved.

Test the newly upgraded test database with existing applications to verify that they operate properly with a new Oracle database.

- Test enhanced functions and new capabilities by adding available Oracle Database features.

- Ensure that the applications operate in the same manner as they did in the current database.

**See Also:**

[Oracle Database Testing Guide](../ratug/testing-a-database-upgrade.md) for information on testing a database upgrade

**Parent topic:** Develop a Test Plan for Upgrading Oracle Database
