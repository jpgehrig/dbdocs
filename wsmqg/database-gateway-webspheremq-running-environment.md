The following topics describe the Oracle Database Gateway for WebSphere MQ running environment:

### Security Models

WebSphere MQ has its own authorization mechanism. Applications are allowed to perform certain operations on queues or queue managers only when their effective user ID has authorization for each operation.

The effective user ID, typically the operating system user, depends on the WebSphere MQ environment and the platform it runs on.

The effective user ID in an Oracle environment is not dependent on an operating system account or the platform. Because of this difference, the gateway provides two authorization models for Oracle applications to work with WebSphere MQ:

- Relaxed

- Strict

Although Oracle and operating system user IDs can be longer than 12 characters, the length of user IDs used for either model cannot exceed 12 characters. Oracle user accounts do not have a minimum number of characters required for their passwords, but some platforms and operating systems do. Take their requirements into consideration when deciding on a password or user ID.

The authorization model is configured with the `AUTHORIZATION_MODEL` parameter in the gateway initialization file.

**Related Topics**

- [Oracle Database Gateway for WebSphere MQ Initialization Parameters](database-gateway-webspheremq-initialization-parameters.md)

#### Relaxed Model

This model discards the Oracle user name and password.

The authorizations granted to the effective user ID of the gateway by the queue manager are the only associations an Oracle application has. For example, if the gateway user ID is granted permission to open or read messages, or place messages on a queue, then all Oracle applications that access the gateway can request those operations.

The effective user ID is determined by how the gateway runs:

- If the gateway runs as an MQI client application, then the user ID is determined by the MQI channel definition.

  **See Also:**

  Refer to IBM publications for more information about channel definitions

- If the gateway runs as an MQI server application, then the effective user ID of the gateway is the user account that started the Oracle Net listener and has authorization to all the WebSphere MQ objects that the Oracle application wants to access.

Oracle recommends using the relaxed model only if your application has minimal security requirements.

**Related Topics**

- Authorization for WebSphere MQ Objects

#### Strict Model

This model uses the Oracle user ID and password provided in the `CREATE DATABASE LINK` statement when a database link is created, or the current Oracle user ID and password if none was provided with `CREATE DATABASE LINK`.

The Oracle user ID:

- Must match a user account for the system that runs the gateway and for the system that runs the WebSphere MQ queue manager

- Must have authorization for all the accessed WebSphere MQ objects.

The authorization process to verify the Oracle user ID and password varies, depending on how the gateway runs.

**Related Topics**

- Authorization for WebSphere MQ Objects

##### Authorization Process for a WebSphere MQ Server Application

If the gateway runs as a WebSphere MQ server application, then the authorization process checks the user ID and password against the local or network password file.

If they match, then the gateway performs a SET-UID for the user ID and continues to run under this user ID. Further WebSphere MQ authorization checks happen for this user ID.

##### Authorization Process for a WebSphere MQ Client Application

If the gateway runs as a WebSphere MQ client application, then the authorization process checks the user ID and password against the local or network password file.

If they match, then the `MQ_USER_ID` and `MQ_PASSWORD` WebSphere MQ environment variables are set to the values of the user ID and password. If the channel definition specifies the `MCAUSER` WebSphere MQ environment variable as blank characters, then WebSphere MQ authorization checks are performed for the user ID.

If MCAUSER is set, not set, or security exits are defined for the MQI channel, then these override the gateway efforts.

**See Also:**

Refer to IBM publications for more information about WebSphere MQ environment variables.

#### Authorization for WebSphere MQ Objects

This topic describes the access authorization for WebSphere MQ objects.

The effective user ID for the relaxed model and the Oracle user ID for the strict model require the WebSphere MQ authorizations described in Table 8-1.

Table 8-1 WebSphere MQ Access Authorization

| Type of Access                                           | WebSphere MQ Authorization Keywords | Alternate WebSphere MQ Authorization Keywords         |
|:---------------------------------------------------------|:------------------------------------|:------------------------------------------------------|
| Permission to access the WebSphere MQ queue manager      | `all` or `allmqi`                   | `connect`<br>`setid`                                  |
| Permission to send messages to a WebSphere MQ queue      | `all` or `allmqi`                   | `passall`<br>`passid`<br>`put`<br>`setid`             |
| Permission to receive messages from a WebSphere MQ queue | `all` or `allmqi`                   | `browse`<br>`get`<br>`passall`<br>`passid`<br>`setid` |

