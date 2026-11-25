## 12 Troubleshooting Oracle Sharding

You can enable tracing, locate log and trace files, and troubleshooting common issues.

The following topics describe Oracle Sharding troubleshooting in detail:

### Troubleshooting Tips

Use these tips to discover information about the sharded database that you need to help you troubleshoot issues.

#### Topics:

- Checking the Sharding Method
- Checking the Replication Type
- Checking the Oracle Data Guard Protection Mode
- Checking Which Shards Are Mapped to a Key
- Checking Shard Operation Mode (Read-Only or Read-Write)
- Checking DDL Text
- Checking Chunk Migration Status
- Checking Table Type (Sharded or Duplicated)
- Checking User Type (Local or ALL_SHARD)
- Identifying Tables Created as Sharded Tablespaces
- Checking if Shard DDL is Enabled or Disabled
- Filtering Data by Sharding Key

#### Checking the Sharding Method

Run `gdsctl config sdb` to check which sharding method, also known as the shard type, is used in the sharded database.

The sharding method can be system-managed, composite, or user-defined.

The sharding method is shown under "Shard type" in the output of `gdsctl config sdb` as shown here.

    gdsctl> config sdb


    GDS Pool administrators
    ------------------------

    Replication Type
    ------------------------
    Data Guard

    Shard type
    ------------------------
    System-managed

    Shard spaces
    ------------------------
    shd1

    Services
    ------------------------
    srv1

#### Checking the Replication Type

Run `gdsctl config sdb` to check which method is used for shard replication in the sharded database.

The replication type is shown under "Replication Type" in the output of `gdsctl config sdb` as shown here.

    gdsctl> config sdb


    GDS Pool administrators
    ------------------------

    Replication Type
    ------------------------
    Data Guard

    Shard type
    ------------------------
    System-managed

    Shard spaces
    ------------------------
    shd1

    Services
    ------------------------
    srv1

Table 12-1 Replication types in config sdb output

| Replication Type  | Value Shown in Output |
|:------------------|:----------------------|
| Oracle Data Guard | Data Guard            |
| Oracle GoldenGate | Golden Gate           |

#### Checking the Oracle Data Guard Protection Mode

You can run `gdsctl config shardspace` on a given shardspace to check the Oracle Data Guard protection mode in your GDSCTL session, rather than switching to DGMGRL.

Data Guard can be configured in three different protection modes: MaxProtection, MaxAvailability, and MaxPerformance.

The Data Guard protection mode is shown under PROTECTION MODE in the `gdsctl config shardspace` command output, as shown here.

    GDSCTL> config shardspace -shardspace shd1
    Shard Group                   Region                        Role
    -----------                   ------                        ----
    dbs1                          east                          Primary

    PROTECTION_MODE               Chunks
    ---------------               ------
    MaxProtection                 6

#### Checking Which Shards Are Mapped to a Key

You can run `gdsctl config chunks -key` to check which shards are mapped to a sharding key.

Example 1: Single Table Family

In the following example, there is only one table family in the sharded database configuration, and the table is partitioned (sharded) on data type number.

In this example, the user is checking which chunk sharding key value "2" is mapped to. In the output it shows sharding key 2 is mapped to chunk "3" and is present in the database "aime1b".

    GDSCTL> config chunks -key 2
    Range Definition
    ------------------------
    Chunks    Range Definition
    ------    ----------------
    3         1431655764-2147483646

    Databases
    ------------------------
    aime1b

Similarly, this can be done for any data type sharding is done on. Also, a multiple column sharding key can be checked with comma separated values.

The range definition is the range of hash values and can be ignored.

Example 2: Multiple Table Families

In a multiple table family configuration, add the option `-table_family` to specify the table family to which the specified sharding key belongs.

The `config chunks` command lists shards from all shardgroups in the topology. This example also lists a Data Guard standby shardgroup, as shown by the addition of "aime1e" to the Databases (shards) list.

    GDSCTL> config chunks -key 1 -table_family testuserfam3.customersfam1

    Range Definition
    ------------------------
    Chunks    Range Definition
    ------    ----------------
    1         0-357913941

    Databases
    ------------------------
    aime1b
    aime1e

Example 3: Specifying a Multiple Column Sharding Key

When a table is sharded by multiple columns, specify the sharding key value as a comma-separated list as shown here.

    GDSCTL> config chunks -key 10,mary,2010-04-04

    Range Definition
    ------------------------
    Chunks    Range Definition
    ------    ----------------
    4         1288490187-1717986916

    Databases
    ------------------------
    aime1b
    aime1e

