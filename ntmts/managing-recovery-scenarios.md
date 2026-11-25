These topics describe how to create and schedule [Microsoft Transaction Server](glossary.md)-related Oracle transaction recovery.

- Microsoft Transaction Server Configuration Requirements

- Microsoft Transaction Server Transaction Recovery Overview

- Scheduling Automatic Microsoft Transaction Server Transaction Recovery

- Viewing Microsoft Transaction Server In-Doubt Transactions

- Modifying Registry Values for Oracle Fail Safe Configurations

### Microsoft Transaction Server Configuration Requirements

You must configure the Microsoft Transaction Server and Oracle Database environments after installing or migrating [Oracle Services for Microsoft Transaction Server (OraMTS)](glossary.md).

Configuration is not required on the Windows computer if a Microsoft Transaction Server is installed on a computer.

To configure the Microsoft Transaction Server, perform the following tasks on the computer where the Oracle Database is installed:

1.  Run the `oramtsadmin.sql` script against the database to create the Microsoft Transaction Server administrative user account (the default username is `mtssys`).

2.  Schedule automatic transaction recovery.

    See "Scheduling Automatic Microsoft Transaction Server Transaction Recovery"

3.  If you have an Oracle Fail Safe configuration, modify the registry values before or after running the `oramtsadmin.sql` script.

    See "Modifying Registry Values for Oracle Fail Safe Configurations".

### Microsoft Transaction Server Transaction Recovery Overview

Distributed transaction capabilities are required to use Microsoft Transaction Server with Oracle database. Microsoft Transaction Server-related Oracle transactions become in-doubt transactions when any of the following fail:

- Microsoft Transaction Server application

- Network

- [Microsoft Distributed Transaction Coordinator (MS DTC)](glossary.md)

An [Oracle MTS Recovery Service](glossary.md) resolves in-doubt transactions on the computer that started the failed transaction. An Oracle MTS Recovery Service is automatically installed with Oracle Services For Microsoft Transaction Server. Only one Oracle MTS Recovery Service can be installed for each computer. A scheduled recovery job on each Microsoft Transaction Server-enabled database permits the Oracle MTS Recovery Service to resolve in-doubt transactions.

The Oracle MTS Recovery Service resolves an in-doubt Microsoft Transaction Server transaction in the following order:

1.  The DBMS recovery job detects an in-doubt MTS-related transaction.

2.  The DBMS recovery job extracts the recovery service's endpoint address from the XID of the in-doubt transaction and requests the recovery service for the outcome of the MTS/MS DTC transaction.

3.  The recovery service requests its MS DTC for transaction outcome.

4.  The recovery service reports transaction outcome to the DBMS job process.

5.  The DBMS recovery job commits or terminates the in-doubt transaction.

### Scheduling Automatic Microsoft Transaction Server Transaction Recovery

OraMTS uses server-based recovery to resolve in-doubt transactions originated by MSDTC. To do this, the OraMTS administrator must be able to access the Windows middle-tier node through `UTL_HTTP`. `oramtsadmin.sql` grants execute privileges on `UTL_HTTP` to the OraMTS administrator, as shown in "Configuring Automatic Transaction Recovery"

**Note:**

Starting with Oracle version 11g, the DBA needs to create an access control list (ACL) as shown in "Creating an Access Control List (ACL)".

#### Creating an Access Control List (ACL)

For Oracle database version 11g and later, the DBA must create an access control list (ACL) that grants the OraMTS administrator the privilege to make out-bound HTTP connections. Example 3-1 demonstrates this:

Example 3-1 Creating an ACL List and Adding OraMTS Administrator to it

    BEGIN
       -- Create the new ACL, naming it "OraMTSadmin.xml", with a description.
       -- This provides the OraMTS administrative user e.g. MTSADMIN user FOO
       -- the privilege to connect
       DBMS_NETWORK_ACL_ADMIN.CREATE_ACL('OraMTSadmin.xml',
                                        'Allow usage to the UTL network packages',
                                        'FOO', TRUE, 'connect');
       -- Now grant privilege to resolve DNS names to the OraMTS administrative user
       DBMS_NETWORK_ACL_ADMIN.ADD_PRIVILEGE('OraMTSadmin.xml' ,
                                            'FOO', TRUE,'resolve');
      -- Specify which hosts this ACL applies to, in this case we are allowing
      -- access to all hosts. if one knew the list of all Windows middle-tier,
      -- these could be added one by one.
       DBMS_NETWORK_ACL_ADMIN.ASSIGN_ACL('OraMTSadmin.xml','*');
     END;

