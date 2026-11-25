The Oracle database initialization parameters in the `init.ora` file are distinct from gateway initialization parameters. Set the gateway parameters in the initialization parameter file using an agent-specific mechanism, or set them in the Oracle data dictionary using the `DBMS_HS` package. The gateway initialization parameter file must be available when the gateway is started. Changes made to the initialization parameters only take effect in the next gateway session.

The following sections contain a list of the gateway initialization parameters that can be set for each gateway and their description. It also describes the initialization parameter file syntax.

- Initialization Parameter File Syntax

- Oracle Database Gateway for DRDA Initialization Parameters

### Initialization Parameter File Syntax

The syntax for the initialization parameter file is as follows:

- The file is a sequence of commands.

- Each command should start on a separate line.

- End of line is considered a command terminator (unless escaped with a backslash).

- If there is a syntax error in an initialization parameter file, none of the settings take effect.

- Set the parameter values as follows:

      [SET][PRIVATE] parameter=value

  Where:

  `parameter` is an initialization parameter name. It is a string of characters starting with a letter and consisting of letters, digits and underscores. Initialization parameter names are case sensitive.

  `value` is the initialization parameter value. It is case-sensitive. An initialization parameter value is either:

  1.  A string of characters that does not contain any backslashes, white space or double quotation marks (")

  2.  A quoted string beginning with a double quotation mark and ending with a double quotation mark. The following can be used inside a quoted string:

      - backslash (\\ is the escape character

      - \n inserts a new line

      - \t inserts a tab

      - \\ inserts a double quotation mark

      - \\ inserts a backslash

      A backslash at the end of the line continues the string on the next line. If a backslash precedes any other character then the backslash is ignored.

  For example, to enable tracing for an agent, set the `HS_FDS_TRACE_LEVEL` initialization parameter as follows:

      HS_FDS_TRACE_LEVEL=ON

  `SET` and `PRIVATE` are optional keywords. You cannot use either as an initialization parameter name. Most parameters are needed only as initialization parameters, so you usually do not need to use the `SET` or `PRIVATE` keywords. If you do not specify either `SET` or `PRIVATE`, the parameter is used only as an initialization parameter for the agent.

  `SET` specifies that, in addition to being used as an initialization parameter, the parameter value is set as an environment variable for the agent process. Use `SET` for parameter values that the drivers or non-Oracle system need as environment variables.

  `PRIVATE` specifies that the initialization parameter should be private to the agent and should not be uploaded to the Oracle database. Most initialization parameters should not be private. If, however, you are storing sensitive information like a password in the initialization parameter file, then you may not want it uploaded to the server because the initialization parameters and values are not encrypted when uploaded. Making the initialization parameters private prevents the upload from happening and they do not appear in dynamic performance views. Use `PRIVATE` for the initialization parameters only if the parameter value includes sensitive information such as a username or password.

  `SET PRIVATE` specifies that the parameter value is set as an environment variable for the agent process and is also private (not transferred to the Oracle database, not appearing in dynamic performance views or graphical user interfaces).

### Oracle Database Gateway for DRDA Initialization Parameters

This section lists all the initialization file parameters that can be set for the Oracle Database Gateway for DRDA. They are as follows:

- HS_CALL_NAME

- HS_DB_DOMAIN

- HS_DB_INTERNAL_NAME

- HS_DB_NAME

- HS_DESCRIBE_CACHE_HWM

- HS_LANGUAGE

- HS_LONG_PIECE_TRANSFER_SIZE

- HS_OPEN_CURSORS

- HS_RPC_FETCH_REBLOCKING

- HS_RPC_FETCH_SIZE

- HS_TRANSACTION_MODEL

- IFILE

- HS_FDS_CONNECT_INFO

- HS_FDS_RECOVERY_ACCOUNT

- HS_FDS_RECOVERY_PWD

- HS_FDS_FETCH_ROWS

- HS_FDS_TRACE_LEVEL

- HS_FDS_TRANSACTION_LOG

- HS_IDLE_TIMEOUT

- HS_FDS_MBCS_TO_GRAPHIC

- HS_FDS_GRAPHIC_TO_MBCS

- HS_FDS_TIMESTAMP_MAPPING

- HS_FDS_DATE_MAPPING

- HS_FDS_QUOTE_IDENTIFIER

- HS_FDS_CAPABILITY

- HS_FDS_ISOLATION_LEVEL

- HS_FDS_PACKAGE_COLLID

- HS_NLS_LENGTH_SEMANTICS

- HS_KEEP_REMOTE_COLUMN_SIZE

- HS_FDS_RESULTSET_SUPPORT

- HS_FDS_REMOTE_DB_CHARSET

- HS_FDS_SUPPORT_STATISTICS

- HS_FDS_RSET_RETURN_ROWCOUNT

- HS_FDS_AUTHENTICATE_USER

- HS_FDS_ENCRYPT_SESSION

- HS_FDS_VALIDATE_SERVER_CERT

- HS_FDS_TRUSTSTORE_FILE

- HS_FDS_TRUSTSTORE_PASSWORD

- HS_FDS_SQLLEN_INTERPRETATION

- HS_FDS_ARRAY_EXEC

### HS_CALL_NAME

| Property        | Description    |
|:----------------|:---------------|
| Default value   | None           |
| Range of values | Not applicable |

Specifies the remote functions that can be referenced in SQL statements. The value is a list of remote functions and their owners, separated by semicolons, in the following format:

    [owner_name.]function_name


For example:

    owner1.A1;owner2.A2;A3

If an owner name is not specified for a remote function, the default owner name becomes the user name used to connect to the remote database (specified when the Heterogeneous Services database link is created or taken from user session if not specified in the DB link).

The entries for the owner names and the function names are case-sensitive.

### HS_DB_DOMAIN

| Property        | Description         |
|:----------------|:--------------------|
| Default value   | `WORLD`             |
| Range of values | 1 to 199 characters |

Specifies a unique network sub-address for a non-Oracle system. The `HS_DB_DOMAIN` initialization parameter is similar to the `DB_DOMAIN` initialization parameter, described in the [Oracle Database Reference](../refrn/PARALLEL_MIN_PERCENT.md). The `HS_DB_DOMAIN` initialization parameter is required if you use the Oracle Names server. The `HS_DB_NAME` and `HS_DB_DOMAIN` initialization parameters define the global name of the non-Oracle system.

**Note:**

The `HS_DB_NAME` and `HS_DB_DOMAIN` initialization parameters must combine to form a unique address in a cooperative server environment.

### HS_DB_INTERNAL_NAME

| Property        | Description                    |
|:----------------|:-------------------------------|
| Default value   | `01010101`                     |
| Range of values | 1 to 16 hexadecimal characters |

Specifies a unique hexadecimal number identifying the instance to which the Heterogeneous Services agent is connected. This parameter's value is used as part of a transaction ID when global name services are activated. Specifying a nonunique number can cause problems when two-phase commit recovery actions are necessary for a transaction.

### HS_DB_NAME

| Property        | Description       |
|:----------------|:------------------|
| Default value   | `HO`              |
| Range of values | 1 to 8 characters |

Specifies a unique alphanumeric name for the data store given to the non-Oracle system. This name identifies the non-Oracle system within the cooperative server environment. The `HS_DB_NAME` and `HS_DB_DOMAIN` initialization parameters define the global name of the non-Oracle system.

### HS_DESCRIBE_CACHE_HWM

| Property        | Description   |
|:----------------|:--------------|
| Default value   | `100`         |
| Range of values | `1` to `4000` |

Specifies the maximum number of entries in the describe cache used by Heterogeneous Services. This limit is known as the describe cache high water mark. The cache contains descriptions of the mapped tables that Heterogeneous Services reuses so that it does not have to re-access the non-Oracle data store.

If you are accessing many mapped tables, increase the high water mark to improve performance. Increasing the high water mark improves performance at the cost of memory usage.

### HS_LANGUAGE

| Property        | Description                                    |
|:----------------|:-----------------------------------------------|
| Default value   | System-specific                                |
| Range of values | Any valid language name (up to 255 characters) |

Provides Heterogeneous Services with character set, language, and territory information of the non-Oracle data source. The value must use the following format:

    language[_territory.character_set]

**Note:**

The globalization support initialization parameters affect error messages, the data for the SQL Service, and parameters in distributed external procedures.

#### Character Sets

Ideally, the character sets of the Oracle database and the non-Oracle data source are the same. In almost all cases, `HS_LANGUAGE` should be set exactly the same as Oracle database character set for optimal character set mapping and performance. If they are not the same, Heterogeneous Services attempts to translate the character set of the non-Oracle data source to the Oracle database character set, and back again. The translation can degrade performance. In some cases, Heterogeneous Services cannot translate a character from one character set to another.

**Note:**

The specified character set must be a superset of the operating system character set on the platform where the agent is installed.

As more Oracle databases and non-Oracle databases use Unicode as database character sets, it is preferable to also run the gateway in Unicode character set. To do so, you must set `HS_LANGUAGE=AL32UTF8`. However, when the gateway runs on Windows, the Microsoft ODBC Driver Manager interface can exchange data only in the double-byte character set, UCS2. This results in extra ratio expansion of described buffer and column sizes. Refer to HS_FDS_REMOTE_DB_CHARSET for instruction on how to adjust to correct sizes.

#### Language

The language component of the `HS_LANGUAGE` initialization parameter determines:

- Day and month names of dates

- AD, BC, PM, and AM symbols for date and time

- Default sorting mechanism

Note that Oracle does not determine the language for error messages for the generic Heterogeneous Services messages (`ORA-25000` through `ORA-28000`). These are controlled by the session settings in the Oracle database.

#### Territory

The territory clause specifies the conventions for day and week numbering, default date format, decimal character and group separator, and ISO and local currency symbols. Note that the level of globalization support between the Oracle database and the non-Oracle data source depends on how the gateway is implemented.

### HS_LONG_PIECE_TRANSFER_SIZE

| Property        | Description          |
|:----------------|:---------------------|
| Default value   | 64 KB                |
| Range of values | Any value up to 2 GB |

Sets the size of the piece of `LONG` data being transferred. A smaller piece size means less memory requirement, but more round-trips to fetch all the data. A larger piece size means fewer round-trips, but more of a memory requirement to store the intermediate pieces internally. Thus, the initialization parameter can be used to tune a system for the best performance, with the best trade-off between round-trips and memory requirements, and network latency or response time.

### HS_OPEN_CURSORS

| Property        | Description                                                                    |
|:----------------|:-------------------------------------------------------------------------------|
| Default value   | `50`                                                                           |
| Range of values | `1` to the value of `OPEN_CURSORS` initialization parameter of Oracle database |

Defines the maximum number of cursors that can be open on one connection to a non-Oracle system instance.

The value never exceeds the number of open cursors in the Oracle database. Therefore, setting the same value as the `OPEN_CURSORS` initialization parameter in the Oracle database is recommended.

### HS_RPC_FETCH_REBLOCKING

| Property        | Description   |
|:----------------|:--------------|
| Default value   | `ON`          |
| Range of values | `OFF` or `ON` |

Controls whether Heterogeneous Services attempts to optimize performance of data transfer between the Oracle database and the Heterogeneous Services agent connected to the non-Oracle data store.

The following values are possible:

- `OFF` disables reblocking of fetched data so that data is immediately sent from agent to server.

- `ON` enables reblocking, which means that data fetched from the non-Oracle system is buffered in the agent and is not sent to the Oracle database until the amount of fetched data is equal or higher than the value of `HS_RPC_FETCH_SIZE` initialization parameter. However, any buffered data is returned immediately when a fetch indicates that no more data exists or when the non-Oracle system reports an error.

### HS_RPC_FETCH_SIZE

| Property        | Description   |
|:----------------|:--------------|
| Default value   | `50000`       |
| Range of values | 1 to 10000000 |

Tunes internal data buffering to optimize the data transfer rate between the server and the agent process.

Increasing the value can reduce the number of network round-trips needed to transfer a given amount of data, but also tends to increase data bandwidth and to reduce latency as measured between issuing a query and completion of all fetches for the query. Nevertheless, increasing the fetch size can increase latency for the initial fetch results of a query, because the first fetch results are not transmitted until additional data is available.

### HS_TRANSACTION_MODEL

| Property        | Description                                                                                    |
|:----------------|:-----------------------------------------------------------------------------------------------|
| Default Value   | `COMMIT_CONFIRM`                                                                               |
| Range of Values | `COMMIT_CONFIRM`, `READ_ONLY`, `READ_ONLY_AUTOCOMMIT`, `SINGLE_SITE`, `SINGLE_SITE_AUTOCOMMIT` |

Specifies the type of transaction model that is used when the non-Oracle database is updated by a transaction.

The following values are possible:

- `COMMIT_CONFIRM` provides read and write access to the non-Oracle database and allows the gateway to be part of a distributed update. To use the commit-confirm model, the following items must be created in the non-Oracle database:

  - Transaction log table. The default table name is `HS_TRANSACTION_LOG`. A different name can be set using the `HS_FDS_TRANSACTION_LOG` parameter. The transaction log table must be granted `SELECT`, `DELETE`, and `INSERT` privileges set to public.

  - Recovery account. The account name is assigned with the `HS_FDS_RECOVERY_ACCOUNT` parameter.

  - Recovery account password. The password is assigned with the `HS_FDS_RECOVERY_PWD` parameter.

    `COMMIT_CONFIRM` does not apply to Oracle Database Gateway for ODBC. The default value for Oracle Database Gateway for ODBC is `SINGLE_SITE`.

- `READ_ONLY` provides read access to the non-Oracle database.

- `READ_ONLY_AUTOCOMMIT` provides read access to the non-Oracle database that do not have logging.

- `SINGLE_SITE` provides read and write access to the non-Oracle database. However, the gateway cannot participate in distributed updates.

- `SINGLE_SITE_AUTOCOMMIT` provides read and write access to the non-Oracle database that do not have logging. Any update is committed immediately, and the gateway cannot participate in distributed updates.

### IFILE

| Property        | Description                |
|:----------------|:---------------------------|
| Default value   | None                       |
| Range of values | Valid parameter file names |

Use the `IFILE` initialization parameter to embed another initialization file within the current initialization file. The value should be an absolute path and should not contain environment variables. The three levels of nesting limit do not apply.

**See Also:**

[Oracle Database Reference](../refrn/IFILE.md)

### HS_FDS_CONNECT_INFO

| Property        | Description    |
|:----------------|:---------------|
| Default Value   | None           |
| Range of Values | Not applicable |

`HS_FDS_CONNECT_INFO` that describes the connection to the non-Oracle system.

The default initialization parameter file already has an entry for this parameter. The syntax for `HS_FDS_CONNECT_INFO` for the gateways are as follows:

    HS_FDS_CONNECT_INFO=IP_address:Port_number/Database_name,Type

Where `IP_address` is the hostname or IP address of the DB2 DRDA server

`Port_number` is the port number of the DB2 DRDA server.

`Database_name` is the database name of the DB2 server

`Type` (case insensitive) is one of the following:

- ZOS (DB2 UDB for z/OS),

- IOS (DB2 UDB for iSeries), or

- LUW (DB2 UDB for Linux, Unix, or Windows)

This release of gateway can support IPv6. If IPv6 address format is to be specified, you would need to wrap square brackets around the IPv6 specification to indicate the separation from the port number.

For example,

    HS_FDS_CONNECT_INFO=[2001:0db8:20C:F1FF:FEC6:38AF]:1300/DB2M,ZOS

### HS_FDS_RECOVERY_ACCOUNT

| Property        | Description       |
|:----------------|:------------------|
| Default Value   | `RECOVER`         |
| Range of values | Any valid user ID |

Specifies the name of the recovery account used for the commit-confirm transaction model. An account with user name and password must be set up at the non-Oracle system. For more information about the commit-confirm model, see the `HS_TRANSACTION_MODEL` parameter.

For DRDA, `HS_FDS_RECOVERY_ACCOUNT` specifies the user ID that is used by the gateway if a distributed transaction becomes in doubt. This user ID must have execute privileges on the package and must be defined to the IBM database.

If a distributed transaction becomes in doubt, then the Oracle database determines the status of the transaction by connecting to the IBM database, using the `HS_FDS_RECOVERY_ACCOUNT`. If this parameter is missing, then the gateway attempts to connect to a user ID of `ORARECOV`.

The name of the recovery account is case-sensitive.

### HS_FDS_RECOVERY_PWD

| Property        | Description        |
|:----------------|:-------------------|
| Default Value   | `RECOVER`          |
| Range of values | Any valid password |

Specifies the password of the recovery account used for the commit-confirm transaction model set up at the non-Oracle system. For more information about the commit-confirm model, see the `HS_TRANSACTION_MODEL` parameter.

`HS_FDS_RECOVERY_PWD` is used with the `HS_FDS_RECOVERY_ACCOUNT`. The recovery user connects to the IBM database if a distributed transaction is in doubt.

The name of the password of the recovery account is case-sensitive.

### HS_FDS_FETCH_ROWS

| Property        | Description                        |
|:----------------|:-----------------------------------|
| Default Value   | `100`                              |
| Range of Values | Any integer between `1` and `1000` |
| Syntax          | `HS_FDS_FETCH_ROWS=``num`          |

`HS_FDS_FETCH_ROWS` specifies the fetch array size. This is the number of rows to be fetched from the non-Oracle database and to return to Oracle database at one time. This parameter will be affected by the `HS_RPC_FETCH_SIZE` and `HS_RPC_FETCH_REBLOCKING` parameters.

### HS_FDS_TRACE_LEVEL

| Property        | Description          |
|:----------------|:---------------------|
| Default Value   | `OFF`                |
| Range of values | `OFF`, `ON`, `DEBUG` |

Specifies whether error tracing is turned on or off for gateway connectivity.

The following values are valid:

- `OFF` disables the tracing of error messages.

- `ON` enables the tracing of error messages that occur when you encounter problems. The results are written by default to a gateway log file in LOG directory where the gateway is installed.

- `DEBUG` enables the tracing of detailed error messages that can be used for debugging.

### HS_FDS_TRANSACTION_LOG

| Property        | Description          |
|:----------------|:---------------------|
| Default Value   | `HS_TRANSACTION_LOG` |
| Range of Values | Any valid table name |

Specifies the name of the table created in the non-Oracle system for logging transactions. For more information about the transaction model, see the `HS_TRANSACTION_MODEL` parameter.

### HS_IDLE_TIMEOUT

| Property        | Description             |
|:----------------|:------------------------|
| Default Value   | 0 (no timeout)          |
| Range of Values | 0-9999 (minutes)        |
| Syntax          | `HS_IDLE_TIMEOUT=``num` |

This feature is only available for Oracle Net TCP protocol.

When there is no activity for a connected gateway session for this specified time period, the gateway session would be terminated automatically with pending update (if any) rolled back.

### HS_FDS_MBCS_TO_GRAPHIC

| Property        | Description                             |
|:----------------|:----------------------------------------|
| Default Value   | `FALSE`                                 |
| Range of Values | `FALSE|TRUE`                            |
| Syntax          | `HS_FDS_MBCS_TO_GRAPHIC=``{FALSE|TRUE}` |

If set to `TRUE`, any single-byte character meant to insert to DB2 (var)graphic column would be converted to equivalent double-byte value before the insert operation.

### HS_FDS_GRAPHIC_TO_MBCS

| Property        | Description                             |
|:----------------|:----------------------------------------|
| Default Value   | `FALSE`                                 |
| Range of Values | `FALSE|TRUE`                            |
| Syntax          | `HS_FDS_GRAPHIC_TO_MBCS=``{FALSE|TRUE}` |

If set to `TRUE`, any double-byte characters in DB2 (var)graphic column that can have equivalent single-byte equivalent would be translated to equivalent single-byte before sending to the user.

### HS_FDS_TIMESTAMP_MAPPING

| Property        | Description                                        |
|:----------------|:---------------------------------------------------|
| Default Value   | `CHAR`                                             |
| Range of Values | `CHAR`\|`DATE`\|`TIMESTAMP`                        |
| Syntax          | `HS_FDS_TIMESTAMP_MAPPING={``CHAR|DATE|TIMESTAMP}` |

If set to `CHAR` , then non-Oracle target timestamp would be mapped to `CHAR(26)`. If set to `DATE` (default), then non-Oracle target timestamp would be mapped to Oracle `DATE`. If set to `TIMESTAMP`, then non-Oracle target timestamp would be mapped to Oracle `TIMESTAMP`.

### HS_FDS_DATE_MAPPING

| Property        | Description                         |
|:----------------|:------------------------------------|
| Default Value   | `DATE`                              |
| Range of Values | `DATE`\|`CHAR`                      |
| Syntax          | `HS_FDS_DATE_MAPPING={``DATE|CHAR}` |

If set to `CHAR`, then non-oracle target date would be mapped to `CHAR(10)`. If set to `DATE`, then non-Oracle target date would be mapped to Oracle date.

### HS_FDS_QUOTE_IDENTIFIER

| Property        | Description                              |
|:----------------|:-----------------------------------------|
| Default Value   | `TRUE`                                   |
| Range of Values | `TRUE|FALSE`                             |
| Syntax          | `HS_FDS_QUOTE_IDENTIFIER=``{FALSE|TRUE}` |

By default, the gateway will quote identifiers if the FDS supports it. However, we give the user the ability to overwrite the behavior.

### HS_FDS_CAPABILITY

| Property        | Description                                                              |
|:----------------|:-------------------------------------------------------------------------|
| Default Value   | None                                                                     |
| Range of Values | Refer to [SQL Functions That Can Be Enabled](developing-applications.md) |
| Syntax          | `HS_FDS_CAPABILITY= {``FUNCTION/{ON|OFF|SKIP}``},...`                    |

If the `HS_FDS_CAPABILITY` is set to `ON` then the specified function will be sent to DB2 for processing. In other words, post processing will be not needed for that function.

If the `HS_FDS_CAPABILITY` is set to `OFF` then the specified function will be not be sent to DB2 for processing. In other words, it will be post processed.

If the `HS_FDS_CAPABILITY` is set to `SKIP` then the specified function will be stripped from the SQL statement sent to DB2. In other words the function will be ignored.

### HS_FDS_TRANSACTION_ISOLATION

| Property        | Description                                                                                   |
|:----------------|:----------------------------------------------------------------------------------------------|
| Default Value   | `READ_COMMITTED`                                                                              |
| Range of Values | {`READ_UNCOMMITTED`\|`READ_COMMITTED`\|`REPEATABLE_READ`\|`SERIALIZABLE`\|`NONE`}             |
| Syntax          | `HS_FDS_ISOLATION_LEVEL={{READ_UNCOMMITTED|READ_COMMITTED|REPEATABLE_READ|SERIALIZABLE|NONE}` |

`HS_FDS_TRANSACTION_ISOLATION` specifies the isolation level that is used for the transaction that the gateway opens on the non-Oracle database.

The isolation level `NONE` is only valid against DB2 iSeries. It specifies level` NO COMMIT`. This isolation level will force an `HS_TRANSACTION_MODEL` of `SINGLE_SITE_AUTOCOMMIT`. Please refer to DB2's documentation regarding this level.

The isolation levels of `READ_UNCOMMITTED`, `READ_COMMITTED`, `REPEATABLE_READ`, and `SERIALIZABLE` are the four isolation levels defined in the SQL standard and adopted by both both ANSI and ISO/IEC. For additional information regarding them, see [Oracle Database Concepts](../cncpt/data-concurrency-and-consistency.md).

Use caution when specifying an isolation level lower than the Oracle transaction isolation level being used, as the gateway transaction will have different Preventable Read Phenomena from what will occur in the Oracle database transaction.

### HS_FDS_PACKAGE_COLLID

| Property        | Description                                         |
|:----------------|:----------------------------------------------------|
| Default Value   | `ORACLEGTW`                                         |
| Range of Values | An alphanumeric string 1 to 18 characters in length |
| Syntax          | `HS_FDS_PACKAGE_COLLID=``collection_id`             |

`HS_FDS_PACKAGE_COLLID` specifies the package collection ID. Note that in DB2 UDB for iSeries, the collection ID is actually the name of an AS/400 library.

**Note:**

Any change to this parameter will cause a new package to be implicitly bound by the gateway. For DB2 for UDB iSeries, prior to attempting a connection, one should use the iSeries SQL command `CREATE SCHEMA` or `CREATE COLLECTION` to create an iSeries library with the name as specified for `HS_FDS_PACKAGE_COLLID`. This `COLLECTION` or `SCHEMA` should be created under the id specified in the `CONNECT TO` phrase of the Oracle SQL command `CREATE DATABASE LINK`.

### HS_NLS_LENGTH_SEMANTICS

| Property        | Description                                 |
|:----------------|:--------------------------------------------|
| Default Value   | `BYTE`                                      |
| Range of values | `BYTE | CHAR`                               |
| Syntax          | `HS_NLS_LENGTH_SEMANTICS = { BYTE | CHAR }` |

This release of gateway has Character Semantics functionality equivalent to the Oracle Database Character Semantics, that is, `NLS_LENGTH_SEMANTICS`. When `HS_NLS_LENGTH_SEMANTICS` is set to `CHAR`, the `(VAR)CHAR` columns of UDB database are to be interpreted as having `CHAR` semantics. The only situation the gateway does not honor the `HS_NLS_LENGTH_SEMANTICS=CHAR` setting is when both Oracle database and the gateway are on the same multi-byte character set

### HS_KEEP_REMOTE_COLUMN_SIZE

| Property        | Description                                             |
|:----------------|:--------------------------------------------------------|
| Default Value   | `OFF`                                                   |
| Range of Values | `OFF | LOCAL | REMOTE | ALL`                            |
| Syntax          | `HS_KEEP_REMOTE_COLUMN_SIZE = OFF | LOCAL |REMOTE |ALL` |
| Parameter type  | String                                                  |

`HS_KEEP_REMOTE_COLUMN_SIZE` specifies whether to suppress ratio expansion when computing the length of `(VAR)CHAR` datatypes during data conversion from UDB database to the gateway, and then to the Oracle database. When it is set to `REMOTE`, the expansion is suppressed between the non-Oracle database to the gateway. When it is set to `LOCAL`, the expansion is suppressed between the gateway and Oracle database. When it is set to `ALL`, the expansion is suppressed from the non-Oracle database to the Oracle database.

When the parameter is set, the expansion is suppressed when reporting the remote column size, calculating the implicit resulting buffer size, and instantiating in the local Oracle database. This has effect only for remote column size from the non-Oracle database to Oracle database. If the gateway runs on Windows and `HS_LANGUAGE=AL32UTF8`, then you must not specify this parameter, as it would influence other ratio related parameter operation. It has no effect for calculating ratio for data moving from Oracle database to non-Oracle database through gateway during `INSERT`, `UPDATE`, or `DELETE`.

### HS_FDS_RESULTSET_SUPPORT

| Property        | Description                                   |
|:----------------|:----------------------------------------------|
| Default Value   | `FALSE`                                       |
| Range of values | `TRUE | FALSE`                                |
| Syntax          | `HS_FDS_RESULTSET_SUPPORT = { TRUE | FALSE }` |

Enables result sets to be returned from stored procedures. By default, all stored procedures do not return a result set to the user.

**Note:**

If you set this initialization parameter, you must do the following:

- Change the syntax of the procedure execute statement for all existing stored procedures, to handle result sets.

- Work in the sequential mode of Heterogeneous Services.

### HS_FDS_REMOTE_DB_CHARSET

| Property        | Description                |
|:----------------|:---------------------------|
| Default Value   | None                       |
| Range of values | Not applicable             |
| Syntax          | `HS_FDS_REMOTE_DB_CHARSET` |

This parameter is valid only when `HS_LANGUAGE` is set to `AL32UTF8` and the gateway runs on Windows. As more Oracle databases and non-Oracle databases use Unicode as database character sets, it is preferable to also run the gateway in Unicode character set. To do so, you must set `HS_LANGUAGE=AL32UTF8`. However, when the gateway runs on Windows, the Microsoft ODBC Driver Manager interface can exchange data only in the double-byte character set, UCS2. This results in extra ratio expansion of described buffer and column sizes. To compensate, the gateway can re-adjust the column size if `HS_FDS_REMOTE_DB_CHARSET` is set to the corresponding non-Oracle database character set. For example, `HS_FDS_REMOTE_DB_CHARSET=KO16KSC5601`.

### HS_FDS_SUPPORT_STATISTICS

| Property        | Description                               |
|:----------------|:------------------------------------------|
| Default Value   | `TRUE`                                    |
| Range of values | `{TRUE|FALSE}`                            |
| Syntax          | `HS_FDS_SUPPORT_STATISTICS= {TRUE|FALSE}` |

We gather statistics from the non-Oracle database by default. You can choose to disable the gathering of remote database statistics by setting the `HS_FDS_SUPPORT_STATISTICS` parameter to `FALSE`.

### HS_FDS_RSET_RETURN_ROWCOUNT

| Property        | Description                                 |
|:----------------|:--------------------------------------------|
| Default Value   | `FALSE`                                     |
| Range of values | `{TRUE|FALSE}`                              |
| Syntax          | `HS_FDS_RSET_RETURN_ROWCOUNT= {TRUE|FALSE}` |

When set to `TRUE`, the gateway returns the row counts of DML statements that are executed inside a stored procedure. The row count is returned as a single row, single column result set of type signed integer.

When set to `FALSE`, the gateway skips the row counts of DML statements that are executed inside a stored procedure. This is the default behavior, and it is the behavior of 11.1 and older gateways.

### HS_FDS_AUTHENTICATE_USER

| Property        | Description                                                                  |
|:----------------|:-----------------------------------------------------------------------------|
| Default Value   | `CLEARTEXT`                                                                  |
| Range of values | `{CLEARTEXT|ENCRYPT|ENCRYPT_BOTH|CLIENT|KERBEROS}`                           |
| Syntax          | `HS_FDS_AUTHENTICATE_USER= {CLEARTEXT|ENCRYPT|ENCRYPT_BOTH|CLIENT|KERBEROS}` |

Specifies the way in which user ID and password are sent to the remote DB2 server and authenticated. Valid values are:

- `CLEARTEXT` : user ID and password are sent in clear text to server (default).

- `ENCRYPT` : password is sent encrypted to server.

- `ENCRYPT_BOTH` : user ID and password are sent encrypted to server.

- `CLIENT` : user ID is validated on the client side instead of by the server.

- `KERBEROS` : uses Kerberos to authenticate user ID.

### HS_FDS_ENCRYPT_SESSION

| Property        | Description                                           |
|:----------------|:------------------------------------------------------|
| Default Value   | `NONE`                                                |
| Range of values | `{NONE|SSL|DB2|NOTRUST_SSL}`                          |
| Syntax          | `HS_FDS_ENCRYPT_SESSION = {NONE|SSL|DB2|NOTRUST_SSL}` |

Specifies the way the session to DB2 is encrypted. Valid values are:

- `NONE` : data session is not encrypted (default).

- `SSL` : Use SSL to encrypt data session.

- `DB2` : Use DB2 encryption protocol for data session (supported only on DB2 for Linux,, UNIX, Windows, and DB2 for z/OS).

- `NOTRUST_SSL`:  This option is equivalent to the SSL setting, with initialization parameter `HS_FDS_VALIDATE_SERVER_CERT = DISABLED`

### HS_FDS_VALIDATE_SERVER_CERT

| Property        | Description                                        |
|:----------------|:---------------------------------------------------|
| Default Value   | `ENABLED`                                          |
| Range of values | `{ENABLED|DISABLED}`                               |
| Syntax          | `HS_FDS_VALIDATE_SERVER_CERT = {ENABLED|DISABLED}` |

Specifies whether the driver validates the certificate that is sent by the database server when SSL encryption is enabled through `HS_FDS_ENCRYPT_SESSION`. When using SSL server authentication, any certificate sent by the server must be issued by a trusted Certificate Authority. Valid values are:

- `ENABLED` : the gateway validates the certificate that is sent by the database server. Any certificate from the server must be issued by a trusted Certificate Authority in the truststore file. The truststore information is specified using the `HS_FDS_TRUSTSTORE_FILE` and `HS_FDS_TRUSTSTORE_PASSWORD` initialization parameters.

- `DISABLED` : the gateway does not validate the certificate that is sent by the database server.

### HS_FDS_TRUSTSTORE_FILE

| Property        | Description                                          |
|:----------------|:-----------------------------------------------------|
| Default Value   | none                                                 |
| Range of values | `path to truststore file`                            |
| Syntax          | `HS_FDS_TRUSTSTORE_FILE` `= path to truststore file` |

Specifies the path that specifies the location of the truststore file. The truststore file contains a list of the valid Certificate Authorities (CAs) that are trusted by the client machine for SSL server authentication.

### HS_FDS_TRUSTSTORE_PASSWORD

| Property        | Description                              |
|:----------------|:-----------------------------------------|
| Default Value   | none                                     |
| Range of values | `password`                               |
| Syntax          | `HS_FDS_TRUSTSTORE_PASSWORD`= `password` |

Specifies the password required to access the truststore.

### HS_FDS_SQLLEN_INTERPRETATION

| Property        | Description                             |
|:----------------|:----------------------------------------|
| Default Value   | `64`                                    |
| Range of values | `{64|32}`                               |
| Syntax          | `HS_FDS_SQLLEN_INTERPRETATION= {64|32}` |

This parameter is only valid for 64 bit platforms. ODBC standard specifies `SQLLEN` (of internal ODBC construct) being 64 bit on 64 bit platforms, but some ODBC driver managers and drivers violate this convention, and implement it as 32 bit. In order for the gateway to compensate their behavior, you need to specify `HS_FDS_SQLLEN_INTERPRETATION=32` if you use these types of driver managers and driver.

### HS_FDS_ARRAY_EXEC

| Property        | Description                       |
|:----------------|:----------------------------------|
| Default Value   | `FALSE`                           |
| Range of values | `{TRUE|FALSE}`                    |
| Syntax          | `HS_FDS_ARRAY_EXEC= {TRUE|FALSE}` |

If set to `TRUE`, the gateway will use array operations for insert, update, delete statements containing binds against the remote data source. The array size is determined by the value of the `HS_FDS_FETCH_ROWS` init parameter.

If set to `FALSE`, the gateway will not use array operations for insert, update, and delete statements. Instead, a single statement will be issued for every value.