#### Checking Shard Operation Mode (Read-Only or Read-Write)

You can check whether shards are running in read-only or read-write mode by running `gdsctl config chunks -cross_shard`.

The `gdsctl config chunks -cross_shard` command output shows which shards, listed under "Database", are running in read-only and read-write modes, as shown below. The command also lists the chunk ranges on those shards.

    gdsctl config chunks -cross_shard

    Read-Only cross shard targets
    ------------------------
    Database                      From To
    --------                      ---- --
    tst3b_cdb2_pdb1               1    3
    tst3c_cdb3_pdb1               9    10
    tst3d_cdb2_pdb1               4    5
    tst3e_cdb3_pdb1               6    8

    Chunks not offered for cross-shard
    ------------------------
    Shard space    From To
    -----------    ---- --

    Read-Write cross-shard targets
    ------------------------
    Database                      From To
    --------                      ---- --
    tst3b_cdb2_pdb1               1    5
    tst3c_cdb3_pdb1               6    10

    Chunks not offered for Read-Write cross-shard activity
    ------------------------
    Data N/A

#### Checking DDL Text

Run `gdsctl show ddl -ddl ``ddl_id` to get the text for the specified DDL.

The DDL numeric identifier is specified with `-ddl ``ddl_id` to get the text and other details of a particular DDL, as shown here.

    gdsctl show ddl -ddl 5

    DDL Text: CREATE SHARDED TABLE Customers ( CustNo NUMBER NOT NULL, Name VARCHAR2(50), Address VARCHAR2(250), Location VARCHAR2(20), Class VARCHAR2(3), CONSTRAINT RootPK PRIMARY KEY(CustNo)) PARTITION BY CONSISTENT HASH (CustNo) PARTITIONS AUTO TABLESPACE SET ts1
    Owner: TESTUSER1
    Object name: CUSTOMERS
    DDL type: C
    Obsolete: 0
    Failed shards:

**Note:**

The `show ddl` command output might be truncated. You can run `SELECT ddl_text FROM gsmadmin_internal.ddl_requests` on the shard catalog to see the full text of the statements.

#### Checking Chunk Migration Status

Run `gdsctl config chunks -show_reshard` to check the status of chunk migration.

A chunk move is a long running operation, whether user-initiated or internal (during incremental deploy), so if you need to check the status, the `gdsctl config chunks -show_reshard` provides the following status indicators as the move progresses.

- empty - indicates no chunk migration in progress

- scheduled - chunk is pending movement, which could be because it is waiting on another chunk move to complete, or the move didn't initiate due to some error

- running - current in progress

- failed - chunk move failed. Check GSM traces and source and target database traces for details.

In the following example, chunk move status is shown in the "Ongoing chunk movement" table in the command output.

    gdsctl config chunks -show_reshard

    Chunks
    ------------------------
    Database                      From      To
    --------                      ----      --
    tst3b_cdb2_pdb1               1         6
    tst3c_cdb3_pdb1               7         10
    tst3d_cdb2_pdb1               1         6
    tst3e_cdb3_pdb1               7         10

    Ongoing chunk movement
    ------------------------
    Chunk     Source                        Target                        status
    -----     ------                        ------                        ------
    7         tst3c_cdb3_pdb1               tst3b_cdb2_pdb1               Running
    8         tst3c_cdb3_pdb1               tst3b_cdb2_pdb1               scheduled
    9         tst3c_cdb3_pdb1               tst3b_cdb2_pdb1               scheduled
    10        tst3c_cdb3_pdb1               tst3b_cdb2_pdb1               scheduled

#### Checking Table Type (Sharded or Duplicated)

You can check whether tables are sharded or duplicated in dba/all/user_tables using `SELECT TABLE_NAME,SHARDED,DUPLICATED FROM user_tables;`.

In the following example, column "S" indicates whether a table is sharded, and column "D" indicates whether a table is duplicated.

    SQL> select TABLE_NAME,SHARDED,DUPLICATED from user_tables;

    TABLE_NAME      S D
    --------------- - -
    CUSTOMERS       Y N
    DUP1            N Y
    LINEITEMS       Y N
    MLOG$_DUP1      N N
    ORDERS          Y N

#### Checking User Type (Local or ALL_SHARD)

You can find out which users are created as local users and which are sharded database users by selecting the username and ALL_SHARD column in dba/all/user_users.

    SQL>  select USERNAME,ALL_SHARD from users_users where username='TESTUSER1';

    USERNAME        ALL_SHARD
    --------------- ---------
    TESTUSER1       YES