**See Also:**

Refer to IBM publications for more information about WebSphere MQ authorizations.

### Transaction Support

Transactions from an Oracle application that use the gateway and invoke WebSphere MQ message queue operations are managed by the transaction coordinator at the Oracle database where the transaction originates.

#### Non‐Oracle Data Sources and Distributed Transactions

When an Oracle distributed database contains a gateway, the gateway must be properly configured to take part in a distributed transaction. 

The outcome of a distributed transaction involving a gateway should be that all participating sites roll back or commit their parts of the distributed transaction. All participating sites, including gateway sites, that are updated during a distributed transaction must be protected against failure and must be able to take part in the two‐phase commit mechanism.

A gateway that updates a target system as part of a distributed transaction must be able to take part in the automatic recovery mechanism, which might require that recovery information be recorded in transaction memory at the target system.

If a SQL‐based gateway is involved in a distributed transaction, the distributed database must be in a consistent state after the distributed transaction is committed.

A database gateway or a SQL‐based gateway with the procedural option translates remote procedure calls into target system calls. From the viewpoint of the Oracle transaction model, the gateway is like an Oracle database executing a PL/SQL block containing SQL statements that are used to access an Oracle database.

For a database gateway, it is unknown if a target system call alters data. To ensure the consistency of a distributed database, it must be assumed that a database gateway updates the target system. Accordingly, all remote procedure calls sent to a database gateway take part in a distributed transaction and must be protected by the two‐phase commit protocol. For example, you could issue the following SQL\*Plus statements:

    EXECUTE REMOTE_PROC@FACTORY;
    INSERT INTO DEBIT@FINANCE
    ROLLBACK;

In this example, `REMOTE_PROC` is a remote procedure call to access a database gateway, `DEBIT` is an Oracle table residing in an Oracle database, and `FACTORY` and `FINANCE` are database links used to access the remote sites.

#### Transaction Capability Types

When gateways are involved in a distributed transaction, the transaction capabilities of the non‐Oracle data source determine whether the data source can participate in two‐phase commit operations or distributed transactions.

Depending on the capabilities of the non‐Oracle data source, transactions can be classified as one of the following types:

| Type                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Read‐only                       | During a distributed transaction, the gateway provides read-only access to the data source, so the gateway can only be queried. A Read-only is used for target systems that use the presumed-commit model or do not support rollback mechanisms.                                                                                                                                                                                          |
| Single-site                     | During a distributed transaction, the target system is either read-only (other sites can be updated) or the only site updated (can participate in remote transactions). Single-site is used for target systems that support rollback, commit, and presumed-abort, but cannot prepare or commit-confirm as they have no distributed transaction memory, the ability to remember what happened during and after a distributed transaction.  |
| Commit-confirm                  | The gateway is a partial partner in the Oracle transaction mode. During a distributed transaction in which it is updated, the gateway must be the commit point site. Commit-confirm is used for target systems that support rollback, commit, presumed-abort, and commit-confirm, but do not support prepare. The commit-confirm capability requires distributed transaction memory.                                                      |
| Two-phase commit                | The gateway is a partial partner in the Oracle transaction model. During a distributed transaction, the gateway cannot be the commit point site.Two-phase commit is used for target systems that support rollback, commit, presumed-abort, and prepare, but do not support commit-confirm, because they have no distributed transaction memory.                                                                                           |
| Two-phase commit-commit confirm | The gateway is a full partner in the Oracle transaction model. During a distributed transaction, the gateway can be the commit point site, depending on the commit point strength defined in the gateway initialization file.This transaction type is used for target systems that support a full two-phased commit transaction model. That is, the target system supports rollback, commit, presumed-abort, prepare, and commit-confirm. |

#### Transaction Capability Types of Oracle Database Gateway for WebSphere MQ

Transactions from an Oracle application (that invoke WebSphere MQ message queue operations and that are using the gateway) are managed by the Oracle transaction coordinator at the Oracle database where the transaction originates.

The Oracle Database Gateway for WebSphere MQ provides the following transaction types:

##### Single-Site Transactions

Single-site transactions are supported for all WebSphere MQ environments and platforms.

Single-Site means that the gateway can participate in a transaction only when queues belonging to the same WebSphere MQ queue manager are updated. An Oracle application can select, but not update, data on any Oracle database within the same transaction that sends to, or receives a message from, a WebSphere MQ queue. To update objects in the Oracle database, the transaction involving the WebSphere MQ queue should first be committed or rolled back.

