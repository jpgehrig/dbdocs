This chapter describes using various workload scale-up techniques with Consolidated Database Replay. It contains the following sections:

- Overview of Workload Scale-Up

- Using Time Shifting

- Using Workload Folding

- Using Schema Remapping

### Overview of Workload Scale-Up

Consolidated Database Replay enables you to replay multiple workloads captured from one or multiple systems concurrently. During the replay, every workload capture that is consolidated will start to replay when the consolidated replay begins. Depending on the use case, you can employ various workload scale-up techniques when using Consolidated Database Replay.

This section describes the following workload scale-up techniques:

- About Time Shifting

- About Workload Folding

- About Schema Remapping

**See Also:**

"[Use Cases for Consolidated Database Replay](using-consolidated-database-replay.md)" for information about typical use cases for Consolidated Database Replay

#### About Time Shifting

Database Replay enables you to perform time shifting when replaying captured workloads. This technique is useful in cases where you want to conduct stress testing on a system by adding workloads to an existing workload capture and replaying them together.

For example, assume that there are three workloads captured from three applications: Sales, CRM, and DW. In order to perform stress testing, you can align the peaks of these workload captures and replay them together using Consolidated Database Replay.

**See Also:**

- "Using Time Shifting" for information about using time shifting

- "[Stress Testing](using-consolidated-database-replay.md)" for information about using Consolidated Database Replay for stress testing

#### About Workload Folding

Database Replay enables you to perform scale-up testing by folding an existing workload capture. For example, assume that a workload was captured from 2 a.m. to 8 p.m. You can use Database Replay to fold the original workload into three capture subsets: one from 2 a.m. to 8 a.m., a second from 8 a.m. to 2 p.m., and a third from 2 p.m. to 8 p.m. By replaying the three capture subsets together, you can fold the original capture and triple the workload during replay to perform scale-up testing.

**See Also:**

- "Using Workload Folding" for information about using workload folding

- "[Capture Subsets](using-consolidated-database-replay.md)" for information about capture subsets

- "[Scale-Up Testing](using-consolidated-database-replay.md)" for information about using Consolidated Database Replay for scale-up testing

#### About Schema Remapping

Database Replay enables you to perform scale-up testing by remapping database schemas. This technique is useful in cases when you are deploying multiple instances of the same application—such as a multi-tenet application—or adding a new geographical area to an existing application.

For example, assume that a single workload exists for a Sales application. To perform scale-up testing and identify possible host bottlenecks, set up the test system with multiple schemas from the Sales schema.

**See Also:**

- "Using Schema Remapping" for information about using schema remapping

- "[Scale-Up Testing](using-consolidated-database-replay.md)" for information about using Consolidated Database Replay for scale-up testing

### Using Time Shifting

This section describes how to use time shifting with Consolidated Database Replay, and assumes a scenario where you want to use time shifting to align the peaks of workloads captured from three applications and replay them simultaneously. The scenario demonstrates how to use time shifting for stress testing. For more information about time shifting, see "About Time Shifting".

This scenario uses the following assumptions:

- The first workload is captured from the Sales application.

- The second workload is captured from the CRM application and its peak time occurs 1 hour before that of the Sales workload.

- The third workload is captured from the DW application and its peak time occurs 30 minutes before that of the Sales workload.

- To align the peaks of these workloads, time shifting is performed by adding a delay of one hour to the CRM workload and a delay of 30 minutes to the DW workload during replay.

#### To perform time shifting in this scenario:

1.  On the replay system which will undergo stress testing, create a directory object for the root directory where the captured workloads are stored:

        CREATE [OR REPLACE] DIRECTORY cons_dir AS '/u01/test/cons_dir';

2.  Preprocess the individual workload captures into separate directories:

    - For the Sales workload:

      1.  Create a directory object:

              CREATE OR REPLACE DIRECTORY sales AS '/u01/test/cons_dir/cap_sales';

      2.  Ensure that the captured workload from the Sales application is stored in this directory.

      3.  Preprocess the workload:

              EXEC DBMS_WORKLOAD_REPLAY.PROCESS_CAPTURE ('SALES');

    - For the CRM workload:

      1.  Create a directory object:

              CREATE OR REPLACE DIRECTORY crm AS '/u01/test/cons_dir/cap_crm';

      2.  Ensure that the captured workload from the CRM application is stored in this directory.

      3.  Preprocess the workload:

              EXEC DBMS_WORKLOAD_REPLAY.PROCESS_CAPTURE ('CRM');

    - For the DW workload:

      1.  Create a directory object:

              CREATE OR REPLACE DIRECTORY DW AS '/u01/test/cons_dir/cap_dw';

      2.  Ensure that the captured workload from the DW application is stored in this directory.

      3.  Preprocess the workload:

              EXEC DBMS_WORKLOAD_REPLAY.PROCESS_CAPTURE ('DW');