#### Identifying Tables Created as Sharded Tablespaces

You can find out whether tablespaces are used for a sharded table by selecting the TABLESPACE_NAME and CHUNK_TABLESPACE columns in dba/all/user_tablespaces.

The value in the CHUNK_TABLESPACE column is Y in dba/all/user_tablespaces if it is a tablespace for a sharded table.

    SQL> select TABLESPACE_NAME,CHUNK_TABLESPACE from user_tablespaces;

    TABLESPACE_NAME                C
    ------------------------------ -
    SYSTEM                         N
    SYSAUX                         N
    TEMP                           N
    SYSEXT                         N
    TS1                            Y

#### Checking if Shard DDL is Enabled or Disabled

You can check if Shard DDL is enabled or disabled in the current SQL session.

These examples show the result of checking Shard DDL status after enabling and disabling Shard DDL.

    SQL> alter session enable shard ddl;

    Session altered.

    SQL> select shard_ddl_status from v$session where AUDSID = userenv('SESSIONID');

    SHARD_DD
    --------
    ENABLED

    SQL> alter session disable shard ddl;

    Session altered.

    SQL> select shard_ddl_status from v$session where AUDSID = userenv('SESSIONID');

    SHARD_DD
    --------
    DISABLED

#### Filtering Data by Sharding Key

You can set the `SHARD_QUERIES_RESTRICTED_BY_KEY` parameter to enable or disable data filtering by a specified sharding key.

The parameter `SHARD_QUERIES_RESTRICTED_BY_KEY` can be set with `ALTER` at the system or session level. If enabled, DMLs will only display select data for specified `SHARDING_KEY` set in the client connection.

In the following example, the client connection is established with a shard with `SHARDING_KEY` specified as "1". However, when the client runs a `SELECT` on the customers table, all of the rows in that table in the shard are displayed.

    connection established for client with sharding_key=1

    SQL> select * from customers order by custno;

        CUSTNO NAME       ADDRESS    LOCATION   CLA
    ---------- ---------- ---------- ---------- ---
             1 John       Oracle KM  Bangalore  A
            50 Larry      Oracle HQ  SFO        B

    2 rows selected.

    SQL>

Now, as shown below, we enable session level filtering, and the result of the same `SELECT` statement is restricted to only the single row that matches the `SHARD_KEY` specified in the client connection.

    SQL> alter session set shard_queries_restricted_by_key = true;

    Session altered.

    SQL> select current_shard_key from dual;

    CURRENT_SHARD_KEY
    -----------------
                    1

    1 row selected.

    SQL> select * from customers;

        CUSTNO NAME       ADDRESS    LOCATION   CLA
    ---------- ---------- ---------- ---------- ---
             1 John       Oracle KM  Bangalore  A

#### Setting the Duplicated Table Refresh Rate

You can modify the refresh rate for duplicated tables by setting the `SHRD_DUPL_TABLE_REFRESH_RATE` database parameter.

By default duplicated tables are refreshed every 60 seconds. The example below shows increasing the refresh interval to 100 seconds.

    SQL> show parameter refresh

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- ------------------------------
    shrd_dupl_table_refresh_rate         integer     60

    SQL> alter system set shrd_dupl_table_refresh_rate=100 scope=both;

    System altered.

    SQL> show parameter refresh

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- ------------------------------
    shrd_dupl_table_refresh_rate         integer     100

### Oracle Sharding Tracing and Debug Information

The following topics explain how to enable tracing and find the logs.

#### Enabling Tracing for Oracle Sharding

Enable PL/SQL tracing to track down issues in the sharded database.

To get full tracing, set the `GWM_TRACE` level as shown here. The following statement provides immediate tracing, but the trace is disabled after a database restart.

    ALTER SYSTEM SET EVENTS 'immediate trace name GWM_TRACE level 7';

The following statement enables tracing that continues in perpetuity, but only after restarting the database.

    ALTER SYSTEM SET EVENT='10798 trace name context forever, level 7' SCOPE=spfile;

It is recommended that you set both of the above traces to be thorough.

To trace everything in the Oracle Sharding environment, you must enable tracing on the shard catalog and all of the shards. The traces are written to the RDBMS session trace file for either the GDSCTL session on the shard catalog, or the session(s) created by the shard director (a.k.a. GSM) on the individual shards.

#### Where to Find Oracle Sharding Alert Logs and Trace Files

There are several places to look for trace and alert logs in the Oracle Sharding environment.

