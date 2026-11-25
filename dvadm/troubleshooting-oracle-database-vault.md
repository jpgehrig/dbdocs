You can troubleshoot Oracle Database Vault by using tools such as trace files or checking certain Oracle Database Vault reports.

- Using Trace Files to Diagnose Oracle Database Vault Events
  Trace files, which the database generates, capture important information to help you debug errors.
- General Diagnostic Tips
  Oracle provides general tips for diagnosing problems in realms, factors, and rule sets.
- Configuration Problems with Oracle Database Vault Components
  Oracle Database Vault provides reports to check configuration problems with realms, command rules, factors, rule sets, or secure application roles.
- Resetting Oracle Database Vault Account Passwords
  Backup accounts can help you reset lost passwords for users who have been granted the `DV_OWNER` and `DV_ACCTMGR` roles.

### E.1 Using Trace Files to Diagnose Oracle Database Vault Events

Trace files, which the database generates, capture important information to help you debug errors.

- About Using Trace Files to Diagnose Oracle Database Vault Events
  You can monitor the Oracle Database Vault database instance for server and background process events by enabling and checking the database instance trace files.
- Types of Oracle Database Vault Trace Events That You Can and Cannot Track
  You can use trace files to track a variety of Oracle Database Vault activities.
- Levels of Oracle Database Vault Trace Events
  You can use the several levels for Oracle Database Vault trace events.
- Performance Effect of Enabling Oracle Database Vault Trace Files
  Be careful about enabling trace files.
- Enabling Oracle Database Vault Trace Events
  You can use the `ALTER SESSION` or `ALTER SYSTEM` SQL statements to enable Oracle Database Vault trace events.
- Finding Oracle Database Vault Trace File Data
  The Linux `grep` command and the ADR Command Interpreter (`ADRCI`) command-line utility can find Oracle Database Vault trace file data.
- Disabling Oracle Database Vault Trace Events
  You can disable tracing for Oracle Database Vault events.

**Parent topic:** Troubleshooting Oracle Database Vault

#### E.1.1 About Using Trace Files to Diagnose Oracle Database Vault Events

You can monitor the Oracle Database Vault database instance for server and background process events by enabling and checking the database instance trace files.

Trace files reveal the Oracle Database Vault policy authorization success and failures. They are useful for providing information to help resolve bug and other issues that may occur.

To set tracing for Oracle Database Vault, you must have the `DV_ADMIN` role. To perform the configuration, you use either of the `ALTER SESSION SET EVENTS` or `ALTER SYSTEM SET EVENTS` SQL statements.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/monitoring-the-database.md) for more information about how to manage trace files

**Parent topic:** Using Trace Files to Diagnose Oracle Database Vault Events

#### E.1.2 Types of Oracle Database Vault Trace Events That You Can and Cannot Track

You can use trace files to track a variety of Oracle Database Vault activities.

Table E-1 describes these activities.

Table E-1 Contents of Oracle Database Vault Trace Files

| Database Vault Feature             | Description                                                                                                                                                                                                                            |
|:-----------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Realm authorizations               | The trace file tracks cases of realm authorization with a rule set and realm authorization to a role. See Example: Low Level Oracle Database Vault Realm Violations in a Trace File for examples of this type of trace file.           |
| Rule set evaluations               | The trace file includes information about a rule set evaluation from a realm authorization, for a command rule, the CONNECT command rule, and from a factor.                                                                           |
| Oracle Data Pump authorization     | The trace file includes Database Vault Data Pump authorization results and other user, object, and SQL text information.                                                                                                               |
| Oracle Scheduler job authorization | The trace file includes the Database Vault Oracle Scheduler job authorization results, job name, job owner, current statement, and so on.                                                                                              |
| Object privilege bypass            | The trace file tracks both direct grants and grants through a role. This type of trace is useful for cases where mandatory realms are not enabled, which enables users who have an object privilege to access realm protected objects. |
| Factor loading                     | The trace file tracks the expression and value for each factor loaded.                                                                                                                                                                 |
| Others                             | Object owner bypassed realm protection and other Database Vault failed and succeeded operations                                                                                                                                        |

**Parent topic:** Using Trace Files to Diagnose Oracle Database Vault Events

#### E.1.3 Levels of Oracle Database Vault Trace Events

You can use the several levels for Oracle Database Vault trace events.

These levels are as follows:

- Low prints the information for all failed Oracle Database Vault authorizations to a trace file. This type of trace file includes failed realm authorizations, failed factor loading, failed rule set evaluating, and so on. It has a low impact on Oracle Database performance.

- High prints trace records that include both successful and failed authorizations. Because this type of tracing tracks all the authorizations, the overhead is larger than that of the low level tracing. In addition, the trace files are usually larger.

- Highest prints the PL/SQL stack and function call stack to a trace file, as well as what is traced at level high (as described in Table E-1). It has the highest impact on Oracle Database performance.

**Parent topic:** Using Trace Files to Diagnose Oracle Database Vault Events

#### E.1.4 Performance Effect of Enabling Oracle Database Vault Trace Files

Be careful about enabling trace files.

Doing so can increase the overhead of the database instance operation, which could decrease performance.

**Parent topic:** Using Trace Files to Diagnose Oracle Database Vault Events

#### E.1.5 Enabling Oracle Database Vault Trace Events

You can use the `ALTER SESSION` or `ALTER SYSTEM` SQL statements to enable Oracle Database Vault trace events.

- Enabling Trace Events for the Current Database Session
  You can use the `ALTER SESSION SET EVENTS` SQL statement to enable trace events for the current database session.
- Enabling Trace Events for All Database Sessions
  You can use the `ALTER SYSTEM SET EVENTS` SQL statement to enable Database Vault trace events for all database sessions.
- Enabling Trace Events in a Multitenant Environment
  In a multitenant environment, trace events affect both the current user session and all database sessions.

**Parent topic:** Using Trace Files to Diagnose Oracle Database Vault Events

##### E.1.5.1 Enabling Trace Events for the Current Database Session

You can use the `ALTER SESSION SET EVENTS` SQL statement to enable trace events for the current database session.

1.  Log into the database instance as a user who has been granted the `DV_ADMIN` role and the `ALTER SESSION` system privilege.
    For example:

        sqlplus sec_admin_owen
        Enter password: password
        Connected.
2.  Enter the `ALTER SESSION SET EVENTS` SQL statement to set the tracing to low, high, or highest, as described in Levels of Oracle Database Vault Trace Events.
    - To turn on tracing for failed operations that have a low impact, enter one of the following statements:

          ALTER SESSION SET EVENTS 'TRACE[DV] DISK=LOW';

          ALTER SESSION SET EVENTS '47998 TRACE NAME CONTEXT FOREVER, LEVEL 1';

    - To turn on tracing for both failed and successful operations that have a high impact, enter one of the following statements:

          ALTER SESSION SET EVENTS 'TRACE[DV] DISK=HIGH';

          ALTER SESSION SET EVENTS '47998 TRACE NAME CONTEXT FOREVER, LEVEL 3';

    - To turn on tracing for both failed and successful operations with a function and PL/SQL call stack that has the highest impact, enter one of the following statements:

          ALTER SESSION SET EVENTS 'TRACE[DV] DISK=HIGHEST';

          ALTER SESSION SET EVENTS '47998 TRACE NAME CONTEXT FOREVER, LEVEL 4';

**Parent topic:** Enabling Oracle Database Vault Trace Events

##### E.1.5.2 Enabling Trace Events for All Database Sessions

You can use the `ALTER SYSTEM SET EVENTS` SQL statement to enable Database Vault trace events for all database sessions.

1.  Log into the database instance as a user who has been granted the `DV_ADMIN` role and the `ALTER SYSTEM` system privilege.
    For example:

        sqlplus sec_admin_owen
        Enter password: password
        Connected.
2.  Enter the `ALTER SYSTEM SET EVENTS` SQL statement, using the syntax that is shown in Step 2 in Enabling Trace Events for the Current Database Session.
    For example:

        ALTER SYSTEM SET EVENTS 'TRACE[DV] DISK=LOW';

Another way that you can enable trace events for all database sessions is to add the following line to the `init.ora` file, and then restart the database:

    event="47998 trace name context forever, level [trace_level]"

Replace `trace_level` with one of the following values:

- `1` for the lowest level of tracing

- `3` for the high level

- `4` for the highest level

For example:

    event="47998 trace name context forever, level [1]"

**Related Topics**

- Disabling Trace Events for All Database Sessions
- Levels of Oracle Database Vault Trace Events

**Parent topic:** Enabling Oracle Database Vault Trace Events

##### E.1.5.3 Enabling Trace Events in a Multitenant Environment

In a multitenant environment, trace events affect both the current user session and all database sessions.