3.  Set the replay directory to the root directory:

        EXEC DBMS_WORKLOAD_REPLAY.SET_REPLAY_DIRECTORY ('CONS_DIR');

4.  Create a replay schedule and add the workload captures:

        EXEC DBMS_WORKLOAD_REPLAY.BEGIN_REPLAY_SCHEDULE ('align_peaks_schedule');
        SELECT DBMS_WORKLOAD_REPLAY.ADD_CAPTURE ('SALES') FROM dual;
        SELECT DBMS_WORKLOAD_REPLAY.ADD_CAPTURE ('CRM', 3600) FROM dual;
        SELECT DBMS_WORKLOAD_REPLAY.ADD_CAPTURE ('DW', 1800) FROM dual;
        EXEC DBMS_WORKLOAD_REPLAY.END_REPLAY_SCHEDULE;

    Note that a delay of 3,600 seconds (or 1 hour) is added to the CRM workload, and a delay of 1,800 seconds (or 30 minutes) is added to the DW workload.

5.  Initialize the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.INITIALIZE_CONSOLIDATED_REPLAY ('align_peaks_replay',
                                  'align_peaks_schedule');

6.  Remap connections:

    1.  Query the `DBA_WORKLOAD_CONNECTION_MAP` view for the connection mapping information:

            SELECT schedule_cap_id, conn_id, capture_conn, replay_conn
              FROM dba_workload_connection_map;

    2.  Remap the connections:

            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 1,
                 conn_id => 1, replay_connection => 'inst1');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 1,
                 conn_id => 2, replay_connection => 'inst1');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 2,
                 conn_id => 1, replay_connection => 'inst2');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 2,
                 conn_id => 2, replay_connection => 'inst2');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 3,
                 conn_id => 1, replay_connection => 'inst3');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 3,
                 conn_id => 2, replay_connection => 'inst3');

        The `replay_connection` parameter represents the services that are defined on the test system.

    3.  Verify the connection remappings:

            SELECT schedule_cap_id, conn_id, capture_conn, replay_conn
              FROM dba_workload_connection_map;

7.  Prepare the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.PREPARE_CONSOLIDATED_REPLAY;

8.  Start replay clients:

    1.  Estimate the number of replay clients that are required:

            wrc mode=calibrate replaydir=/u01/test/cons_dir/cap_sales
            wrc mode=calibrate replaydir=/u01/test/cons_dir/cap_crm
            wrc mode=calibrate replaydir=/u01/test/cons_dir/cap_dw

    2.  Add the output to determine the number of replay clients required.

        You will need to start at least one replay client per workload capture contained in the consolidated workload.

    3.  Start the required number of replay clients by repeating this command:

            wrc username/password mode=replay replaydir=/u01/test/cons_dir

        The `replaydir` parameter is set to the root directory in which the workload captures are stored.

9.  Start the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.START_CONSOLIDATED_REPLAY;

### Using Workload Folding

This section describes how to use workload folding with Consolidated Database Replay, and assumes a scenario where you want to use workload folding to triple a captured workload. The scenario demonstrates how to use workload folding for scale-up testing. For more information about workload folding, see "About Workload Folding".

This scenario uses the following assumptions:

- The original workload was captured from 2 a.m. to 8 p.m. and folded into three capture subsets.

- The first capture subset contains part of the original workload from 2 a.m. to 8 a.m.

- The second capture subset contains part of the original workload from 8 a.m. to 2 p.m.

- The third capture subset contains part of the original workload from 2 p.m. to 8 p.m.

- To triple the workload during replay, workload folding is performed by replaying the three capture subsets simultaneously.

#### To perform workload folding in this scenario:

1.  On the replay system where you plan to perform scale-up testing, create a directory object for the root directory where the captured workloads are stored:

        CREATE OR REPLACE DIRECTORY cons_dir AS '/u01/test/cons_dir';

2.  Create a directory object for the directory where the original workload is stored:

        CREATE OR REPLACE DIRECTORY cap_monday AS '/u01/test/cons_dir/cap_monday';

3.  Create directory objects for the directories where you are planning to store the capture subsets:

    1.  Create a directory object for the first capture subset:

            CREATE OR REPLACE DIRECTORY cap_mon_2am_8am
                                       AS '/u01/test/cons_dir/cap_monday_2am_8am';

    2.  Create a directory object for the second capture subset:

            CREATE OR REPLACE DIRECTORY cap_mon_8am_2pm
                                       AS '/u01/test/cons_dir/cap_monday_8am_2pm';

    3.  Create a directory object for the third capture subset:

            CREATE OR REPLACE DIRECTORY cap_mon_2pm_8pm
                                       AS '/u01/test/cons_dir/cap_monday_2pm_8pm';

4.  Create the capture subsets:

    1.  Generate the first capture subset for the time period from 2 a.m. to 8 a.m.:

            EXEC DBMS_WORKLOAD_REPLAY.GENERATE_CAPTURE_SUBSET ('CAP_MONDAY',
                                      'CAP_MON_2AM_8AM', 'mon_2am_8am_wkld',
                                      0, TRUE, 21600, FALSE, 1);

    2.  Generate the second capture subset for the time period from 8 a.m. to 2 p.m.:

            EXEC DBMS_WORKLOAD_REPLAY.GENERATE_CAPTURE_SUBSET ('CAP_MONDAY',
                                      'CAP_MON_8AM_2PM', 'mon_8am_2pm_wkld',
                                      21600, TRUE, 43200, FALSE, 1);

    3.  Generate the third capture subset for the time period from 2 p.m. to 8 p.m.:

            EXEC DBMS_WORKLOAD_REPLAY.GENERATE_CAPTURE_SUBSET ('CAP_MONDAY',
                                      'CAP_MON_2PM_8PM', 'mon_2pm_8pm_wkld',
                                      43200, TRUE, 0, FALSE, 1);

5.  Preprocess the capture subsets:

        EXEC DBMS_WORKLOAD_REPLAY.PROCESS_CAPTURE ('CAP_MON_2AM_8AM');
        EXEC DBMS_WORKLOAD_REPLAY.PROCESS_CAPTURE ('CAP_MON_8AM_2PM');
        EXEC DBMS_WORKLOAD_REPLAY.PROCESS_CAPTURE ('CAP_MON_2PM_8PM');

6.  Set the replay directory to the root directory:

        EXEC DBMS_WORKLOAD_REPLAY.SET_REPLAY_DIRECTORY ('CONS_DIR');

7.  Create a replay schedule and add the capture subsets:

        EXEC DBMS_WORKLOAD_REPLAY.BEGIN_REPLAY_SCHEDULE ('monday_folded_schedule');
        SELECT DBMS_WORKLOAD_REPLAY.ADD_CAPTURE ('CAP_MON_2AM_8AM') FROM dual;
        SELECT DBMS_WORKLOAD_REPLAY.ADD_CAPTURE ('CAP_MON_8AM_2PM') FROM dual;
        SELECT DBMS_WORKLOAD_REPLAY.ADD_CAPTURE ('CAP_MON_2PM_8PM') FROM dual;
        EXEC DBMS_WORKLOAD_REPLAY.END_REPLAY_SCHEDULE;

8.  Initialize the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.INITIALIZE_CONSOLIDATED_REPLAY (
                                  'monday_folded_replay', 'monday_folded_schedule');

9.  Remap connections:

    1.  Query the `DBA_WORKLOAD_CONNECTION_MAP` view for the connection mapping information:

            SELECT schedule_cap_id, conn_id, capture_conn, replay_conn
              FROM dba_workload_connection_map;

    2.  Remap the connections:

            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 1,
                 conn_id => 1, replay_connection => 'inst1');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 1,
                 conn_id => 2, replay_connection => 'inst1');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 2,
                 conn_id => 1, replay_connection => 'inst2');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 2,
                 conn_id => 2, replay_connection => 'inst2');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 3,
                 conn_id => 1, replay_connection => 'inst3');
            EXEC DBMS_WORKLOAD_REPLAY.REMAP_CONNECTION (schedule_cap_id => 3,
                 conn_id => 2, replay_connection => 'inst3');

        The `replay_connection` parameter represents the services that are defined on the test system.

    3.  Verify the connection remappings:

            SELECT schedule_cap_id, conn_id, capture_conn, replay_conn
              FROM dba_workload_connection_map;

