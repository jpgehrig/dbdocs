Consider the APIs that support migration from MySQL, the mapping of data types, support for specific MySQL APIs within Oracle, and error handling for migrated applications..

For documentation of MySQL C APIs, refer to MySQL 5.5 documentation.

### Mapping Data Types

Oracle database types are described in the Internal Data Types section of [Oracle Call Interface Programmer's Guide](../lnoci/data-types.md).

MySQL data types are fully described in MySQL documentation.

MySQL C APIs use `MYSQL_TYPE`\_symbols to process data to and from MySQL database. These type symbols are mapped to MySQL data types in the server.

For instance, `MYSQL_TYPE_VAR_STRING` is mapped to `VARCHAR` in the server.

#### Mapping Oracle Data Types to MySQL Data Types

This table shows the value of the type field in `MYSQL_FIELD` parameter returned from `mysql_fetch_field_*` calls. The Oracle database type is mapped to a MySQL C API data type.

For example: A `VARCHAR2` column is represented by `MYSQL_TYPE_VAR_STRING`.

It is recommended that users use this table when migrating MySQL applications to Oracle. The MySQL Client Library driver for Oracle will perform Data type conversions between MySQL and Oracle.

Table 7-1 Mapping Oracle Data Types to MySQL Data Types

| Oracle Data Type                                        | Maps to MySQL Data Type |
|:--------------------------------------------------------|:------------------------|
| `CHAR`                                                  | `MYSQL_TYPE_VAR_STRING` |
| `NCHAR`                                                 | `MYSQL_TYPE_VAR_STRING` |
| `NVARCHAR2`                                             | `MYSQL_TYPE_VAR_STRING` |
| `VARCHAR2`                                              | `MYSQL_TYPE_VAR_STRING` |
| `NUMBER`                                                | `MYSQL_TYPE_NEWDECIMAL` |
| `LONG`                                                  | `MYSQL_TYPE_BLOB`       |
| `CLOB`                                                  | `MYSQL_TYPE_BLOB`       |
| `NCLOB`                                                 | `MYSQL_TYPE_BLOB`       |
| `DATE`                                                  | `MYSQL_TYPE_DATETIME`   |
| `RAW`                                                   | `MYSQL_TYPE_VAR_STRING` |
| `BLOB`                                                  | `MYSQL_TYPE_BLOB`       |
| `LONG RAW`                                              | `MYSQL_TYPE_BLOB`       |
| `ROWID`                                                 | `MYSQL_TYPE_VAR_STRING` |
| `UROWID`                                                | `MYSQL_TYPE_VAR_STRING` |
| `BINARY FLOAT`                                          | `MYSQL_TYPE_FLOAT`      |
| `BINARY DOUBLE`                                         | `MYSQL_TYPE_DOUBLE`     |
| User-defined type (object type, `VARRAY`, Nested Table) | Not supported           |
| `REF`                                                   | Not supported           |
| `BFILE`                                                 | `MYSQL_TYPE_BLOB`       |
| `TIMESTAMP`                                             | `MYSQL_TYPE_DATETIME`   |
| `TIMESTAMP WITH TIME ZONE`                              | `MYSQL_TYPE_DATETIME`   |
| `TIMESTAMP WITH LOCAL TIME ZONE`                        | `MYSQL_TYPE_DATETIME`   |
| `INTERVAL YEAR TO MONTH`                                | `MYSQL_TYPE_VAR_STRING` |
| `INTERVAL DAY TO SECOND`                                | `MYSQL_TYPE_VAR_STRING` |

#### Data Type Conversions for MySQL Program Variable Data Types

The calls to mysql_stmt_bind_param() and mysql_stmt_bind_result() may be used to convert between C program variables and database column values. Similarly, OCI provides rich conversion support from server data types to many client data types.

Input conversions from a C program value to a database column value are handled by invoking mysql_stmt_bind_param(). Output to a C program value is handled through a call to mysql_stmt_bind_result().

Table 7-2 summarizes viable conversions between MySQL program variable data types and Oracle column data types. The possible values in the table are:

- `I`: input conversion is supported

- `O`: output conversion is supported

- `I/O`: both input and output conversion is supported

- `-`: conversion is not supported.

Be sure to read the corresponding notes for each data type before finalizing conversion choices.

Table 7-2 Converting MySQL Program Variable Data Types to Oracle Column Data Types

| MySQL Program Variable Data Types | CHAR    | VARCHAR2 | NUMBER | LONG  | ROWID | UROWID | DATE  | RAW   | LONG RAW |
|:----------------------------------|:--------|:---------|:-------|:------|:------|:-------|:------|:------|:---------|
| `MYSQL_TYPE_TINY`                 | `I``/O` | `I``/O`  | `I/O`  | `I`   | \-    | \-     | \-    | \-    | \-       |
| `MYSQL_TYPE_SHORT`                | `I``/O` | `I``/O`  | `I/O`  | `I`   | \-    | \-     | \-    | \-    | \-       |
| `MYSQL_TYPE_LONG`                 | `I``/O` | `I``/O`  | `I/O`  | `I`   | \-    | \-     | \-    | \-    | \-       |
| `MYSQL_TYPE_LONGLONG`             | `I``/O` | `I``/O`  | `I/O`  | `I`   | \-    | \-     | \-    | \-    | \-       |
| `MYSQL_TYPE_FLOAT`                | `I/O`   | `I/O`    | `I/O`  | `I`   | \-    | \-     | \-    | \-    | \-       |
| `MYSQL_TYPE_DOUBLE`               | `I/O`   | `I/O`    | `I/O`  | `I`   | \-    | \-     | \-    | \-    | \-       |
| `MYSQL_TYPE_DATE`                 | `I/O`   | `I/O`    | \-     | `I`   | \-    | \-     | `I/O` | \-    | \-       |
| `MYSQL_TYPE_TIME`                 | `I/O`   | `I/O`    | \-     | `I`   | \-    | \-     | `I/O` | \-    | \-       |
| `MYSQL_TYPE_DATETIME`             | `I/O`   | `I/O`    | \-     | `I`   | \-    | \-     | `I/O` | \-    | \-       |
| `MYSQL_TYPE_TIMESTAMP`            | `I/O`   | `I/O`    | \-     | `I`   | \-    | \-     | `I/O` | \-    | \-       |
| `MYSQL_TYPE_STRING`               | `I/O`   | `I/O`    | `I/O`  | `I/O` | `I/O` | `I/O`  | `I/O` | `I/O` | `I/O`    |
| `MYSQL_TYPE_VAR_STRING`           | `O`     | `O`      | `O`    | `O`   | `O`   | `O`    | `O`   | `O`   | `O`      |
| `MYSQL_TYPE_BLOB`                 | `I/O`   | `I/O`    | \-     | `I/O` | \-    | \-     | \-    | `I/O` | `I/O`    |
| `MYSQL_TYPE_TINY_BLOB`            | `O`     | `O`      | \-     | `O`   | \-    | \-     | \-    | `O`   | `O`      |
| `MYSQL_TYPE_MEDIUM_BLOB`          | `O`     | `O`      | \-     | `O`   | \-    | \-     | \-    | `O`   | `O`      |
| `MYSQL_TYPE_LONG_BLOB`            | `O`     | `O`      | \-     | `O`   | \-    | \-     | \-    | `O`   | `O`      |
| `MYSQL_TYPE_NEWDECIMAL`           | `O`     | `O`      | `O`    | \-    | \-    | \-     | \-    | \-    | \-       |

##### MYSQL_TYPE_BLOB

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. On input, column value is stored in hexadecimal format.

- `LONG`: Conversion is valid for input or output. On input, column value is stored in hexadecimal format.

- `RAW`: Conversion is valid for input or output.

- `LONG RAW`: Conversion is valid for input or output.

- Conversion is not supported for `NUMBER`, `ROWID`, `UROWID`, and `DATE`.

##### MYSQL_TYPE_DATE

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For input, host string must be in Oracle `DATE` character format. For output, column value is returned in Oracle `DATE` format.

- `DATE`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `NUMBER`, `ROWID`, `UROWID`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_DATETIME

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For input, host string must be in Oracle `DATE` character format. For output, column value is returned in Oracle `DATE` format.

- `DATE`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `NUMBER`, `ROWID`, `UROWID`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_DOUBLE

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For output, column value must represent a valid number.

- `NUMBER`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `ROWID`, `UROWID`, `DATE`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_FLOAT

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For output, column value must represent a valid number.

- `NUMBER`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `ROWID`, `UROWID`, `DATE`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_LONG

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For output, column value must represent a valid number.

- `NUMBER`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `ROWID`, `UROWID`, `DATE`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_LONG_BLOB

- `CHAR`, `VARCHAR2`, `LONG`, `RAW`, and `LONG RAW`: Conversion is valid for output.

- Conversion is not supported for `NUMBER`, `ROWID`, `UROWID`, and `DATE`.

##### MYSQL_TYPE_LONGLONG

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For output, column value must represent a valid number.

- `NUMBER`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `ROWID`, `UROWID`, `DATE`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_MEDIUM_BLOB

- `CHAR`, `VARCHAR2`, `LONG`, `RAW`, and `LONG RAW`: Conversion is valid for output.

- Conversion is not supported for `NUMBER`, `ROWID`, `UROWID`, and `DATE`.

##### MYSQL_TYPE_NEWDECIMAL

- `CHAR` and `VARCHAR2`: Conversion is valid for output. Column value must represent a valid number.

- `NUMBER`: Conversion is valid for output to C program value.

- Conversion is not supported for `LONG`, `ROWID`, `UROWID`, `DATE`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_SHORT

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For output, column value must represent a valid number.

- `NUMBER`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `ROWID`, `UROWID`, `DATE`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_STRING

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output.

- `NUMBER`: Conversion is valid for input or output. For input, the host string must represent a valid number.

- `LONG`: Conversion valid for input or output.

- `ROWID`: Conversion is valid for input or output. For input, the host string must be in Oracle `ROWID` format. For output, column value is returned in Oracle `ROWID` format.

- `UROWID`: Conversion is valid for input or output. For input, the host string must be in Oracle `UROWID` format. For output, column value is returned in Oracle `UROWID` format.

- `DATE`: Conversion is valid for input or output. For input, host string must be in Oracle `DATE` character format. For output, column value is returned in Oracle `DATE` format.

- `RAW`: Conversion is valid for input or output. For input, host string must be in hexadecimal format.

- `LONG RAW`: Conversion is valid for input or output. For input, host string must be in hexadecimal format.

##### MYSQL_TYPE_TIME

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For input, host string must be in Oracle `DATE` character format. For output, column value is returned in Oracle `DATE` format.

- `DATE`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `NUMBER`, `ROWID`, `UROWID`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_TIMESTAMP

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For input, host string must be in Oracle `DATE` character format. For output, column value is returned in Oracle `DATE` format.

- `DATE`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `NUMBER`, `ROWID`, `UROWID`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_TINY

- `CHAR` and `VARCHAR2`: Conversion is valid for input or output. For output, column value must represent a valid number.

- `NUMBER`: Conversion is valid for input or output.

- `LONG`: Conversion valid for input to database column value.

- Conversion not supported for `ROWID`, `UROWID`, `DATE`, `RAW`, and `LONG RAW`.

##### MYSQL_TYPE_TINY_BLOB

- `CHAR`, `VARCHAR2`, `LONG`, `RAW`, and `LONG RAW`: Conversion is valid for output.

- Conversion is not supported for `NUMBER`, `ROWID`, `UROWID`, and `DATE`.

##### MYSQL_TYPE_VAR_STRING

- `CHAR` and `VARCHAR2`: Conversion is valid for output to C program value.

- `NUMBER`: Conversion is valid for output to C program value.

- `LONG`: Conversion is valid for output to C program value.

- `ROWID`: Conversion is valid for output to C program value. On output, column value is returned in Oracle `ROWID` format.

- `UROWID`: Conversion is valid for output to C program value. On output, column value is returned in Oracle `UROWID` format.

- `DATE`: Conversion is valid for output to C program value. On output, column value is returned in Oracle `DATE` format.

- `RAW`: Conversion is valid for output to C program value.

- `LONG RAW`: Conversion is valid for output to C program value.

#### Data Type Conversions for MySQL External Data Types (LOB Data Type Descriptors)

The external data types Table 7-3 may be converted to the specified Oracle internal data types.

Table 7-3 Data Type Conversions for LOB Data Type Descriptors

| MySQL External Data Types | ORACLE INTERNAL CLOB/NCLOB | ORACLE INTERNAL BLOB |
|:--------------------------|:---------------------------|:---------------------|
| `MYSQL_TYPE_BIT`          | `I/O`                      | `I/O`                |
| `MYSQL_TYPE_STRING`       | `I/O`                      | `I/O`                |
| `MYSQL_TYPE_VAR_STRING`   | `O`                        | `O`                  |
| `MYSQL_TYPE_BLOB`         | I/O                        | `I/O`                |
| `MYSQL_TYPE_TINY_BLOB`    | O                          | `O`                  |
| `MYSQL_TYPE_MEDIUM_BLOB`  | O                          | `O`                  |
| `MYSQL_TYPE_LONG_BLOB`    | O                          | `O`                  |

#### Data Type Conversions for Datetime and Interval Data Types

When working with a `DATETIME` or `INTERVAL` columns, it is possible to use one of the character data types to define a host variable used in a `FETCH` or `INSERT` operation The driver automatically converts between the character data type and `DATETIME` or `INTERVAL` data type.

Table 7-4 lists external data types that may be converted to the specified internal Oracle data types.

Table 7-4 Data Conversions for Datetime and Internal Data Type

| External/Internal Types | VARCHAR, CHAR | DATE  | TS    | TSTZ  | TSLTZ | INTERVAL YEAR TO MONTH | INTERVAL DAY TO SECOND |
|:------------------------|:--------------|:------|:------|:------|:------|:-----------------------|:-----------------------|
| `MYSQL_TYPE_STRING`     | `I/O`         | `I/O` | `I/O` | `I/O` | `I/O` | `I/O`                  | `I/O`                  |
| `MYSQL_TYPE_VAR_STRING` | `O`           | `O`   | `O`   | `O`   | `O`   | `O`                    | `O`                    |
| `MYSQL_TYPE_DATE`       | `I/O`         | `I/O` | `I/O` | `I/O` | `I/O` | \-                     | \-                     |
| `MYSQL_TYPE_TIME`       | `I/O`         | `I/O` | `I/O` | `I/O` | `I/O` | \-                     | \-                     |
| `MYSQL_TYPE_DATETIME`   | `I/O`         | `I/O` | `I/O` | `I/O` | `I/O` | \-                     | \-                     |
| `MYSQL_TYPE_TIMESTAMP`  | `I/O`         | `I/O` | `I/O` | `I/O` | `I/O` | \-                     | \-                     |

### Error Handling

All errors generated by OCI or Oracle server pass to the application when methods mysql_errno() or mysql_error() are invoked after an error. The application receives an Oracle-specific error. Oracle error messages are more specific then MySQL error codes, and are therefore more pertinent to resolving the error condition.

The errors that are generated by the driver itself are in an error range reserved for the MySQL driver in the OCI error space.

The mysql_sqlstate() call attempts to map the error to the appropriate `SQLSTATE` whenever possible. In most cases, it returns `HY000`, which corresponds to the general error state.

Possible `SQLSTATE` values are:

- `00000` success

- `HY000` all other errors

However, this also means that client applications that expect more specific `SQLSTATE` errors must be partially re-written.

### Available Oracle Support for MySQL APIs

Oracle MySQL driver implements the APIs listed in MySQL C API documentation. Please note the following:

- Some MySQL functions have changed behavior, typically due to not having an equivalent behavior in Oracle; the description notes the changed behavior.

- Some MySQL functions are not supported; the description marks them accordingly. The driver returns an error for these functions, and prompts the application to work around the unsupported functionality.

Supported MySQL APIs are grouped functionally here, and here are links to more extensive information. However, we do not provide full documentation of function behavior and parameters, leaving it to the original MySQL C API documentation.

#### Client Library Initialization and Termination

The following interfaces support client library initialization and termination: mysql_library_end(), mysql_library_init(), mysql_server_end(), and mysql_server_init().

#### Connection Management

The following interfaces support connection management: my_init(), mysql_change_user(), mysql_close(), mysql_connect(), mysql_get_character_set_info(), mysql_get_ssl_cipher(), mysql_init(), mysql_options(), mysql_ping(), mysql_real_connect(), mysql_select_db(), mysql_set_character_set(), andmysql_ssl_set().

#### Error Reporting

The following interfaces support error reporting: mysql_errno(), mysql_error(), andmysql_sqlstate()

#### Statement Construction and Execution

The following interfaces support statement construction and execution: mysql_affected_rows(), mysql_escape_string(), mysql_hex_string(), mysql_kill(), mysql_query(), mysql_real_escape_string(), mysql_real_query(), and mysql_reload().

#### Result Set Processing

The following interfaces support result set processing: mysql_data_seek(), mysql_eof(), mysql_fetch_field(), mysql_fetch_field_direct(), mysql_fetch_fields(), mysql_fetch_lengths(), mysql_fetch_row(), mysql_field_count(), mysql_field_seek(), mysql_field_tell(), mysql_free_result(), mysql_insert_id(), mysql_list_dbs(), mysql_list_fields(), mysql_list_processes(), mysql_list_tables(), mysql_more_results(), mysql_next_result(), mysql_num_fields(), mysql_num_rows(), mysql_row_seek(), mysql_row_tell(), mysql_store_result(), and mysql_use_result().

#### Prepared Statements

The following interfaces support statement preparation: mysql_stmt_affected_rows(), mysql_stmt_attr_get(), mysql_stmt_attr_set(), mysql_stmt_bind_param(), mysql_stmt_bind_result(), mysql_stmt_close(), mysql_stmt_data_seek(), mysql_stmt_errno(), mysql_stmt_error(), mysql_stmt_execute(), mysql_stmt_fetch(), mysql_stmt_fetch_column(), mysql_stmt_field_count(), mysql_stmt_free_result(), mysql_stmt_init(), mysql_stmt_insert_id(), mysql_stmt_next_result(), mysql_stmt_num_rows(), mysql_stmt_param_count(), mysql_stmt_param_metadata(), mysql_stmt_prepare(), mysql_stmt_reset(), mysql_stmt_result_metadata(), mysql_stmt_row_seek(), mysql_stmt_row_tell(), mysql_stmt_send_long_data(), mysql_stmt_sqlstate(), and mysql_stmt_store_result().

#### Transaction Control

The following interfaces support transaction control: mysql_autocommit(), mysql_commit(), and mysql_rollback().

#### Information Routines

The following interfaces support information routines: mysql_character_set_name(), mysql_get_client_info(), mysql_get_client_version(), mysql_get_host_info(), mysql_get_proto_info(), mysql_get_server_info(), mysql_get_server_version(), mysql_info(), mysql_stat(), mysql_thread_id(), and mysql_warning_count().

#### Administrative Routines

The following interfaces support administrative routines: mysql_refresh(), mysql_set_server_option(), mysql_set_local_infile_default(), mysql_set_local_infile_handler(), and mysql_shutdown().

#### Miscellaneous Routines

The following interfaces support all remaining routines: mysql_create_db(), mysql_debug(), mysql_debug_info(), mysql_drop_db(), mysql_dump_debug_info(), mysql_read_query_result(), mysql_send_query(), mysql_thread_end(), mysql_thread_init(), and mysql_thread_safe().

#### my_init()

This function is a no-op function. It is called by `my_init` macro in `my_sys.h` file. All initializations are done by the `mysql_library_init()`.

##### Return Value

`0`

#### mysql_affected_rows()

Returns the number of rows processed for `INSERT`, `UPDATE`, and `DELETE` statements executed.

For `UPDATE` statements, note that the semantics of MySQL do not report rows where the new value is the same as the old value. In contrast, Oracle reports that rows are affected, even if the new value is the same as the old value. This function implements Oracle semantics. Therefore, existing applications that rely on this call may have to make programmatic changes.

For `SELECT` statement, the return is (`my_ulonglong`) -1.

##### Return Value

A number of rows that were processed by DML statement; `>0`. `0` indicates no updates were made by the statement. `-1 `indicates that the statement was a query (`SELECT`), or an error.

#### mysql_autocommit()

Sets auto commit mode to `ON` or `OFF`.

##### Return Value

`0`, if the auto commit mode is changed successfully. Non-zero if an error occurred in the process.

#### mysql_change_user()

Changes the user, including user name, password, and database on the same or different host. In Oracle Database 12c, change of the database is not supported, so the value entered for the `db` parameter is ignored.

A call to `mysql_change_user()` rolls back any active transactions, ends the current session, and then re-establishes a new connection based on information stored in the `host` parameter.

Existing applications must make necessary application logic changes to implement this behavior in Oracle Database 12c.

##### Return Value

`0` if connection can be reestablished with the original host for the supplied user name and password. Non-zero if an error occurred.

#### mysql_character_set_name()

Not supported in Oracle Database 12c. Applications that rely on results of this call must change their application logic.

##### Return Value

Empty string.

#### mysql_close()

Closes the connection and frees all associated data structures.

##### Return Value

none

#### mysql_commit()

Commits the transaction currently associated with the service context.

A `mysql_commit()` call supports the default mode in Oracle Database 12c. It therefore ignores the `completion type` system variable.

Existing applications that use this API to perform MySQL-specific `completion type` operations must change their application logic.

##### Return Value

`0` if successful, non-zero otherwise.

#### mysql_connect()

Deprecated; use mysql_real_connect().

##### Return Value

Initialized `MYSQL` structure. `NULL` if an error occurred.

#### mysql_create_db()

Not supported in Oracle Database 12c. Applications that rely on results of this call must change their application logic.

##### Return Value

`0` if successful; non-zero if an invalid MYSQL structure is passed in.

#### mysql_data_seek()

Seeks to a row in a result set based on the value specified in the offset parameter.

Offset value, being a row number, can range from `0` to `mysql_num_rows(result)` -1.

##### Return Value

None

#### mysql_debug()

Not supported in Oracle Database 12c. Applications that rely on results of this call must change their application logic.

#### mysql_debug_info()

Not supported in Oracle Database 12c. Applications that rely on results of this call must change their application logic.

##### Return Value

`0` if successful; non-zero if invalid `MYSQL` structure.

#### mysql_drop_db()

Not supported in Oracle Database 12c. Applications that rely on results of this call must change their application logic.

##### Return Value

`0` if successful; non-zero if invalid `MYSQL` structure.

#### mysql_dump_debug_info()

Not supported in Oracle Database 12c. Applications that rely on results of this call must change their application logic.

##### Return Value

`0` if successful; non-zero if an invalid `MYSQL` structure is passed in.

#### mysql_eof()

DEPRECATED. Use mysql_errno() or mysql_error() instead.

Determines if the last row of a result set has been read.

##### Return Value

`1` if fetched the last row; otherwise `0`.

#### mysql_errno()

Returns Oracle error number of the last error on the connection or the global context.

If the previous call did not have an established connection, pass in `NULL`; this returns the last error number on global context.

##### Return Value

Last error number on the `MYSQL` connection, or the last error number on the global context.

#### mysql_error()

Returns Oracle error messages for the last error on the connection or the global context.

If the previous call did not have an established connection, pass in `NULL`; this returns the last error message on global context.

##### Return Value

Last error message on the `MYSQL` connection, or the last error message on the global context.

#### mysql_escape_string()

Encodes the string in the source (`from` parameter), places it in the destination (`to` parameter), and appends a terminating `NULL`.

Supports encoding of only one character, '`\`' using the current character set in the connection.

See mysql_real_escape_string().

##### Return Value

The length of the value placed into `to`, excluding the terminating `NULL`.

#### mysql_fetch_field()

Returns the definition of one column of a result set as a `MYSQL_FIELD `structure.

Only the following attributes of the `MYSQL_FIELD` structure are supported: `flag`, `name`, `name_length`, `org_name`, `org_name_length`, `type`, and `max_length`.

- The `flag` attribute supports only the following values: `NOT_NULL_FLAG`, `NUM_FLAG`, and `BINARY_FLAG`.

- The attribute `org_name` is set to have the same value as `name` attribute.

- The attribute `org_name_length` is set to have the same value as `name_length` attribute.

##### Return value

The `MYSQL_FIELD` structure for the current column. `NULL` if no columns are left.

#### mysql_fetch_field_direct()

Retrieves the column's field definition for a specified field number as a `MYSQL_FIELD` structure.

##### Return Value

Field definition for the specific field. `NULL` if an error occurred, or if field number `fieldnr` is not in range.

#### mysql_fetch_fields()

Returns an array of all `MYSQL_FIELD` structures for a result set. Each `MYSQL_FIELD` structure gives the field definition for one column of the result set.

##### Return Value

`NULL `if an error occurred.

#### mysql_fetch_lengths()

Returns an array of lengths of the column on the current row.

##### Return Value

An array of unsigned long integers that represent the size of each column. `NULL` if an error occurred.

#### mysql_fetch_row()

Retrieves the next row of a result set.

##### Return Value

A MYSQL_ROW structure for the next row. `NULL` if there are no more rows to retrieve or if an error occurred.

#### mysql_field_count()

Returns the number of columns in the result set for the recent query on the connection.

##### Return Value

Number of fields in the result set within the MYSQL structure.; `0` if an error occurred.

#### mysql_field_seek()

Sets the field cursor to the specified offset.

##### Return Value

The offset to the field set

#### mysql_field_tell()

Returns the position of the field; used for the current field.

##### Return Value

Offset of the current field

#### mysql_free_result()

Frees the memory allocated for the result set.

##### Return Value

None

#### mysql_get_character_set_info()

Not supported in Oracle Database 12c. Applications that rely on results of this call must change their application logic.

##### Return Value

None

#### mysql_get_client_info()

Returns MySQL version number defined by `MYSQL_SERVER_VERSION `macro in `mysql_version.h` header file, in string format. The macro definition is used in the `mysql_version.h file` that builds `oramysql` library; it is not the `mysql_version.h` file used by the application.

##### Return Value

A character string that represents MySQL client library version.

#### mysql_get_client_version()

Returns current MySQL version, as defined by `MYSQL_VEERSION_ID` macro in the `mysql_version.h` header file. The macro definition is used in the `mysql_version.h file` that builds `oramysql` library; it is not the `mysql_version.h` file used by the application.

##### Return Value

An unsigned long integer for MySQL version stored in the `MYSQL_VERSION_ID `macro. The macro definition is used in the `mysql_version.h file` that builds `oramysql` library; it is not the `mysql_version.h` file used by the application.

#### mysql_get_host_info()

Returns the host name used to connect to the database.

##### Return Value

A character string of host name. `NULL` in case of an error.

#### mysql_get_proto_info()

This is a no-op under Oracle environment. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_get_server_info()

Returns the Oracle server version in text string format, such as "12.1.0.1.0".

Applications that rely on results of this call must change their application logic.

##### Return Value

A character string that represents Oracle Server Number. `NULL` if an error occurred.

#### mysql_get_server_version()

Returns Oracle Database version number, such as `120100`. This is in integer `XXYYZZ` format, where `XX` represents the major version, `YY` represents the minor version, and `ZZ` represents the version within the release level.

##### Return Value

Oracle Database version number. `0` if an error occurred.

#### mysql_get_ssl_cipher()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`NULL`

#### mysql_hex_string()

Encodes string specified by `from` parameter to hexadecimal format. Each character is encoded as two hexadecimal digits. The result is placed in the `to` parameter, with a terminal `NULL` byte.

The `to` buffer should have a minimum size equal to `length*2+1` bytes.

##### Return Value

Length of the value placed into `to` parameter, excluding the terminating `NULL` character.

#### mysql_info()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`NULL`

#### mysql_init()

Allocates a `MYSQL` structure if `NULL` is passed. Otherwise, this call initializes the passed in `MYSQL` structure.

##### Return Value

Initialized MYSQL structure. `NULL` if `MYSQL` structure cannot be allocated or initialized.

#### mysql_insert_id()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_kill()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`, and non-zero if an invalid MYSQL structure is passed in.

#### mysql_library_end()

Terminates `oramysql` library.

##### Return Value

none

#### mysql_library_init()

Initializes `oramysql` library.

##### Return Value

`0` if successful, non-zero in case of a failure to initialize MySQL library.

#### mysql_list_dbs()

Returns a list of database names that match the wild parameter on the server.

To use this API, the DBA creates the `oramysql_dbs_view` view, and grants privileges to `PUBLIC`.

##### For Oracle Database 12c

For Oracle Database 12c, view `oramysql_dbs_view` is based on the `V$DATABASE` and `V$PDBS` system objects.

When connecting to Oracle Database 12c and subsequent versions, use the following SQL script to create the view `oramysql_dbs_view` in Oracle Database 12c:

    create view oramysql_dbs_view(name) as select left.name from v$pdbs left
      union select right.name from v$database right;
    create public synonym oramysql_dbs_view for oramysql_dbs_view;
    grant select on oramysql_dbs_view to public;

If `oramysql_dbs_view` view does not exist when an application calls the `mysql_list_dbs()` function, the information is retrieved from the `V$ PDBS` and `V$ DATABASE `tables. However, this generates errors if the user does not have privileges to access these tables.

##### For Oracle Databases prior to Oracle Database 12c

Use the following SQL script to create the view `oramysql_dbs_view` in the Oracle Database:

    create view oramysql_dbs_view(name) as select name form v$database;
    create public synonym oramysql_dbs_view for oramysql_dbs_view;
    grant select on oramysql_dbs_view to public;

If the view does not exist, the wild parameter is ignored, and the call executes the following SQL statement:

    select SYS_CONTEXT( 'USERENV', 'DB_NAME') from DUAL;

##### Return Value

`NULL` if an error occurs, a `MYSQL_RES` result set if successful.

#### mysql_list_fields()

Returns the column names that match the `wild` parameter for a specified table.

##### Return Value

`NULL` if an error occurred, a MySql result set if successful.

#### mysql_list_processes()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`NULL`

#### mysql_list_tables()

This is a no-op function. Applications that rely on results of this call must change their application logic.

##### Return Value

`NULL`

#### mysql_more_results()

Verifies if more results are available from the currently executing statement.

##### Return Value

`TRUE` if more results exist; `FALSE` if no more result sets exist.

#### mysql_next_result()

Gets the next result set.

##### Returns Value

`0` if successful and there are more results; `-1` if successful and there are no more results; `>0` if an error occurred.

#### mysql_num_fields()

Returns the number of columns in a result set.

##### Return Value

An unsigned integer that represents the number of columns in the result set; returns `0` if not successful.

#### mysql_num_rows()

Returns the number of rows in the result set.

##### Return Value

The number of rows in the result set; otherwise `0`.

#### mysql_options()

This is a no-op function. Applications that rely on results of this call must change their application logic.

##### Return Value

`0` if successful, non-zero if an invalid `MYSQL` structure is passed in.

#### mysql_ping()

If the server cannot be accessed, returns an error with connection failure details.

##### Return Value

`0` if success, non-zero if error occurred.

#### mysql_query()

Executes the SQL statement pointed to by the null-terminated string.

##### Return Value

`0` if successful, non-zero if an error occurred.

#### mysql_read_query_result()

This is a no-op function; query results from `mysql_send_query()` are available when that call completes.

##### Return Value

`0`

#### mysql_real_connect()

The `db` parameter is not used in Oracle Database 12c. Existing applications using this parameter to connect to a `db` must supply the connection identifier or service name in the `host` parameter. The connection string has the following format:

    [//]host[:port][/service_name][:server][/instance_name]

For instance, the host parameter would appear as: `ca-tools3.``hostname``.com/orcl3`, when connecting to host `ca-tools3.``hostname``.com` with SID `orcl3`.

The parameters `db`, `port`, `unix_socket`, and `client_flag` are not in use. When the user must specify the port, it has to be in the syntax method used for `host` parameter.

##### Return Value

`MYSQL` structure initialized if successful. `NULL` in case initialization does not work.

#### mysql_real_escape_string()

Encodes the string in the source (`from` parameter) and the result is placed in the destination (`to` parameter) and a terminating null byte is appended.

Note that only single-quote characters are escaped. Each single-quote is escaped using Oracle semantics. The `to` buffer should have a minimum size of `length*2+1 bytes`. Each single quote in the original string is replaced by two consecutive single quotes.

See mysql_escape_string().

##### Return Value

The length of the value placed into `to` buffer, excluding the terminating `NULL`. `0 `otherwise.

#### mysql_real_query()

This function executes the query string.

##### Return Value

`0` if successful, non-zero in case of an error.

#### mysql_refresh()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0` if successful. Non-zero if an invalid MySQL structure was passed in.

#### mysql_reload()

Reloads the grant tables. This function is deprecated, and has not been implemented. Use mysql_query() instead. Applications that rely on results of this call must change their application logic.

#### mysql_rollback()

Rolls back the current transaction defined as the set of statements executed after the last mysql_commit() or mysql_real_connect() call. If the application is running under object mode, the modified or updated objects in the object cache for this transaction are also rolled back.

A `mysql_rollback()` call supports the default mode in Oracle Database 12c. It therefore ignores the `completion type` system variable.

Existing applications that use this API to perform MySQL-specific `completion type` operations must change their application logic.

##### Return Value

Error if an attempt is made to roll back a global transaction that is not currently active.

#### mysql_row_seek()

Sets to a particular row and returns offset of previous row.

##### Return Value

Offset of previous row in `MYSQL_ROW_OFFSET` structure.

#### mysql_row_tell()

Gives the current row position in the result set.

##### Return Value

Offset of current row in `MYSQL_ROW_OFFSET` structure. `NULL` if an error occurred.

#### mysql_select_db()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_send_query()

Sends a query. This function is not asynchronous in `oramysql` library. Instead, the call blocks until the query is executed.

##### Return Value

`0` if successful, non-zero if an error occurred.

#### mysql_server_end()

Terminates and cleans up `oramysql` library.

##### Return Value

none

#### mysql_server_init()

Initializes the `oramysql` client library before any connections are created. The function `mysql_library_init()` macro is defined to be `mysql_server_init()` in `mysql.h` header file. This call is not thread-safe. Only one thread is expected to call it.

##### Return Value

`0` if successful, non-zero if an error occurred.

#### mysql_set_character_set()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_set_local_infile_default()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_set_local_infile_handler()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_set_server_option()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_shutdown()

Helps shutdown an Oracle Database instance. Before using the `mysql_shutdown` API, the C program must connect to server with `SYSDBA` or `SYSOPER` session.

The parameters `mysql_shutdown_level` and `mysql_enum_shutdown_level` are ignored. Internally, the [`OCIDBShutdown()`](../lnoci/connect-authorize-and-initialize-functions.md) call is executed in the `OCI_DEFAULT` mode.

##### Return Value

`0` if successful. Non-zero if an error occurred.

#### mysql_sqlstate()

Returns `SQLSTATE` string which is not null-terminated. There are many `SQLSTATE` codes in MySQL which are not in use.

##### Return Value

`SQLSTATE` code: `00000` - Success, or `HY000` - All other errors.

#### mysql_ssl_set()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0` if successful. Non-zero if an invalid MYSQL structure was passed.

#### mysql_stat()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

A string of 4 blanks (" ") if successful. `NULL` if an invalid `MYSQL` structure was passed.

#### mysql_stmt_affected_rows()

This function returns the number of rows affected by the execution on the prepared statement.

##### Return Value

Number of rows affected by the DML operation if successful. `(my_ulonglong)-1` if an error occurred, or a `SELECT` statement was executed.

#### mysql_stmt_attr_get()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_stmt_attr_set()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_stmt_bind_param()

This function binds all the parameters in the prepared statement.

##### Return Value

`0 `if parameters are bound successfully. Non-zero if an error occurred.

#### mysql_stmt_bind_result()

Binds program variables for all `SELECT` list columns of a prepared statement.

##### Return Value

`0 `if successful. Non-zero if an error occurred.

#### mysql_stmt_close()

Closes a `MYSQL_STMT` object.

##### Return Value

`0`

#### mysql_stmt_data_seek()

This function seeks to get data for a particular row.

##### Return Value

None

#### mysql_stmt_errno()

Returns error number for the last error that occurred on the `MYSQL_STMT` object.

##### Return Value

none

#### mysql_stmt_error()

This function returns error message for the last error that occurred on the `MYSQL_STMT` object.

##### Return Value

A `const *char` error message.

#### mysql_stmt_execute()

This function executes the prepared statement.

##### Return Value

`0 `if the statement executed successfully; non-zero if an error occurred.

#### mysql_stmt_fetch()

This function fetches one row in program variables bound by the `mysql_stmt_bind_result` call.

##### Return Value

0 if one row is successfully fetched. `MYSQL_NO_DATA` if no more rows/data exists. `MYSQL_DATA_TRUNCATED` if data truncation occurred. `1 `if an error occurred.

#### mysql_stmt_fetch_column()

This function fetches one column from the current result set row.

##### Return Value

`0 `if the value was fetched successfully. Non-zero if an error occurred.

#### mysql_stmt_field_count()

Fetches the number of fields in the `MYSQL_STMT` object.

##### Return Value

0 if an error occurred; otherwise, the number of fields in the result set associated with the `MYSQL_STMT` object.

#### mysql_stmt_free_result()

Frees the result set associated with the `MYSQL_STMT` object.

##### Return Value

`0`

#### mysql_stmt_init()

Creates a new `MYSQL_STMT` object from the `MYSQL` connection object.

##### Return Value

`MYSQL_STMT` object if successful. `NULL` if an error occurred.

#### mysql_stmt_insert_id()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_stmt_next_result()

This function is not implemented. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_stmt_num_rows()

Returns the number of rows in a stored result set. In case of a non-stored (unbuffered result set), it returns the total number of rows fetched so far.

##### Return Value

0 if an error occurred in fetching the number of rows.

#### mysql_stmt_param_count()

Returns the number of bind parameters in the prepared statement.

##### Return Value

`0` if an error occurred in returning the number of bind parameters.

#### mysql_stmt_param_metadata()

This function is cast to MySql result set `(MYSQL_RES *) NULL`

##### Return Value

`NULL`

#### mysql_stmt_prepare()

Prepares a statement in the `MYSQL_STMT` for execution.

##### Return Value

`0` if successful, non-zero if an error occurred.

#### mysql_stmt_reset()

Resets the prepared statement in the `MYSQL_STMT`.

##### Return Value

`0`

#### mysql_stmt_result_metadata()

Returns the metadata for the result of a `SELECT` statement that is executed through a `MYSQL_STMT` object.

##### Return Value

A result set that describes the metadata of the prepared `SELECT` statement.` NULL` if an error occurred.

#### mysql_stmt_row_seek()

Seeks to a row position and returns the offset of the previous row.

##### Return Value

An offset of the previous row in `MYSQL_ROW_OFFSET` structure.

#### mysql_stmt_row_tell()

Gives the current row position in the result set.

##### Return Value

Current row position. `NULL` if an error occurred.

#### mysql_stmt_send_long_data()

Sends parameter data to the server in parts.

The function `mysql_stmt_bind_param()` must be called first, then `mysql_stmt_send_long_data()`, followed by `mysql_stmt_execute()`.

The function can be called multiple times to send parts of a character or binary data value for a column.

##### Return Value

`0` if the data is sent to the server successfully, non-zero if an error occurred.

#### mysql_stmt_sqlstate()

Returns `SQLSTATE` string for the recent prepared statement. There are many `SQLSTATE` codes in MySQL that are not used.

##### Return Value

`SQLSTATE` codes: "`00000`" - Success, or "`HY0000`" - All other errors.

#### mysql_stmt_store_result()

Stores the result set from the last query.

If the last query was a `SELECT`, a result set is returned. If the last statement was a non-`SELECT` or error, a `NULL` result set is returned.

##### Return Value

A valid result set if successful, `NULL` if an error occurred, or a non-`SELECT` statement.

#### mysql_store_result()

Stores the result set from the last query.

If the last query was `SELECT`, returns a result set.

If the last statement was a non-`SELECT` or an error, a `NULL` result set is returned.

##### Return Value

A valid result set if successful; otherwise, `NULL` for errors or non-`SELECT` statements.

#### mysql_thread_end()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

none

#### mysql_thread_id()

Returns Oracle session identifier (SID) for the connection. This is obtained internally by executing the following SQL statement:

    select SYS_CONTEXT('USERENV', 'SID') from DUAL;

Applications that rely on results of this call must change their application logic.

##### Return Value

Oracle session identifier (SID). `0` if an error occurs.

#### mysql_thread_init()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0`

#### mysql_thread_safe()

The `oramysql` library is thread-safe, so this function always returns `TRUE`.

##### Return Value

`TRUE`

#### mysql_use_result()

Initiates a result set retrieval.

##### Return Value

`NULL` if an error occurred, a valid result set if successful.

#### mysql_warning_count()

This is a no-op API. Applications that rely on results of this call must change their application logic.

##### Return Value

`0` if successful, non-zero if an error occurred.