- Trace events for the current user session: In a multitenant environment, running the `ALTER SESSION SET EVENTS` SQL statement from either the root or a pluggable database (PDB) enables tracing for the current user session. If you switch from one PDB to another PDB (by using the `ALTER SESSION SET CONTAINER` statement), then tracing is still enabled for the new PDB. You cannot enable tracing for a single PDB in a multitenant container database (CDB); the tracing applies to all PDBs and the root. Remember that you must have the `ALTER SESSION SET CONTAINER` system privilege to move from one PDB to another.

- Trace events for all database sessions: In a multitenant environment, running the `ALTER SYSTEM SET EVENTS` statement from either the root or a specific PDB enables tracing for all PDBs in the container database.

**Parent topic:** Enabling Oracle Database Vault Trace Events

#### E.1.6 Finding Oracle Database Vault Trace File Data

The Linux `grep` command and the ADR Command Interpreter (`ADRCI`) command-line utility can find Oracle Database Vault trace file data.

- Finding the Database Vault Trace File Directory Location
  You can find the full directory location of trace files by querying the `V$DIAG_INFO` dynamic view.
- Using the Linux grep Command to Search Trace Files for Strings
  To query or process the trace files, you can use the Linux `grep` command to search for strings.
- Using the ADR Command Interpreter (ADRCI) Utility to QueryTrace Files
  You can query trace files by using the ADR Command Interpreter (`ADRCI`) command-line utility.
- Example: Low Level Oracle Database Vault Realm Violations in a Trace File
  You can use trace file data to track low level realm violations.
- Example: High Level Trace Enabled for Oracle Database Vault Authorization
  You can track Oracle Database Vault authorizations in a trace file with high level trace enabled.
- Example: Highest Level Traces on Violations on Realm-Protected Objects
  You can track high level violations using trace files.

**Parent topic:** Using Trace Files to Diagnose Oracle Database Vault Events

##### E.1.6.1 Finding the Database Vault Trace File Directory Location

You can find the full directory location of trace files by querying the `V$DIAG_INFO` dynamic view.

- Query the `V$DIAG_INFO` dynamic view as follows:

      SELECT VALUE FROM V$DIAG_INFO WHERE NAME = 'Default Trace File';

Output similar to the following appears:

    VALUE
    --------------------------------------------------------------------------------
    /u01/app/oracle/product/12.1.0/log/diag/rdbms/orcl/orcl/trace/orcl_ora_7174.trc

**Parent topic:** Finding Oracle Database Vault Trace File Data

##### E.1.6.2 Using the Linux grep Command to Search Trace Files for Strings

To query or process the trace files, you can use the Linux `grep` command to search for strings.

- For example, to find the trace files that show realm authorization failures, enter the following command:

      grep 'Result=Realm Authorization Failed'  *.trc

**Parent topic:** Finding Oracle Database Vault Trace File Data

##### E.1.6.3 Using the ADR Command Interpreter (ADRCI) Utility to QueryTrace Files

You can query trace files by using the ADR Command Interpreter (`ADRCI`) command-line utility.

- To use the `ADRCI` utility to find trace file information, use the `SHOW` command.

For example, to use `ADRCI` to find the trace files, enter the `SHOW TRACEFILE` command:

    adrci --To start ACRCI from the command line
    adrci> show tracefile

    diag/rdbms/orcl/orcl/trace/orcl_m002_14551.trc
    diag/rdbms/orcl/orcl/trace/orcl_tmon_13450.trc
    diag/rdbms/orcl/orcl/trace/orcl_vktm_963.trc
    diag/rdbms/orcl/orcl/trace/alert_orcl.log
    ...

To find the number of all trace incidents:

    adrci> show incident

    ADR Home = /u01/app/oracle/product/12.1.0/log/diag/rdbms/orcl/orcl:
    *************************************************************************
    234 rows fetched

The following `ADRCI` command returns a list of all trace files whose name contains the word `ora`:

    adrci> show tracefile %ora%

    /u01/app/oracle/product/12.1.0/log/diag/rdbms/orcl/orcl/trace/orcl_ora_18841.trc
    /u01/app/oracle/product/12.1.0/log/diag/rdbms/orcl/orcl/trace/orcl_ora_12017.trc
    /u01/app/oracle/product/12.1.0/log/diag/rdbms/orcl/orcl/trace/orcl_ora_19372.trc
    /u01/app/oracle/product/12.1.0/log/diag/rdbms/orcl/orcl/trace/orcl_ora_12221.trc
    /u01/app/oracle/product/12.1.0/log/diag/rdbms/orcl/orcl/trace/orcl_ora_1600.trc
    ...