10. Prepare the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.PREPARE_CONSOLIDATED_REPLAY;

11. Start replay clients:

    1.  Estimate the number of replay clients that are required:

            wrc mode=calibrate replaydir=/u01/test/cons_dir/cap_monday_2am_8am
            wrc mode=calibrate replaydir=/u01/test/cons_dir/cap_monday_8am_2pm
            wrc mode=calibrate replaydir=/u01/test/cons_dir/cap_monday_2pm_8pm

    2.  Add the output to determine the number of replay clients required.

        You will need to start at least one replay client per workload capture contained in the consolidated workload.

    3.  Start the required number of replay clients by repeating this command:

            wrc username/password mode=replay replaydir=/u01/test/cons_dir

        The `replaydir` parameter is set to the root directory in which the workload captures are stored.

12. Start the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.START_CONSOLIDATED_REPLAY;

### Using Schema Remapping

This section describes how to use schema remapping with Consolidated Database Replay, and assumes a scenario where you want to use schema remapping to identify possible host bottlenecks when deploying multiple instances of an application. The scenario demonstrates how to use schema remapping for scale-up testing. For more information about schema remapping, see "About Schema Remapping".

This scenario uses the following assumptions:

- A single workload exists that is captured from the Sales application.

- To set up the replay system with multiple schemas from the Sales schema, schema remapping is performed by adding the captured workload multiple times into a replay schedule and remapping the users to different schemas.

#### To perform schema remapping in this scenario:

1.  On the replay system where you plan to perform scale-up testing, create a directory object for the root directory where the captured workloads are stored:

        CREATE OR REPLACE DIRECTORY cons_dir AS '/u01/test/cons_dir';

2.  Create a directory object for the directory where the captured workload is stored:

        CREATE OR REPLACE DIRECTORY cap_sales AS '/u01/test/cons_dir/cap_sales';

    Ensure that the captured workload from the Sales application is stored in this directory.

3.  Preprocess the captured workload:

        EXEC DBMS_WORKLOAD_REPLAY.PROCESS_CAPTURE ('CAP_SALES');

4.  Set the replay directory to the root directory:

        EXEC DBMS_WORKLOAD_REPLAY.SET_REPLAY_DIRECTORY ('CONS_DIR');

5.  Create a replay schedule and add the captured workload multiple times:

        EXEC DBMS_WORKLOAD_REPLAY.BEGIN_REPLAY_SCHEDULE ('double_sales_schedule');
        SELECT DBMS_WORKLOAD_REPLAY.ADD_CAPTURE ('CAP_SALES') FROM dual;
        SELECT DBMS_WORKLOAD_REPLAY.ADD_CAPTURE ('CAP_SALES') FROM dual;
        EXEC DBMS_WORKLOAD_REPLAY.END_REPLAY_SCHEDULE;

6.  Initialize the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.INITIALIZE_CONSOLIDATED_REPLAY (
                                  'double_sales_replay', 'double_sales_schedule);

7.  Remap the users:

        EXEC DBMS_WORKLOAD_REPLAY.SET_USER_MAPPING (2, 'sales_usr', 'sales_usr_2');

8.  Prepare the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.PREPARE_CONSOLIDATED_REPLAY;

9.  Start replay clients:

    1.  Estimate the number of replay clients that are required:

            wrc mode=calibrate replaydir=/u01/test/cons_dir/cap_sales

    2.  Add the output to determine the number of replay clients required.

        You will need to start at least one replay client per workload capture contained in the consolidated workload.

    3.  Start the required number of replay clients by repeating this command:

            wrc username/password mode=replay replaydir=/u01/test/cons_dir

        The `replaydir` parameter is set to the root directory in which the workload captures are stored.

10. Start the consolidated replay:

        EXEC DBMS_WORKLOAD_REPLAY.START_CONSOLIDATED_REPLAY;