#### Configuring Automatic Transaction Recovery

Automatic transaction recovery is performed by scheduling a database job. A database job for in-doubt transactions must be scheduled for each database participating in Microsoft Transaction Server transactions.

Transaction recovery is configured by running the `oramtsadmin.sql` script, which triggers `utl_oramts.sql` and `prvtoramts.plb` scripts to create the PL/SQL package `utl_oramts`. The database view `oramts_2pc_pending` is also created to show in-doubt transactions related to Microsoft Transaction Server transactions.

The `oramtsadmin.sql` script:

- Creates the Microsoft Transaction Server administrator user account.

- Automatically schedules database jobs for transaction recovery every one minute.

  When the database job is run, it checks for unresolved global transactions in the database that are related to Microsoft Transaction Server. Information in the [transaction identifiers (XIDs)](glossary.md) of the in-doubt transactions identifies the computer on which the transaction was started. The Oracle MTS Recovery Service on that computer resolves the transaction.

- Schedules post-recovery cleanup every half hour.

Schedule automatic transaction recovery in the database by performing these tasks:

- Setting and Starting Up Database Job-Queue Processes

- Creating and Scheduling Automatic Transaction Recovery

##### Setting and Starting Up Database Job-Queue Processes

The `JOB_QUEUE_PROCESSES` initialization parameter specifies the maximum number of job slaves started on an instance.

To set and start up job-queue processes:

1.  Ensure that you have `SYSDBA` privileges.
2.  Go to the computer on which the Oracle Database is installed.
3.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
4.  Connect to the database as `SYSDBA`:
        SQL> CONNECT / AS SYSDBA
5.  Set the `JOB_QUEUE_PROCESSES` initialization parameter:
        JOB_QUEUE_PROCESSES = 1

    The default value for this parameter is `0`. Set this parameter to a value greater than `1` if there are many destinations to which to propagate the messages.
6.  Shut down the Oracle Database:
        SQL> SHUTDOWN
7.  Restart the Oracle Database:
        SQL> STARTUP
8.  Exit SQL\*Plus:
        SQL> EXIT

##### Creating and Scheduling Automatic Transaction Recovery

The `oramtsadmin.sql` script creates the Microsoft Transaction Server administrator user account with the default username `mtssys`. The Microsoft Transaction Server transaction recovery jobs run under the administrator user account.

The `oramtsadmin.sql` script runs the `utl_oramts.sql` script to grant the following privileges and roles to the administrator user account:

- `CREATE SESSION` role

- `SELECT_CATALOG_ROLE` role

- `FORCE_ANY_TRANSACTION` privilege

- `DBMS_JOBS` package, on which `EXECUTE` privileges are granted

- `DBMS_TRANSACTION` package, on which `EXECUTE` privileges are granted

To create and schedule automatic transaction recovery:

1.  Ensure that you have `SYSDBA` privileges.
2.  Log on to the computer where the Oracle Database is installed.
3.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
4.  Connect to the database as `SYSDBA`:
        SQL> CONNECT / AS SYSDBA
5.  Run the `oramtsadmin.sql` script:
        SQL> @ORACLE_BASE\ORACLE_HOME\oramts\admin\oramtsadmin.sql;

    You are prompted for the Microsoft Transaction Server administrator username and password. You can accept the default username of `mtssys` and password of `mtssys`, or change them.
6.  If you did change the password in step 5, you can change it using this script:
        SQL> ALTER USER USERNAME IDENTIFIED BY new_password;

    To change the username after completing this task, drop the user, rerun the `oramtsadmin.sql` script, and specify a different username when prompted.
7.  Exit SQL\*Plus:
        SQL> EXIT

A single PL/SQL package, `utl_oramts`, is created in the Microsoft Transaction Server administrator's schema. `utl_oramts` exposes these public procedures and creates this view:

- utl_oramts.show_indoubt Procedure

- utl_oramts.recover_automatic Procedure

- utl_oramts.forget_RMs Procedure

- oramts_2pc_pending View

###### utl_oramts.show_indoubt Procedure

Use this procedure to view Microsoft Transaction Server in-doubt transactions in the database. This procedure uses the `dbms_output` package to display results.

##### Description

This procedure requires `SERVEROUTPUT` set to `ON`.

    SQL> SET SERVEROUTPUT ON

    SQL> EXECUTE utl_oramts.show_indoubt;