The following `ADRCI` command searches for trace files that contain the phrase `Realm Authorization Failed`:

    adrci> show trace %trc -xp "[payload like '%Realm Authorization Failed%']"

**See Also:**

- [Oracle Database Utilities](../sutil/oracle-adr-command-interpreter-adrci.md) for detailed information about the `ADRCI` utility

- [Oracle Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md) for information about viewing reports with the `ADRCI` utility

**Parent topic:** Finding Oracle Database Vault Trace File Data

##### E.1.6.4 Example: Low Level Oracle Database Vault Realm Violations in a Trace File

You can use trace file data to track low level realm violations.

Example E-1 shows an example of tracking low lever real violations.

Example E-1 Low Level Oracle Database Vault Realm Violations in a Trace File

    *** 2010-02-05 18:35:31.438
    *** SESSION ID:(34.559) 2010-02-05 18:35:31.438
    *** CLIENT ID:() 2010-02-05 18:35:31.438
    *** SERVICE NAME:(SYS$USERS) 2010-02-05 18:35:31.438
    *** MODULE NAME:(SQL*Plus) 2010-02-05 18:35:31.438
    *** ACTION NAME:() 2010-02-05 18:35:31.438

    Result=Realm Authorization Failed
            Realm_Name=realm 3      Required_Auth_Level=0
            Current_User=116
            Object_Owner=U1 Object_Name=T1  Object_Type=TABLE
            SQL_Text=INSERT INTO U1.T1 VALUES(30)

    Result=Realm Authorization Failed
            Realm_Name=realm 3      Required_Auth_Level=0
            Current_User=116
            Object_Owner=U1 Object_Name=T1  Object_Type=TABLE
            SQL_Text=DELETE FROM U1.T1

    Result=Realm Authorization Failed
            Realm_Name=realm 3      Required_Auth_Level=0
            Current_User=116
            Object_Owner=U1 Object_Name=T3  Object_Type=TABLE
            SQL_Text=CREATE TABLE U1.T3(C INT)

    *** 2010-02-05 18:35:34.465

    Result=Realm Authorization Failed
            Realm_Name=realm 3      Required_Auth_Level=0
            Current_User=116
            Object_Owner=U1 Object_Name=T1  Object_Type=TABLE
            SQL_Text=INSERT INTO U1.T1 VALUES(30)

    Result=Realm Authorization Failed
            Realm_Name=realm 3      Required_Auth_Level=0
            Current_User=116
            Object_Owner=U1 Object_Name=T1  Object_Type=TABLE
            SQL_Text=DELETE FROM U1.T1

**Parent topic:** Finding Oracle Database Vault Trace File Data

##### E.1.6.5 Example: High Level Trace Enabled for Oracle Database Vault Authorization

You can track Oracle Database Vault authorizations in a trace file with high level trace enabled.

Example E-2 shows an example of this type of trace file.

