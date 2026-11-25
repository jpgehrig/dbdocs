The Oracle Database Gateway for WebSphere MQ has its own initialization parameters, which are described in this the following topics, and supports the initialization parameters for Oracle Database Gateways.

### Gateway Initialization File

The gateway initialization file is called `init``sid`.`ora`.

A default initialization file is created in the directory `ORACLE_HOME``\dg4mq\admin` on Microsoft Windows and `ORACLE_HOME``/dg4mq/admin` on UNIX based systems during the installation of the Oracle Database Gateway for WebSphere MQ.

### Gateway Parameters

These topics describe gateway parameters, listing the default value, range of values, and the syntax for usage.

#### LOG_DESTINATION

The following table describes the `LOG_DESTINATION` parameter:

| LOG_DESTINATION | Use                                                      |
|:----------------|:---------------------------------------------------------|
| Syntax          | `LOG_DESTINATION =` `log_file`                           |
| Default value   | `SID_agt_PID.trc` (PID is the process ID of the gateway) |
| Range of values | None                                                     |

`LOG_DESTINATION` specifies the full path name of the gateway log file.

#### AUTHORIZATION_MODEL

The following table describes how to use the `AUTHORIZATION_MODEL` parameter:

| AUTHORIZATION_MODEL | Use                                      |
|:--------------------|:-----------------------------------------|
| Syntax              | `AUTHORIZATION_MODEL = {RELAXED|STRICT}` |
| Default value       | `RELAXED`                                |
| Range of values     | `RELAXED` or `STRICT`                    |

`AUTHORIZATION_MODEL` defines the authorization model for the gateway user. The relaxed model specifies that authorizations that are granted to the effective user ID of the gateway by the queue manager are the only associations that an Oracle application has.

The strict model specifies that the Oracle user ID and password (that are provided when a database link is created), or the current user ID and password (when the Oracle user ID and password are not provided), should be checked against the local or network password file.

Refer to "[Security Models](database-gateway-webspheremq-running-environment.md)" for more information about effective user IDs.

#### QUEUE_MANAGER

The following table describes the `QUEUE_MANAGER` parameter:

| QUEUE_MANAGER   | Use                              |
|:----------------|:---------------------------------|
| Syntax          | `QUEUE_MANAGER =` `manager_name` |
| Default value   | None                             |
| Range of values | None                             |

`QUEUE_MANAGER`, a required parameter, specifies the name of the queue manager that the gateway connects to at logon time. The effective user ID of the gateway should have the correct user privileges or should be authorized to connect to this queue manager. Specify `manager_name` using the following rules:

- 1 to 48 alphanumeric characters in length

- No leading or embedded blank characters

- Trailing blank characters are permitted

Refer to "[Security Models](database-gateway-webspheremq-running-environment.md)" for more information about effective user IDs.

#### TRACE_LEVEL

The following table describes the `TRACE_LEVEL` parameter:

| TRACE_LEVEL     | Use                     |
|:----------------|:------------------------|
| Syntax          | `TRACE_LEVEL =` `level` |
| Default value   | `0`                     |
| Range of values | `0` to 7                |

`TRACE_LEVEL` controls whether tracing information is collected as the gateway runs. When set to collect information, the trace data is written to the log file that is specified by the `LOG_DESTINATION` parameter. Specify `level` as an integer from `0` to `3`, which is the sum of the desired trace values. The following table describes the significance of these values:

| Trace Level | Description                                                                                                                                                                                                              |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0           | Specifies that no tracing is to be done.                                                                                                                                                                                 |
| 1           | Specifies that general tracing is to be done. This includes the user ID that is used to log on to the WebSphere MQ queue manager, the name of the queue manager, the gateway transaction mode, security mode, and so on. |
| 2           | Specifies that tracing is to be done for all MQI calls that are issued by the gateway.                                                                                                                                   |
| 3           | Specifies that tracing is to be done for all parameter values that are passed to, or received from, the MQI calls that were issued by the gateway.                                                                       |

For more information about MQI calls.

**See Also:**

Refer to IBM publications, for more information about MQI calls.

#### TRANSACTION_LOG_QUEUE

The following table describes how to use `TRANSACTION_LOG_QUEUE`.

| TRANSACTION_LOG_QUEUE | Description                               |
|:----------------------|:------------------------------------------|
| Syntax                | `TRANSACTION_LOG_QUEUE =` `tx_queue_name` |
| Default value         | None                                      |
| Range of values       | None                                      |

`TRANSACTION_LOG_QUEUE` specifies the name of the queue for logging transaction IDs. Specify `tx_queue_name` using the following rules:

- 1 to 48 alphanumeric characters in length

- No leading or embedded blank characters

- Trailing blank characters are permitted

Refer to "[Creating a Transaction Log Queue](configuring-database-gateway-webspheremq.md)" for more information.

#### TRANSACTION_MODEL

The following table describes how to use `TRANSACTION_MODEL`.

| TRANSACTION_MODEL | Description                                             |
|:------------------|:--------------------------------------------------------|
| Syntax            | `TRANSACTION_MODEL` = {`COMMIT_CONFIRM`\|`SINGLE_SITE`} |
| Default value     | `SINGLE_SITE`                                           |
| Range of values   | `COMMIT_CONFIRM` or `SINGLE_SITE`                       |

