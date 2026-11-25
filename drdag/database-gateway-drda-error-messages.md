The following sections provide information about error messages and error codes specific to the Oracle Database Gateway for DRDA:

- Interpreting Gateway Error Messages

- Mapped Errors

- SQL Tracing and the Gateway

### Interpreting Gateway Error Messages

The gateway architecture consists of different components. Any component may detect and report an error condition while processing SQL statements that refer to one or more DRDA database tables. This means that errors can be complex, involving error codes and supporting data from multiple components. In all cases, however, the application ultimately receives a single error code or a return code.

As most gateway messages exceed the 70 character message area in the Oracle SQL Communications Area (SQLCA), the programmatic interfaces and Oracle Call Interfaces, that you use to access data through the gateway should use SQLGLM or OERHMS to view the entire text of messages. Refer to the programmer's guide to the Oracle precompilers for additional information about SQLGLM, and refer to the [Oracle C++ Call Interface Programmer's Guide](../lncpp/index.md) for additional information about OERHMS.

Errors encountered when using the gateway can originate from many sources, as follows:

- Errors detected by the Oracle database

- Errors detected by the gateway

- Errors detected in the DRDA software, either on the client or server side

- Communication errors

- Errors detected by the server database

#### Errors Detected by the Gateway

Errors detected by the Oracle database are reported back to the application or tool with the standard `ORA` type message. Refer to [Oracle Database Error Messages](../errmg/index.md) for descriptions of these errors. For example, the following error occurs when an undefined database link name is specified:

    ORA-02019:  connection description for remote database not found

Errors in the `ORA-9100` to `ORA-9199` range are reserved for the generic gateway layer (components of the gateway that are not specific to DRDA). Messages in this range are documented in [Oracle Database Error Messages](../errmg/index.md).

#### Errors Detected in the DRDA Software

Errors detected in the DRDA gateway, on the client or server side, are usually reported with error `ORA-28500`, followed by a gateway-specific expanded error message. There are two return codes reported in the expanded message:

- `drc` specifies DRDA-specific errors.

- `grc` specifies generic gateway errors detected in the DRDA layer. These errors are documented in the [Oracle Database Error Messages](../errmg/index.md).

**Note:**

Error code `ORA‐28500 `was error code `ORA‐09100` prior to gateway version 8. Error code` ORA‐28501` was listed as `ORA‐09101` prior to gateway version 8.

The values in parentheses that follow the `drc` values are used for debugging by Oracle Support Services. The` errp `field indicates the program (client or server) that detected the error. If present,` errmc `lists any error tokens.

For example, the following error message is returned when the database name specified with the `DRDA_REMOTE_NAME` parameter in the i`nitsid.ora` file is not defined at the DRDA server:

    ORA-28500: connection from ORACLE to non-Oracle system returned the message:

#### Errors Detected by the DRDA Server

Errors detected by the DRDA server are reported with an `ORA-28500` followed by a gateway-specific expanded error message. Refer to IBM documentation for the specific database being used. Also refer to Mapped Errorsfor some SQL errors that get translated.

**Note:**

Error code `ORA‐28500` was error code` ORA‐09100` prior to gateway version 8. Error code `ORA‐28501` was listed as `ORA‐09101` prior to gateway version 8.

For example, the following error message indicates that the DRDA server did not find the DB2 database name specified in the `HS_FDS_CONNECT_INFO` parameter in the `initSID.ora` file:

    ORA-28500: connection from ORACLE to a non-Oracle system returned this message:
    [Oracle][ODBC DB2 Wire Protocol driver]Remote Database Not Found: UNKNOWN

### Mapped Errors

Some SQL errors are returned from the DRDA server and are translated to an Oracle error code. This is needed when the Oracle instance or gateway provides special handling of an error condition.

The following is an example of a translated object does not exist error:

    ORA-00942: table or view does not exist
    [Oracle][ODBC DB2 Wire Protocol driver][UDB DB2 for OS/390 and z/OS]PCASTRO.XXX IS AN UNDEFINED NAME.

### SQL Tracing and the Gateway

When developing applications, it is often useful to be able to see the exact SQL statements that are being passed through the gateway. The following sections describe setting appropriate trace parameters and setting up the debug gateway.

#### SQL Tracing in the Oracle Database

Oracle database has a command for capturing the SQL statement that is actually sent to the gateway. This command is called `EXPLAIN PLAN`. The `EXPLAIN PLAN` command is used to determine the execution plan that Oracle database follows to execute a specified SQL statement. This command inserts a row, which describes each step of the execution plan, into a specified table. If you are using cost-based optimization, then this command also determines the cost of executing the statement. The syntax of the command is:

    EXPLAIN PLAN [ SET STATEMENT_ID = 'text' ]
        [ INTO [schema.]table[@dblink] ] FOR statement

For detailed information on this command, refer to the [Oracle Database SQL Language Reference](../sqlrf/EXPLAIN-PLAN.md).

**Note:**

In most cases, `EXPLAIN PLAN` should be sufficient to extract the SQL statement that is actually sent to the gateway, and thus sent to the DRDA server. However, certain SQL statement form have post-processing performed on them in the gateway.