Example E-2 High Level Trace Enabled for Oracle Database Vault Authorization

    Result= Realm Authorization Passed
            Reason=Current user is the object owner
            Current_User=70 Command=SELECT
            Object_Owner=LBACSYS    Object_Name=LBAC$AUDIT  Object_Type=TABLE

    Result= Realm Authorization Passed
            Reason=Current user is the object owner
            Current_User=70 Command=SELECT
            Object_Owner=LBACSYS    Object_Name=LBAC$AUDIT  Object_Type=TABLE

    Result= Realm Authorization Passed
            Reason=Current user is the object owner
            Current_User=70 Command=SELECT
            Object_Owner=LBACSYS    Object_Name=LBAC$POL    Object_Type=TABLE

    Result= Realm Authorization Passed
            Reason=Current user is the object owner
            Current_User=70 Command=SELECT
            Object_Owner=LBACSYS    Object_Name=LBAC$USER_LOGON     Object_Type=VIEW

    ……

    Result= Realm Authorization Passed
            Reason=Current user is the object owner
            Current_User=70 Command=SELECT
            Object_Owner=LBACSYS    Object_Name=LBAC$POL    Object_Type=TABLE

    Result=Set Factor Value
            Factor_Name=Sensitive_Treatments        Factor_Expression=/SURGERY/PSYCHOLOGICAL

    Result=Set Factor Value
            Factor_Name=Database_Instance   Factor_Expression=UPPER(SYS_CONTEXT('USERENV','INSTANCE'))      Factor_Value=1

    Result=Set Factor Value
            Factor_Name=Client_IP   Factor_Expression=UPPER(SYS_CONTEXT('USERENV','IP_ADDRESS'))    Factor_Value=

    Result=Set Factor Value
            Factor_Name=Authentication_Method       Factor_Expression=UPPER(SYS_CONTEXT('USERENV','AUTHENTICATION_METHOD')) Factor_Value=PASSWORD
    ……

    *** ACTION NAME:() 2010-02-05 18:47:19.540

    Result=Rule Set Evaluation Failed
            Command=SELECT  RuleSet_ID=2    RuleSet_Name=Disabled
            Current_User=SYSTEM
            Object_Owner=U1 Object_Name=T1  Object_Type=TABLE
            SQL_Text=SELECT * FROM U1.T1

    Result=Rule Set Evaluation Succeeded
            Command=SELECT  RuleSet_ID=1    RuleSet_Name=Enabled
            Current_User=SYSTEM
            Object_Owner=U1 Object_Name=T1  Object_Type=TABLE
            SQL_Text=SELECT * FROM U1.T1

**Parent topic:** Finding Oracle Database Vault Trace File Data

##### E.1.6.6 Example: Highest Level Traces on Violations on Realm-Protected Objects

You can track high level violations using trace files.

Example E-3 shows how highest level violations that involve Oracle Scheduler jobs authorization can appear in a trace file when trace is enabled at the highest level.

Example E-3 Highest Level Traces on Violations on Realm-Protected Objects

    ------ Call Stack Trace ------
    kzvdvechk<-kzvdveqau<-kksfbc<-opiexe<-kpoal8<-opiodr<-ttcpip<-opitsk<-opiino<-opiodr<-opidrv<-sou2o<-opimai_real<-ssthrdmain<-main<-__libc_start_main<-_start

    Result=Object Privilege check passed
            Current_User=INVOKER2   Used_Role=1
            Object_Owner=SYSTEM     Object_Name=PRODUCT_PRIVS       Object_Type=VIEW
            SQL_Text=SELECT CHAR_VALUE FROM SYSTEM.PRODUCT_PRIVS WHERE (UPPER('SQL*PLUS') LIKE UPPER(PRODUCT)) AND ((USER LIKE USERID) OR (USERID = 'PUBLIC')) AND (UPPER(ATTRIBUTE) = 'ROLES')
    *** MODULE NAME:(SQL*Plus) 2010-02-05 18:57:53.973
    *** ACTION NAME:() 2010-02-05 18:57:53.973

    ----- Current SQL Statement for this session (sql_id=2sr63rjm45yfh) -----
    UPDATE INVOKER1.T1 SET A = 20
    ----- PL/SQL Stack -----
    ----- PL/SQL Call Stack -----
      object      line  object
      handle    number  name
    0x26a00e34         1  anonymous block
    0x2495b000       185  package body SYS.DBMS_ISCHED
    0x24958fb8       486  package body SYS.DBMS_SCHEDULER
    0x247bbb34         1  anonymous block

    ------ Call Stack Trace ------
    kzvdvechk<-kzvdveqau<-kksfbc<-opiexe<-opipls<-opiodr<-__PGOSF151_rpidrus<-skgmstack<-rpidru<-rpiswu2<-rpidrv<-psddr0<-psdnal<-pevm_EXECC<-pfrinstr_EXECC<-pfrrun_no_tool<-pfrrun<-plsql_run<-peicnt<-kkxexe<-opiexe<-kpoal8<-opiodr<-kpoodr<-upirtrc<-kpurcsc<-kpuexec
    <-OCIStmtExecute<-jslvec_execcb<-jslvswu<-jslve_execute0<-jskaJobRun<-jsiRunJob<-jsaRunJob<-spefcmpa<-spefmccallstd<-pextproc<-__PGOSF495_peftrusted<-__PGOSF522_psdexsp<-rpiswu2<-psdextp<-pefccal<-pefcal<-pevm_FCAL<-pfrinstr_FCAL<-pfrrun_no_tool<-pfrrun<-plsql_run
    <-peicnt<-kkxexe<-opiexe<-kpoal8<-opiodr<-ttcpip<-opitsk<-opiino<-opiodr<-opidrv<-sou2o<-opimai_real<-ssthrdmain<-main<-__libc_start_main<-_start

    Result=Realm Authorization Succeeded
            Realm_Name=jobowner realm       Used_Auth_Level=0
            Current_User=119
            Object_Owner=INVOKER1   Object_Name=T1  Object_Type=TABLE
            SQL_Text=UPDATE INVOKER1.T1 SET A = 20

    Result=Scheduler Job Authorization Succeeded
            Current_User=JOBOWNER   Logon_User=INVOKER2
            Job_Owner=JOBOWNER      Job_Name=DMLJOB1
            Object_Owner=INVOKER1   Object_Name=T1  Object_Type=TABLE
            SQL_Text=UPDATE INVOKER1.T1 SET A = 20

