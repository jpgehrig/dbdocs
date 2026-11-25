Configure the gateway using initialization parameters.

This is done by creating an initialization file and setting the desired parameters in this file.

Heterogeneous Services initialization parameters are distinct from Oracle Database initialization parameters. Heterogeneous Services initialization parameters are set in the Heterogeneous Services initialization file and not in the Oracle database initialization parameter file (`init.ora` file). There is a Heterogeneous Services initialization file for each gateway instance.

- Encrypting Initialization Parameters
  An encryption feature has been added to Heterogeneous Services making it possible to encrypt parameter values.
- Gateway Initialization Parameters
  Generic initialization parameters that are common to all gateways.

**Related Topics**

- [Heterogeneous Services Configuration Information](heterogeneous-services-configuration-information.md)

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)

### Encrypting Initialization Parameters

An encryption feature has been added to Heterogeneous Services making it possible to encrypt parameter values.

Initialization parameters may contain sensitive information, such as user IDs or passwords. Initialization parameters are stored in plain text files and are insecure. An encryption feature has been added to Heterogeneous Services making it possible to encrypt parameter values. This is done through the `dg4pwd` utility. To use this feature requires setting the value of a parameter in the initialization file to an unquoted asterisk (\*). For example:

    HD_FDS_CONNECT_INFO = *

With the value set to this security marker, all Heterogeneous Services agents know that the real value will be stored in a related, encrypted password file. The name of this file is `init``sid``.pwd`, where `sid` is the Oracle system identifier used for the gateway. This file is created by the `dg4pwd` utility in the current directory containing the initialization file. Running the `dg4pwd` utility prompts for the real value of the parameter, which the utility encrypts and stores in the password file. The encrypted initialization parameters are implicitly treated as `PRIVATE` parameters and are not uploaded to the server.

- Using the dg4pwd Utility
  The `dg4pwd` utility is used to encrypt initialization parameters that would normally be stored in the initialization parameter file in plain text.

**Parent topic:** Initialization Parameters

#### Using the dg4pwd Utility

The `dg4pwd` utility is used to encrypt initialization parameters that would normally be stored in the initialization parameter file in plain text.

The utility works by reading the initialization parameter file in the current directory and looking for parameters having a security marker for the value. The security marker is an unquoted asterisk (\*). This designates that the value of this parameter is to be stored in an encrypted form in a password file. The following is an example of an initialization parameter set to this value:

    HS_FDS_CONNECT_INFO = *

To encrypt the `HS_FDS_CONNECT_INFO` initialization parameter, take the following steps:

1.  Edit the `HS_FDS_CONNECT_INFO` initialization parameter file in the current directory to set the value to an unquoted asterisk (\*) security marker.

2.  Run the `dg4pwd` utility, specifying the gateway SID on the command line, with an optional user ID to designate a different owner of the encrypted information.

3.  The `dg4pwd` utility reads the initialization parameter file and prompts you to enter the real values that are to be encrypted.

The syntax of the command is as follows:

    dg4pwd [sid] {userid}

In the syntax example above, `[``sid``]` is the `SID` of the gateway and `{``userid``}` is an optional user ID used to encrypt the contents. If no user ID is specified, then the current user's ID is used. Values are encrypted using this ID. In order to decrypt the values, the agent must be run as that user. The following example assumes a gateway SID of SYBASE:

    dg4pwd SYBASE
    ORACLE Gateway Password Utility
    Constructing password file for Gateway SID SYBASE
    Enter the value for HS_FDS_CONNECT_INFO
    SYBASE_password

In the previous example, the initialization parameter file, `initSYBASE.ora`, is read. The parameter, `HS_FDS_CONNECT_INFO`, is identified as requiring encryption. Enter the value (for example, `SYBASE_password`) and presses enter. If more parameters require encryption, the utility prompts for those passwords in turn. The encrypted data is stored in the same directory as the initialization file. Any initialization parameters needing encryption should be encrypted before using the Oracle Database gateway.

**Parent topic:** Encrypting Initialization Parameters

### Gateway Initialization Parameters

Generic initialization parameters that are common to all gateways.

Gateway initialization parameters can be divided into two groups. One is a set of generic initialization parameters that are common to all gateways and the other is a set of initialization parameters that are specific to individual gateways. The following generic initialization parameters are the only initialization parameters discussed in this document:

- `HS_BULK`
- `HS_CALL_NAME`
- `HS_COMMIT_POINT_STRENGTH`
- `HS_DB_DOMAIN`
- `HS_DB_INTERNAL_NAME`
- `HS_DB_NAME`
- `HS_DESCRIBE_CACHE_HWM`
- `HS_FDS_ARRAY_EXEC`
- `HS_FDS_CONNECT_INFO`
- `HS_FDS_DEFAULT_SCHEMA_NAME`
- `HS_FDS_SHAREABLE_NAME`
- `HS_FDS_TRACE_LEVEL`
- `HS_LANGUAGE`
- `HS_LONG_PIECE_TRANSFER_SIZE`
- `HS_NLS_DATE_FORMAT`
- `HS_NLS_DATE_LANGUAGE`
- `HS_NLS_NCHAR`
- `HS_NLS_NUMERIC_CHARACTERS`
- `HS_NLS_TIMESTAMP_FORMAT`
- `HS_NLS_TIMESTAMP_TZ_FORMAT`
- `HS_OPEN_CURSORS`
- `HS_ROWID_CACHE_SIZE`
- `HS_RPC_FETCH_REBLOCKING`
- `HS_RPC_FETCH_SIZE`
- `HS_TIME_ZONE`

Do not use the `PRIVATE` keyword when setting any of these parameters. Using the `PRIVATE` keyword prevents the parameter from being uploaded to the server and can cause errors in SQL processing. Do not set these parameters as environment variables using the `SET` command.

**See Also:**

Individual gateway documentation for the list of initialization parameters specific to a gateway

**Parent topic:** Initialization Parameters