The following information appears:

    =========================================================
    currently indoubt transactions
    =========================================================
    formatid    : 21255235
    gtrid           : C2229A505904974D81FB7316B147325900000000
    bqual       : 5BAB6A6B55CD294AA20335839110829C0100000000901944700050
    local txid  : 142.11.202
    tx state           : prepared
    protocol    : HTTP
    endpoint    : middletier-1@foo.com:2030
    =========================================================
    formatid    : 21255235
    gtrid           : 259DF9C8DFC5574F8876F0DF4E15CCAD00000000
    bqual       : 2C8DCED5B9816244BA2B73CC013EEB870100000000901944700050
    local txid  : 2.18.185
    tx state    : prepared
    protocol    : HTTP
    endpoint    : middletier-2@foo.com:2030

###### utl_oramts.recover_automatic Procedure

This procedure is run by the transaction recovery job. An automatic database job is scheduled for `utl_oramts.recover_automatic`. When the job is run, it checks for unresolved global transactions in the database that are related to Microsoft Transaction Server. Information in the XIDs of the in-doubt transactions identifies the computer on which the transaction started. The Oracle MTS Recovery Service is contacted and resolves the transactions.

###### utl_oramts.forget_RMs Procedure

Use this procedure to request the transaction manager (MS DTC) to forget resolved transactions. This procedure is run by the post-recovery cleanup job.

###### oramts_2pc_pending View

The view `oramts_2pc_pending` is created by executing `oramtsadmin.sql`. `oramts_2pc_pending` shows in-doubt transactions in the database. This view consists of the following columns:

##### Formatid

This is the `formatid` of the global transaction in the database.

##### global_transaction_id

This is the transaction identifier of the Oracle global transaction corresponding to the Microsoft Transaction Server transaction. In fact, this is the globally unique identifier (GUID) of the Microsoft Transaction Server transaction.

##### branch_id

This shows the branch identifier of the Oracle transaction. A single Microsoft Transaction Server transaction can have multiple Oracle global transactions. This depends on the number of Microsoft Transaction Server/COM+ components that span the same Microsoft Transaction Server transaction. All these transactions have the small global transaction identifier, but different branch identifiers.

##### local_tx_id

A local Oracle transaction corresponds to each Microsoft Transaction Server transaction. This column shows the identifier corresponding to this local transaction.

##### state

This shows the state of the transaction: pending, heuristically committed, heuristically terminated, and so on.

##### protocol

This is the protocol that the transaction recovery job in the database uses to communicate with the Oracle MTS Recovery Service.

##### endpoint

This is the endpoint of the Windows computer on which the Microsoft Transaction Server transaction originated. For HTTP connections, this translates to a hostname and port number.

### Viewing Microsoft Transaction Server In-Doubt Transactions

To view Microsoft Transaction Server–related in-doubt transactions in the database, use SQL\*Plus to query the view `oramts_2pc_pending`:

1.  Start SQL\*Plus with the Microsoft Transaction Server administrator user account:
        C:\> sqlplus mtsadmin_user/ mtsadmin_password
2.  Enter the following command:
        SQL> SELECT * FROM oramts_2pc_pending;

    This displays the computer on which the in-doubt transaction originated.

### Modifying Registry Values for Oracle Fail Safe Configurations

In typical configurations, the MS DTC and Oracle MTS Recovery Service run on the same computer. This ensures that the required information for transaction recovery is available to the Oracle-Microsoft Transaction Server integration layer.

In configurations where the Microsoft Transaction Server application is part of a Windows cluster (for example, the application can fail over to another node or host in the cluster), the MS DTC runs as a cluster-wide resource. All cluster nodes use a single instance of the MS DTC running on any cluster node.

If you have an Oracle Fail Safe configuration, make sure the following registry information is replicated on all nodes in the cluster participating in Microsoft Transaction Server transactions:

To modify registry values for Oracle Fail Safe configurations:

1.  Go to the computer on which the MS DTC and Oracle MTS Recovery Service are installed.
2.  Start the registry from the command prompt:
        C:\> regedt32

    The Registry Editor window appears.
3.  Go to `HKEY_LOCAL_MACHINE`\\`Software`\\`Oracle`\\`OracleMTSRecoveryService`.
4.  Copy the registry information appearing here to all nodes in the cluster.
5.  Reboot the computer on which you added the key.