`TRANSACTION_MODEL` defines the transaction mode of the gateway. Specify a value for `TRANSACTION_MODEL` as described in the following table:

| Item             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `COMMIT_CONFIRM` | Specifies that the gateway can participate in transactions when queues belonging to the same WebSphere queue manager are updated. At the same time, any number of Oracle databases are updated. Only one gateway with the commit-confirm model can join the distributed transaction, because the gateway operates as the focal point of the transaction.<br>When this value is specified, you must also set the `RECOVERY_USER`, `RECOVERY_PASSWORD`, and `TRANSACTION_LOG_QUEUE` parameters. |
| `SINGLE_SITE`    | Specifies that the gateway can participate in a transaction only when queues belonging to the same WebSphere queue manager are updated. An Oracle application can select, but not update, data at any Oracle database within the same transaction that accesses WebSphere MQ.                                                                                                                                                                                                                 |

#### TRANSACTION_RECOVERY_PASSWORD

The following table describes `TRANSACTION_RECOVERY_PASSWORD`.

| TRANSACTION_RECOVERY_PASSWORD | Description                                                                                   |
|:------------------------------|:----------------------------------------------------------------------------------------------|
| Default value                 | `*`                                                                                           |
| Range of values               | An asterisk (\*), which indicates that the parameter must be encrypted, or any valid password |
| Syntax                        | `TRANSACTION_RECOVERY_PASSWORD = rec_password`<br>or<br>`TRANSACTION_RECOVERY_PASSWORD = *`   |

`TRANSACTION_RECOVERY_PASSWORD` specifies the password of the user that the gateway uses to start recovery of a transaction. The default value is set to an asterisk (\*), and this asterisk indicates that the value of this parameter is stored in an encrypted form in a separate password file. To specify or change a valid password for encrypted gateway parameters, you need to use the `dg4pwd` gateway utility to do the work. For more information, refer to "Using the dg4pwd Utility".

The `TRANSACTION_RECOVERY_PASSWORD` parameter is required only when `TRANSACTION_MODEL` is set to `COMMIT_CONFIRM`. Refer to "[Creating a Transaction Log Queue](configuring-database-gateway-webspheremq.md)" for more information.

##### Passwords in the Gateway Initialization File

The gateway uses user IDs and passwords to access information in the remote database on the WebSphere MQ server. Some user IDs and passwords must be defined in the gateway initialization file to handle functions such as resource recovery. In a security-conscious environment, plain-text passwords are regarded as insecure when they are accessible in the initialization file. A new encryption feature has been added to the gateway to make such passwords more secure. The `dg4pwd` utility can be used to encrypt passwords that would normally be stored in the gateway initialization file. Using this feature is optional, but highly recommended by Oracle. With this feature, passwords are no longer stored in the initialization file but are stored in a password file in an encrypted form. This makes the password information more secure.

##### Using the dg4pwd Utility

The `dg4pwd` utility is used to encrypt passwords that would normally be stored in the gateway initialization file. The utility works by reading the initialization file and looks for parameters with a special value. The value is the asterisk (`*`). The asterisk indicates that the value of this parameter is stored in an encrypted form in another file. The following sample is a section of the initialization file with this value.

##### TRANSACTION_RECOVERY_PASSWORD=\*

The initialization file is first edited to set the value of the parameter to the asterisk (`*`). Then the `dg4pwd` utility is run, specifying the gateway SID on the command line. The utility reads the initialization file and prompts the user to enter the values to be encrypted.

The syntax of this command is:

    dg4pwd gateway_sid

In this command, `gateway_sid` is the SID of the gateway.

The following is an example, assuming that the gateway SID is `dg4mqs`:

    % dg4pwd dg4mqs
    ORACLE Gateway Password Utility (dg4mqseries) Constructing password file for
    Gateway SID dg4mqs
    Enter the value for TRANSACTION_RECOVERY_PASSWORD
    welcome
    %

In this example, the `TRANSACTION_RECOVERY_PASSWORD` parameter is identified as requiring encryption. The user enters the value (for example, `welcome`) and presses the Enter key. If more parameters require encryption, then you are prompted for their values. The encrypted data is stored in the `dg4mq\admin` directory on Microsoft Windows and `dg4mq/admin` directory on UNIX based systems.

**Note:**

It is important that the `ORACLE_HOME` environment variable specifies the correct gateway home to ensure that the correct gateway initialization file is read.

#### TRANSACTION_RECOVERY_USER

The following table describes how to use the `TRANSACTION_RECOVERY_USER` parameter:

| Item            | Description                                                                         |
|:----------------|:------------------------------------------------------------------------------------|
| Syntax          | `TRANSACTION_RECOVERY_USER =` `rec_user`                                            |
| Default value   | None.                                                                               |
| Range of values | Any valid operating system user ID that is authorized by WebSphere MQ Manager (MQM) |

`TRANSACTION_RECOVERY_USER` specifies the user name that the gateway uses to start the recovery of a transaction. This parameter is required only when `AUTHORIZATION_MODEL` is set to `STRICT`, and `TRANSACTION_MODEL` is set to `COMMIT_CONFIRM`. Refer to "[Creating a Transaction Log Queue](configuring-database-gateway-webspheremq.md)" for more information.