This default mode of the gateway is implemented using WebSphere MQ single-phase, where the queue manager acts as the synchronizing point coordinator.

##### Commit-Confirm Transactions

Commit-Confirm transactions are enhanced forms of single-site transactions and are supported for all WebSphere MQ environments and platforms.

Commit-confirm means that the gateway can participate in transactions when queues belonging to the same WebSphere MQ queue manager are updated and, at the same time, any number of Oracle databases are updated. Only one gateway with the commit-confirm model can join the distributed transaction because the gateway operates as the focal point of the transaction. To apply changes to queues of more than one queue manager, updates applied to one queue manager need to be committed before a new transaction is started for the next queue manager.

As with single-site transactions, commit-confirm transactions are implemented using WebSphere MQ single-phase, but it requires a dedicated recovery queue at the queue manager to log the transaction ID. At commit time, the gateway places a message in this queue with the message ID set to the Oracle transaction ID. After the gateway calls the queue manager to commit the transaction, the extra message on the transaction log queue becomes part of the overall transaction. This makes it possible to determine the outcome of the transaction in case of system failure, allowing the gateway to recover a failed transaction. When a transaction completes successfully, the gateway removes the associated message from the queue.

The WebSphere MQ administrator must create a reserved queue at the queue manager. The name of this queue is specified in the gateway initialization file with the `TRANSACTION_LOG_QUEUE` parameter. All Oracle users that access WebSphere MQ through the gateway should have full authorization for this queue. The transaction log queue is reserved for transaction logging only and must not be used, accessed, or updated other than by the gateway. When a system failure occurs, the Oracle recovery process checks the transaction log queue to determine the recovery strategy.

Two gateway initialization parameters, `TRANSACTION_RECOVERY_USER` and `TRANSACTION_RECOVERY_PASSWORD`, are set in the gateway initialization file to specify the user ID and password for recovery purposes. When set, the gateway uses this user ID and password combination for recovery work. The recovery user ID should have full authorization for the transaction log queue.

**Related Topics**

- [Oracle Database Gateway for WebSphere MQ Initialization Parameters](database-gateway-webspheremq-initialization-parameters.md)

### Troubleshooting

This section includes information about messages, error codes, gateway tracing, and gateway operations.

#### Message and Error Code Processing

The gateway architecture includes a number of components. Any of these components can detect and report an error condition while processing PL/SQL code.

An error condition can be complex, involving error codes and supporting data from multiple components. In all cases, the Oracle application receives a single Oracle error code on which to act.

Error conditions are represented in the following ways:

- Errors from the Oracle database

  Messages from the Oracle database are in the format ORA‐xxxxx or PLS‐xxxxx, where xxxxx is a code number.  ORA‐xxxxx is followed by text explaining the error code.

  For example:

      PLS‐00306: wrong number or types of arguments in call to 'MQOPEN'
      ORA‐06550: line7, column 3:
      PL/SQL: Statement ignored

- Gateway and WebSphere MQ errors

  When possible, a WebSphere MQ error code is converted to an Oracle error code. If that is not possible, then the Oracle error ORA‐29400 with the corresponding WebSphere MQ error code is returned.

  For Example:

      ORA-29400: data cartridge error
      MQI MQCONNX failed. completion code=2, reason code=2058

  **Note:**

  Because the Oracle database distinguishes only between a successful or failed outcome of all user operations, MQI calls that return a warning are reported as a successful operation.

**Related Topics**

- Common Error Codes

**See Also:**

[Oracle Database Error Messages](../errmg/index.md)

##### Interpreting Gateway Messages

Error codes are generally accompanied by additional message text, beyond the text associated with the Oracle message number.

The additional text includes details about the error.

Gateway messages have the following format:

    ORA‐nnnnn:error_message_text
    gateway_message_line

where:

- nnnn is an Oracle error number.

- `error_message_text` is the text of the message associated with the error.

- `gateway_message_line` is additional message text generated by the gateway.

#### Common Error Codes

The error conditions that are described in this section are common error conditions that an application might receive while using the gateway.

However, it does not cover all error situations.

ORA‐01017: invalid username/password; logon denied
Cause: Invalid username or password

Action: Logon denied