Standard RDBMS trace files located in diag/rdbms/.. will contain trace output.

Output from ‘deploy’ will go to job queue trace files db_unique_name\_jXXX\_PID.trc.

Output from other GDSCTL commands will go to either a shared server trace file db_unique_name\_sXXX\_PID.trc or dedicated trace file db_unique_name\_ora\_PID.trc depending on connect strings used.

Shared servers are typically used for many of the connections to the catalog and shards, so the tracing is in a shared server trace file named SID\_s00\*.trc.

GDSCTL has several commands that can display status and error information.

Use `GDSCTL STATUS GSM` to view locations for shard director (GSM) trace and log files.

    GDSCTL> status
    Alias                     SHARDDIRECTOR1
    Version                   18.0.0.0.0
    Start Date                25-FEB-2016 07:27:39
    Trace Level               support
    Listener Log File         /u01/app/oracle/diag/gsm/slc05abw/sharddirector1/alert/log.xml
    Listener Trace File       /u01/app/oracle/diag/gsm/slc05abw/sharddirector1/trace/
    ora_10516_139939557888352.trc
    Endpoint summary          (ADDRESS=(HOST=shard0)(PORT=1571)(PROTOCOL=tcp))
    GSMOCI Version            2.2.1
    Mastership                N
    Connected to GDS catalog  Y
    Process Id                10535
    Number of reconnections   0
    Pending tasks.     Total  0
    Tasks in  process. Total  0
    Regional Mastership       TRUE
    Total messages published  71702
    Time Zone                 +00:00
    Orphaned Buddy Regions:   None
    GDS region                region1
    Network metrics:
       Region: region2 Network factor:0

The non-XML version of the alert.log file can be found in the /trace directory as shown here.

    /u01/app/oracle/diag/gsm/shard-director-node/sharddirector1/trace/alert*.log

To decrypt log output in GSM use the following command.

    GDSCTL> set _event 17 -config_only

Master shard director (GSM) trace/alert files include status and errors on any and all asynchronous commands or background tasks (move chunk, split chunk, deploy, shard registration, Data Guard configuration, shard DDL execution, etc.)

To find pending AQ requests for the shard director, including error status, use GDSCTL CONFIG.

To see ongoing and scheduled chunk movement, use GDSCTL CONFIG CHUNKS -show_reshard

To see shards with failed DDLs, use GDSCTL SHOW DDL -failed_only

To see the DDL error information for a given shard, use GDSCTL CONFIG SHARD -shard shard_name

### Common Error Patterns and Resolutions for Sharded Databases

See the following topics for information about troubleshooting common errors in Oracle Sharding.

#### Issues Starting Remote Scheduler Agent

If you encounter issues starting Remote Scheduler Agent on all the shard hosts, try the following:

To start Scheduler you must be inside ORACLE_HOME on each shard server.

    [oracle@shard2 ~]$ echo welcome | schagent -registerdatabase 192.0.2.24 8080
    Agent Registration Password?
    Failed to get agent Registration Info from db: No route to host

    Solution: Disable firewall

    service ipchains stop
    service iptables stop
    chkconfig ipchains off
    chkconfig iptables off

#### Shard Director Fails to Start

If you encounter issues starting the shard director, try the following:

To start Scheduler you must be inside ORACLE_HOME on each shard server.

    GDSCTL>start gsm -gsm shardDGdirector
    GSM-45054: GSM error
    GSM-40070: GSM is not able to establish connection to GDS catalog

    GSM alert log, /u01/app/oracle/diag/gsm/shard1/sharddgdirector/trace/alert_gds.log
    GSM-40112: OCI error. Code (-1). See GSMOCI trace for details.
    GSM-40122: OCI Catalog Error. Code: 12514. Message: ORA-12514: TNS:listener does not
    currently know of service requested in connect descriptor
    GSM-40112: OCI error. Code (-1). See GSMOCI trace for details.
    2017-04-20T22:50:22.496362+05:30
    Process 1 in GSM instance is down
    GSM shutdown is successful
    GSM shutdown is in progress
    NOTE : if not message displayed in the GSM log then enable GSM trace level to 16
    while adding GSM itself.

1.  Remove the newly created shard director (GSM) that failed to start.

        GDSCTL> remove gsm -gsm shardDGdirector

2.  Add the shard director using trace level 16.

        GDSCTL> add gsm -gsm shardDGdirector -listener port_num -pwd gsmcatuser_password
         -catalog hostname:port_num:shard_catalog_name
         -region region1 -trace_level 16