**Parent topic:** Finding Oracle Database Vault Trace File Data

#### E.1.7 Disabling Oracle Database Vault Trace Events

You can disable tracing for Oracle Database Vault events.

- Disabling Trace Events for the Current Database Session
  You can use the `ALTER SESSION SET EVENTS` SQL statement to disable Database Vault tracing for the current database session.
- Disabling Trace Events for All Database Sessions
  You can use the `ALTER SYSTEM SET EVENTS` SQL statement to disable Database Vault tracing for all database sessions.
- Disabling Trace Events in a Multitenant Environment
  Disabling trace events in a multitenant environment affects both the current user session and all database sessions.

**Parent topic:** Using Trace Files to Diagnose Oracle Database Vault Events

##### E.1.7.1 Disabling Trace Events for the Current Database Session

You can use the `ALTER SESSION SET EVENTS` SQL statement to disable Database Vault tracing for the current database session.

1.  Log into the database instance as a user who has been granted the `DV_ADMIN` role and the `ALTER SESSION` system privilege.
    For example:

        sqlplus sec_admin_owen
        Enter password: password
        Connected.
2.  Enter both of the following SQL statements to disable tracing:
        ALTER SESSION SET EVENTS 'TRACE[DV] OFF';
        ALTER SESSION SET EVENTS '47998 trace name context off';

    Alternatively, you can use the `ALTER SYSTEM` statement as well:

        ALTER SYSTEM SET EVENTS 'TRACE[DV] OFF';
        ALTER SYSTEM SET EVENTS '47998 trace name context off';

**Parent topic:** Disabling Oracle Database Vault Trace Events

##### E.1.7.2 Disabling Trace Events for All Database Sessions

You can use the `ALTER SYSTEM SET EVENTS` SQL statement to disable Database Vault tracing for all database sessions.

1.  Log into the database instance as a user who has been granted the `DV_ADMIN` role and the `ALTER SYSTEM` system privilege.
    For example:

        sqlplus sec_admin_owen
        Enter password: password
        Connected.
2.  Enter the `ALTER SYSTEM SET EVENTS` SQL statement, using the syntax that is shown in Step 2 in Disabling Trace Events for the Current Database Session.
    For example:

        ALTER SYSTEM SET EVENTS 'TRACE[DV] OFF';

Another way that you can disable trace events for all database sessions is to add the following line to the `init.ora` file, and then restart the database:

    event="47998 trace name context off"

Ensure that the `init.ora` file does not have any conflicting `47998` lines, such as `event="47998 trace name context forever, level [1]"`.

**Parent topic:** Disabling Oracle Database Vault Trace Events

##### E.1.7.3 Disabling Trace Events in a Multitenant Environment

Disabling trace events in a multitenant environment affects both the current user session and all database sessions.

- Trace events for the current user session: In a multitenant environment, running the `ALTER SESSION SET EVENTS` SQL statement from either the root or a PDB disables tracing for the current user session. If you switch from one PDB to another PDB (by using the `ALTER SESSION SET CONTAINER` statement), then tracing is still disabled for the new PDB. You cannot disable tracing for a single PDB in a CDB; the tracing applies to all PDBs and the root. Remember that you must have the `ALTER SESSION SET CONTAINER` system privilege to move from one PDB to another.

- Trace events for all database sessions: In a multitenant environment, running the `ALTER SYSTEM SET EVENTS` statement from either the root or a specific PDB disables tracing for all PDBs in the CDB.

**Parent topic:** Disabling Oracle Database Vault Trace Events

### E.2 General Diagnostic Tips

Oracle provides general tips for diagnosing problems in realms, factors, and rule sets.