ORA‐29400: The MQSeries MQI call "call_name" fails with reason code mqi_code
Cause: An MQI call to a WebSphere MQ queue manager failed. The gateway could not complete the current operation.

Action: If `call_name` is `MQOPEN` and `mqi_code` is 2035, then do the following:

- If the gateway is configured for the relaxed security model, then use the WebSphere MQ administrative command interface to grant sufficient message privileges to the user account that started the Oracle Net listener. These privileges allow the user to send and receive messages for the specified WebSphere MQ queue. Refer to IBM publications for more information.

- If the gateway is configured for the strict security model, use the WebSphere MQ administrative command interface to grant message privileges to the user name specified in the `CREATE DATABASE LINK` statement. If no user name was specified in the `CREATE DATABASE LINK` statement, the privileges are granted to the current Oracle user ID. These privileges enable the user to send and receive messages for the specified WebSphere MQ queue. Refer to IBM publications for more information.

If `call_name` is `MQOPEN`, and if `mqi_code` is 2085, then verify that the queue that is specified in the WebSphere MQ profile exists at the WebSphere MQ queue manager that you are trying to access and that the queue name is correctly spelled and in the correct letter case.

**See Also:**

Refer to IBM publications for more information on `mqi_codes` other than 2035 and 2085..

#### Gateway Tracing

The gateway has a trace feature for testing and debugging purposes.

The trace feature collects information about the gateway running environment, MQI calls, and parameter values of the MQI calls. The amount of trace data to collect is based on the tracing level selected with the `TRACE_LEVEL` parameter.

**Note:**

Do not enable tracing when your application is running in a production environment because it reduces gateway performance.

The trace data is written to the directory and file specified by the `LOG_DESTINATION` parameter.

**Related Topics**

- [Oracle Database Gateway for WebSphere MQ Initialization Parameters](database-gateway-webspheremq-initialization-parameters.md)

##### LOG_DESTINATION Parameter

This is a gateway initialization parameter.

###### Gateway

 SQL-based and procedural

###### Default Value

 The default value is `SID_agt_PID.trc`.

###### Range of Values

None

###### Syntax

 `LOG_DESTINATION = ``log_file`

##### Parameter Description

    LOG_DESTINATION = log_file

`LOG_DESTINATION` specifies the file name or directory where the gateway writes logging information. When `log_file` already exists, logging information is written to the end of file.

If you do not specify `LOG_DESTINATION`, then the default log file is created each time that the gateway starts up.

#### Verifying Gateway Operation

If your application cannot connect to the gateway, then rerun the application with the gateway trace feature enabled.

If no trace information is written to the log file specified by `LOG_DESTINATION`, or if the log file is not created at all, then verify that:

- The Oracle Net configuration for the gateway and the Oracle database is set up properly.

- A database link exists between the Oracle database and the gateway was created.

If the Oracle Net configuration and database link are set up correctly, then check the operation of the gateway with the `test.sql` script:

1.  Change directory to the gateway sample directory by entering:

    For Microsoft Windows:

        > cd %ORACLE_HOME%\dg4mq\sample

    For UNIX based systems:

        $ cd $ORACLE_HOME/dg4mq/sample

2.  Using an editor, modify the `test.sql` script as follows:

    1.  Specify the database link name that you created for the gateway. To do this, replace the characters `@dg4mq` with `@``dblink`, where `dblink` is the name you chose when the database link was created.

    2.  Replace the characters `YOUR_QUEUE_NAME` with a valid WebSphere MQ queue name.

3.  Using SQL\*Plus, connect to your Oracle database as a valid user.

4.  Run `test.sql`, a script that sends and retrieves a message from a WebSphere MQ queue. A successful completion displays the following output:

        SQL> @test.sql
        message put on queue = 10203040506070809000
        MQPUT: CorrelId length = 24
        MQPUT: MsgId length = 24
        MQPUT returned with reason code 0
        MQGET returned with reason code 0
        message read back = 10203040506070809000

    An unsuccessful test displays the following output:

        SQL> @test.sql
        message put on queue = 10203040506070809000
        Error: Oracle Database Gateway for WebSphere MQ verification script failed.
        ORA-29400: data cartridge error
        MQI MQOPEN failed. completion code=2, reason code=2085

**Related Topics**

- [Configuring Oracle Net for the Gateway](configuring-database-gateway-webspheremq.md)
- [Administering the Database Links Alias Library](configuring-database-gateway-webspheremq.md)