3.  If the shard catalog database is running on a non-default port (other than 1521), set the remote listener.

        SQL> alter system set local_listener='(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)
        (HOST=hostname)(PORT=port_num)))';

#### Errors From Shards Created with CREATE SHARD

For errors that occur during a DEPLOY from shards created with the GDSCTL CREATE SHARD command check the following:

- Remote Scheduler Agent logs on shard hosts

- DBA_SCHEDULER_JOB_RUN_DETAILS view on shard catalog

- NETCA/DBCA output files in \$ORACLE_BASE/cfgtoollogs on shard hosts

#### Issues Using Create Shard

The following are solutions to some issues that occur when using the GDSCTL CREATE SHARD command..

##### Make sure to create \$ORACLE_BASE/oradata and \$ORACLE_BASE/fast_recovery_area directories to avoid the following errors

    GDSCTL> create shard -shardgroup primary_shardgroup -destination che -osaccount
     oracle -ospassword oracle
    GSM-45029: SQL error
    ORA-03710: directory does not exist or is not writeable at destination:
     $ORACLE_BASE/oradata
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 6920
    ORA-06512: at "SYS.DBMS_SYS_ERROR", line 86
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 4730
    ORA-06512: at line 1

    GDSCTL>create shard -shardgroup primary_shardgroup -destination che -osaccount oracle
     -ospassword oracle
    GSM-45029: SQL error
    ORA-03710: directory does not exist or is not writeable at destination:
     $ORACLE_BASE/fast_recovery_area
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 6920
    ORA-06512: at "SYS.DBMS_SYS_ERROR", line 86
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 4755
    ORA-06512: at line 1

Solution: Create oradata,fast_recovery_area under \$ORACLE_BASE on all the shard hosts.

##### Privilege issues

    GDSCTL>create shard -shardgroup primary_shardgroup -destination blr -credential cred
    GSM-45029: SQL error
    ORA-02610: Remote job failed with error:
    EXTERNAL_LOG_ID="job_79126_3",
    USERNAME="oracle",
    STANDARD_ERROR="Launching external job failed: Login executable not setuid-root"
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 6920
    ORA-06512: at "SYS.DBMS_SYS_ERROR", line 86
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 4596
    ORA-06512: at line 1

Solution: Make sure to have root privilege on following directories,

    chown root $ORACLE_HOME/bin/extjob
    chmod 4750 $ORACLE_HOME/bin/extjob
    chown root $ORACLE_HOME/rdbms/admin/externaljob.ora
    chmod 640 $ORACLE_HOME/rdbms/admin/externaljob.ora
    chown root $ORACLE_HOME/bin/jssu
    chmod 4750 $ORACLE_HOME/bin/jssu

##### Error on create shard

    GDSCTL>create shard -shardgroup primary_shardgroup -destination mysql02 -osaccount
     oracle -ospassword oracle
    GSM-45029: SQL error
    ORA-03719: Shard character set does not match catalog character set.
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 7469
    ORA-06512: at "SYS.DBMS_SYS_ERROR", line 79
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 5770
    ORA-06512: at line 1

Solution: Check the JAVA version, it must be the same on the shard catalog and all shard servers.

    rpm -qa|grep java

#### Issues Using Deploy Command

    GDSCTL> deploy
    GSM-45029: SQL error
    ORA-29273: HTTP request failed
    ORA-06512: at "SYS.DBMS_ISCHED", line 3715
    ORA-06512: at "SYS.UTL_HTTP", line 1267
    ORA-29276: transfer timeout
    ORA-06512: at "SYS.UTL_HTTP", line 651
    ORA-06512: at "SYS.UTL_HTTP", line 1257
    ORA-06512: at "SYS.DBMS_ISCHED", line 3708
    ORA-06512: at "SYS.DBMS_SCHEDULER", line 2609
    ORA-06512: at "GSMADMIN_INTERNAL.DBMS_GSM_POOLADMIN", line 14284
    ORA-06512: at line 1

Solution : Check the \$ORACLE_HOME/data/pendingjobs for the exact error. ORA-1017 is thrown if any issues on wallet.

1.  On problematic Shard host stop the remote scheduler agent.

        schagent -stop

2.  rename wallet direcotry on Database home

        mv $ORACLE_HOME/data/wallet $ORACLE_HOME/data/wallet.old

3.  start the remote scheduler agent and it will create new wallet directory

        schagent -start
        schagent -status
        echo welcome | schagent -registerdatabase 10.10.10.10 8080