These guidelines are as follows:

- For realm protections, verify that a user has the underlying system or object privileges (granted directly or through a role) that might affect the command.

- If a realm authorization is not working, verify that the account roles are set correctly.

- For PL/SQL expressions used in factors and rule sets, grant the `EXECUTE` privilege on the PL/SQL package functions used in these expressions directly to the account and determine if the results appear to be correct.

- Use the auditing reports to diagnose problems in general. See [Oracle Database Vault Auditing Reports](oracle-database-vault-reports.md) for more information.

**Parent topic:** Troubleshooting Oracle Database Vault

### E.3 Configuration Problems with Oracle Database Vault Components

Oracle Database Vault provides reports to check configuration problems with realms, command rules, factors, rule sets, or secure application roles.

See the following sections for more information:

- [Command Rule Configuration Issues Report](oracle-database-vault-reports.md)

- [Factor Configuration Issues Report](oracle-database-vault-reports.md)

- [Factor Without Identities Report](oracle-database-vault-reports.md)

- [Identity Configuration Issues Report](oracle-database-vault-reports.md)

- [Realm Authorization Configuration Issues Report](oracle-database-vault-reports.md)

- [Rule Set Configuration Issues Report](oracle-database-vault-reports.md)

- [Secure Application Configuration Issues Report](oracle-database-vault-reports.md)

To run these reports, see [Running the Oracle Database Vault Reports](oracle-database-vault-reports.md).

**Parent topic:** Troubleshooting Oracle Database Vault

### E.4 Resetting Oracle Database Vault Account Passwords

Backup accounts can help you reset lost passwords for users who have been granted the `DV_OWNER` and `DV_ACCTMGR` roles.

- Resetting the DV_OWNER User Password
  You can use the `DV_OWNER` backup account to reset the `DV_OWNER` user password.
- Resetting the DV_ACCTMGR User Password
  You can use the `DV_ACCTMGR` backup account to reset the `DV_ACCTMGR` user password.

**Parent topic:** Troubleshooting Oracle Database Vault

#### E.4.1 Resetting the DV_OWNER User Password

You can use the `DV_OWNER` backup account to reset the `DV_OWNER` user password.

To reset the `DV_OWNER` user password, you must temporarily revoke the `DV_OWNER` role from this user, reset the password, and then re-grant the role back to the user.

1.  Log in to the database instance as the backup user for the `DV_OWNER` user account.
    For example:

        sqlplus dbv_owner_backup
        Enter password: password
2.  Revoke the `DV_OWNER` role from the `DV_OWNER` user who has lost the password.
    For example:

        REVOKE DV_OWNER FROM sec_admin_owen;
3.  Connect as a user who has been granted the `DV_ACCTMGR` role.
    For example:

        CONNECT accts_admin_ace
        Enter password: password
4.  Reset the password for the `DV_OWNER` user.
        ALTER USER sec_admin_owen IDENTIFIED BY password;

    Follow the guidelines in [Oracle Database Security Guide](../dbseg/configuring-authentication.md) to replace `password` with a password that is secure.
5.  Connect as the backup `DV_OWNER` user.
        CONNECT dbv_owner_backup
        Enter password: password
6.  Grant the `DV_OWNER` role back to the `DV_OWNER` user.
        GRANT DV_OWNER TO sec_admin_owen WITH ADMIN OPTION;

**Note:**

Ensure that the backup `DV_OWNER` account is safely stored in case it is needed again.

**Parent topic:** Resetting Oracle Database Vault Account Passwords

#### E.4.2 Resetting the DV_ACCTMGR User Password

You can use the `DV_ACCTMGR` backup account to reset the `DV_ACCTMGR` user password.

To reset the `DV_ACCTMGR` user password, you can use the backup `DV_ACCTMGR` account to reset this user’s password.

1.  Log in to the database instance as the backup user for the `DV_ACCTMGR` user account.
    For example:

        sqlplus dbv_acctmgr_backup
        Enter password: password
2.  Reset the password for the `DV_ACCTMGR` user.
    For example:

        ALTER USER accts_admin_ace IDENTIFIED BY password;

    Follow the guidelines in [Oracle Database Security Guide](../dbseg/configuring-authentication.md) to replace `password` with a password that is secure.

**Note:**

Ensure that the backup `DV_ACCTMGR` account is safely stored in case it is needed again.

**Parent topic:** Resetting Oracle Database Vault Account Passwords
