The Oracle database initialization parameters in the `init.ora` file are distinct from gateway initialization parameters. Set the gateway parameters in the initialization parameter file using an agent-specific mechanism, or set them in the Oracle data dictionary using the `DBMS_HS` package. The gateway initialization parameter file must be available when the gateway is started.

The following topics contain a list of the gateway initialization parameters that can be set for each gateway and their description. The topics also describe the initialization parameter file syntax.

- Initialization Parameter File Syntax

- Oracle Database Gateway for Informix Initialization Parameters

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

  - A string of characters that does not contain any backslashes, white space or double quotation marks (")

  - A quoted string beginning with a double quotation mark and ending with a double quotation mark. The following can be used inside a quoted string:

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

  `PRIVATE` specifies that the initialization parameter should be private to the agent and should not be uploaded to the Oracle database. Most initialization parameters should not be private. If, however, you are storing sensitive information like a password in the initialization parameter file, then you may not want it uploaded to the server because the initialization parameters and values are not encrypted when uploaded. Making the initialization parameters private prevents the upload from happening and they do not appear in dynamic performance views. Use `PRIVATE` for the initialization parameters only if the parameter value includes sensitive information such as a user name or password.

  `SET PRIVATE` specifies that the parameter value is set as an environment variable for the agent process and is also private (not transferred to the Oracle database, not appearing in dynamic performance views or graphical user interfaces).

### Oracle Database Gateway for Informix Initialization Parameters

The initialization file parameters that can be set for the Oracle Database Gateway for Informix are as follows:

- HS_DB_DOMAIN

- HS_DB_INTERNAL_NAME

- HS_DB_NAME

- HS_DESCRIBE_CACHE_HWM

- HS_LANGUAGE

- HS_LONG_PIECE_TRANSFER_SIZE

- HS_OPEN_CURSORS

- HS_RPC_FETCH_REBLOCKING

- HS_RPC_FETCH_SIZE

- HS_TIME_ZONE

- HS_FDS_TRANSACTION_ISOLATION

- HS_TRANSACTION_MODEL

- IFILE

- HS_FDS_TIMESTAMP_MAPPING

- HS_FDS_DATE_MAPPING

- HS_FDS_CONNECT_INFO

- HS_FDS_RECOVERY_ACCOUNT

- HS_FDS_RECOVERY_PWD

- HS_FDS_TRACE_LEVEL

- HS_FDS_TRANSACTION_LOG

- HS_FDS_FETCH_ROWS

- HS_IDLE_TIMEOUT

- HS_NLS_LENGTH_SEMANTICS

- HS_KEEP_REMOTE_COLUMN_SIZE

- HS_FDS_REMOTE_DB_CHARSET

- HS_FDS_SUPPORT_STATISTICS

- HS_FDS_SQLLEN_INTERPRETATION

- HS_FDS_ARRAY_EXEC

### HS_DB_DOMAIN

| Property        | Description         |
|:----------------|:--------------------|
| Default value   | `WORLD`             |
| Range of values | 1 to 199 characters |

Specifies a unique network sub-address for a non-Oracle system. The `HS_DB_DOMAIN` initialization parameter is similar to the `DB_DOMAIN` initialization parameter, described in the Oracle Database Reference. The `HS_DB_DOMAIN` initialization parameter is required if you use the Oracle Names server. The `HS_DB_NAME` and `HS_DB_DOMAIN` initialization parameters define the global name of the non-Oracle system.

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

| Property        | Description                                                          |
|:----------------|:---------------------------------------------------------------------|
| Default value   | `50`                                                                 |
| Range of values | `1` to the value of Oracle's `OPEN_CURSORS` initialization parameter |

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

### HS_TIME_ZONE

| Property                            | Description                                               |
|:------------------------------------|:----------------------------------------------------------|
| Default value for '\[+\|-\]hh:mm'   | Derived from the `NLS_TERRITORY` initialization parameter |
| Range of values for '\[+\|-\]hh:mm' | Any valid datetime format mask                            |

Specifies the default local time zone displacement for the current SQL session. The format mask, \[+\|-\]hh:mm, is specified to indicate the hours and minutes before or after UTC (Coordinated Universal Time—formerly Greenwich Mean Time). For example:

    HS_TIME_ZONE = [+ | -] hh:mm

### HS_TRANSACTION_MODEL

| Property        | Description                                                                                    |
|:----------------|:-----------------------------------------------------------------------------------------------|
| Default Value   | `COMMIT_CONFIRM`                                                                               |
| Range of Values | `COMMIT_CONFIRM`, `READ_ONLY`, `SINGLE_SITE`, `READ_ONLY_AUTOCOMMIT`, `SINGLE_SITE_AUTOCOMMIT` |

Specifies the type of transaction model that is used when the non-Oracle database is updated by a transaction.

The following values are possible:

- `COMMIT_CONFIRM` provides read and write access to the non-Oracle database and allows the gateway to be part of a distributed update. To use the commit-confirm model, the following items must be created in the non-Oracle database:

  - Transaction log table. The default table name is `HS_TRANSACTION_LOG`. A different name can be set using the `HS_FDS_TRANSACTION_LOG` parameter. The transaction log table must be granted `SELECT`, `DELETE`, and `INSERT` privileges set to public.

  - Recovery account. The account name is assigned with the `HS_FDS_RECOVERY_ACCOUNT` parameter.

  - Recovery account password. The password is assigned with the `HS_FDS_RECOVERY_PWD` parameter.

- `READ_ONLY` provides read access to the non-Oracle database.

- `SINGLE_SITE` provides read and write access to the non-Oracle database. However, the gateway cannot participate in distributed updates.

- `READ_ONLY_AUTOCOMMIT` provides read only access to the non-Oracle database that does not use logging.

- `SINGLE_SITE_AUTOCOMMIT` provides read and write access to the non-Oracle database without logging. The gateway cannot participate in distributed updates. Moreover, any update to the non-Oracle database is committed immediately.

### IFILE

| Property        | Description                |
|:----------------|:---------------------------|
| Default value   | None                       |
| Range of values | Valid parameter file names |

Use the `IFILE` initialization parameter to embed another initialization file within the current initialization file. The value should be an absolute path and should not contain environment variables. The three levels of nesting limit do not apply.

**See Also:**

[Oracle Database Reference](../refrn/IFILE.md)

### HS_FDS_TIMESTAMP_MAPPING

| Property        | Description                                        |
|:----------------|:---------------------------------------------------|
| Default Value   | `DATE`                                             |
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

### HS_FDS_CONNECT_INFO

| Property        | Description    |
|:----------------|:---------------|
| Default Value   | None           |
| Range of Values | Not applicable |

`HS_FDS_CONNECT_INFO` that describes the connection to the non-Oracle system.

The default initialization parameter file already has an entry for this parameter. The syntax for `HS_FDS_CONNECT_INFO` for the gateway is as follows:

    HS_FDS_CONNECT_INFO=host_name:port_number/server_name/database_name

where, `host_name` is the host name or IP address of the machine hosting the Informix database, `port_number` is the port number of the Informix database server, `server_name` is the name of the Informix database server, and `database_name` is the Informix database name.

This release supports IPv6 format, so you can enter IPv6 format in place of `hostname`, but you need to wrap square brackets around the IPv6 specification.

For example,

    HS_FDS_CONNECT_INFO=[2001:0db8:20c:f1ff:fec6:38af]:port_number/…

### HS_FDS_RECOVERY_ACCOUNT

| Property        | Description       |
|:----------------|:------------------|
| Default Value   | RECOVER           |
| Range of values | Any valid user ID |

Specifies the name of the recovery account used for the commit-confirm transaction model. An account with user name and password must be set up at the non-Oracle system. For more information about the commit-confirm model, see the `HS_TRANSACTION_MODEL` parameter.

The name of the recovery account is case-sensitive.

### HS_FDS_RECOVERY_PWD

| Property        | Description        |
|:----------------|:-------------------|
| Default Value   | `RECOVER`          |
| Range of values | Any valid password |

Specifies the password of the recovery account used for the commit-confirm transaction model set up at the non-Oracle system. For more information about the commit-confirm model, see the `HS_TRANSACTION_MODEL` parameter.

The name of the password of the recovery account is case-sensitive.

### HS_FDS_TRACE_LEVEL

| Property        | Description        |
|:----------------|:-------------------|
| Default Value   | `OFF`              |
| Range of values | `OFF`, `ON`, DEBUG |

Specifies whether error tracing is turned on or off for gateway connectivity.

The following values are valid:

- OFF disables the tracing of error messages.

- ON enables the tracing of error messages that occur when you encounter problems. The results are written by default to a gateway log file in LOG directory where the gateway is installed.

- DEBUG enables the tracing of detailed error messages that can be used for debugging.

### HS_FDS_TRANSACTION_ISOLATION

| Property        | Description                                                                              |
|:----------------|:-----------------------------------------------------------------------------------------|
| Default Value   | `READ_COMMITTED`                                                                         |
| Range of Values | {`READ_UNCOMMITTED`\|`READ_COMMITTED`\|`REPEATABLE_READ`\|`SERIALIZABLE`}                |
| Syntax          | `HS_FDS_ISOLATION_LEVEL={{READ_UNCOMMITTED|READ_COMMITTED|REPEATABLE_READ|SERIALIZABLE}` |

`HS_FDS_TRANSACTION_ISOLATION` specifies the isolation level that is used for the transaction that the gateway opens on the non-Oracle database.

The isolation levels of `READ_UNCOMMITTED`, `READ_COMMITTED`, `REPEATABLE_READ`, and `SERIALIZABLE` are the four isolation levels defined in the SQL standard and adopted by both ANSI and ISO/IEC. For additional information regarding them, see [Oracle Database Concepts](../cncpt/data-concurrency-and-consistency.md).

Use caution when specifying an isolation level lower than the Oracle transaction isolation level being used, as the gateway transaction will have different Preventable Read Phenomena from what will occur in the Oracle database transaction.

### HS_FDS_TRANSACTION_LOG

| Property        | Description          |
|:----------------|:---------------------|
| Default Value   | `HS_TRANSACTION_LOG` |
| Range of Values | Any valid table name |

Specifies the name of the table created in the non-Oracle system for logging transactions. For more information about the transaction model, see the `HS_TRANSACTION_MODEL` parameter.

### HS_FDS_FETCH_ROWS

| Property        | Description                        |
|:----------------|:-----------------------------------|
| Default Value   | `100`                              |
| Range of Values | Any integer between `1` and `1000` |
| Syntax          | `HS_FDS_FETCH_ROWS=``num`          |

`HS_FDS_FETCH_ROWS` specifies the fetch array size. This is the number of rows to be fetched from the non-Oracle database and to return to Oracle database at one time. This parameter will be affected by the `HS_RPC_FETCH_SIZE` and `HS_RPC_FETCH_REBLOCKING` parameters.

### HS_IDLE_TIMEOUT

| Property        | Description             |
|:----------------|:------------------------|
| Default Value   | 0 (no timeout)          |
| Range of Values | 0-9999 (minutes)        |
| Syntax          | `HS_IDLE_TIMEOUT=``num` |

This feature is only available for Oracle Net TCP protocol. When there is no activity for a connected gateway session for this specified time period, the gateway session would be terminated automatically with pending update (if any) rolled back.

### HS_NLS_LENGTH_SEMANTICS

| Property        | Description                                 |
|:----------------|:--------------------------------------------|
| Default Value   | `BYTE`                                      |
| Range of Values | `BYTE | CHAR`                               |
| Syntax          | `HS_NLS_LENGTH_SEMANTICS = { BYTE | CHAR }` |

This release of gateway has Character Semantics functionality equivalent to the Oracle Database Character Semantics, that is, `NLS_LENGTH_SEMANTICS`. When `HS_NLS_LENGTH_SEMANTICS` is set to `CHAR`, the `(VAR)CHAR` columns of Informix database are to be interpreted as having `CHAR` semantics. The only situation the gateway does not honor the `HS_NLS_LENGTH_SEMANTICS=CHAR` setting is when both Oracle database and the gateway are on the same multi-byte character set.

### HS_KEEP_REMOTE_COLUMN_SIZE

| Property        | Description                                              |
|:----------------|:---------------------------------------------------------|
| Default Value   | `OFF`                                                    |
| Range of Values | `OFF | LOCAL |REMOTE | ALL`                              |
| Syntax          | `HS_KEEP_REMOTE_COLUMN_SIZE = OFF | LOCAL |REMOTE | ALL` |
| Parameter type  | String                                                   |

`HS_KEEP_REMOTE_COLUMN_SIZE` specifies whether to suppress ratio expansion when computing the length of `(VAR)CHAR` datatypes during data conversion from non-Oracle database to the gateway, and then to the Oracle database. When it is set to `REMOTE`, the expansion is suppressed between the non-Oracle database and the gateway. When it is set to `LOCAL`, the expansion is suppressed between the gateway and the Oracle database. When it is set to `ALL`, the expansion is suppressed from the non-Oracle database to the Oracle database.

When the parameter is set, the expansion is suppressed when reporting the remote column size, calculating the implicit resulting buffer size, and instantiating in the local Oracle database. This has effect only for remote column size from non-Oracle database to Oracle database. If the gateway runs on Windows and `HS_LANGUAGE=AL32UTF8`, then you must not specify this parameter, as it would influence other ratio related parameter operation. It has no effect for calculating ratio for data moving from Oracle database to non-Oracle database through gateway during `INSERT`, `UPDATE`, or `DELETE`.

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
| Default Value   | `TRUE`                            |
| Range of values | `{TRUE|FALSE}`                    |
| Syntax          | `HS_FDS_ARRAY_EXEC= {TRUE|FALSE}` |

If set to `TRUE`, the gateway will use array operations for insert, update, delete statements containing binds against the remote data source. The array size is determined by the value of the `HS_FDS_FETCH_ROWS` eter.

If set to `FALSE`, the gateway will not use array operations for insert, update, and delete statements. Instead, a single statement will be issued for every value.
