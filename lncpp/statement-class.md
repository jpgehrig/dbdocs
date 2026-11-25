A `Statement` object is used for executing SQL statements. The statement may be a query returning result set, or a non-query statement returning an update count. Non-query SQL can be insert, update, or delete statements. Non-query SQL statements can also be DML statements (such as create, grant, and so on) or stored procedure calls.

A query, insert / update / delete, or stored procedure call statements may have` IN` bind parameters, while a stored procedure call statement may have either `OUT` bind parameters or bind parameters that are both `IN` and `OUT`, referred to as `IN`/`OUT` parameters.

The `Statement` class methods are divided into three categories:

- `Statement` methods applicable to all statements

- Methods applicable to prepared statements with `IN` bind parameters

- Methods applicable to callable statements with `OUT` or `IN/OUT` bind parameters.

Table 13-43 Enumerated Values used by the Statement Class

| Attribute | Options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Status`  | • `NEEDS_STREAM_DATA` indicates that output `Streams` must be written for the streamed `IN` bind parameters. If there are multiple streamed parameters, call the getCurrentStreamParam() method to find out the bind parameter that needs the stream. If the statement is executed iteratively, call getCurrentIteration() to find the iteration for the stream that must to be written.<br>• `PREPARED` indicates that the `Statement` is set to a query.<br>• `RESULT_SET_AVAILABLE` indicates that the getResultSet() method must be called to get the result set.<br>• `STREAM_DATA_AVAILABLE` indicates that the input `Streams` must be read for the streamed `OUT` bind parameters. If there are multiple streamed parameters, call the getCurrentStreamParam() method to find out the bind parameter that needs the stream. If the statement is executed iteratively, call getCurrentIteration() to find the iteration for the stream that must be read.<br>• `UPREPARED` indicates that the `Statement` object is not set to a query.<br>• `UPDATE_COUNT_AVAILABLE` indicates that the getUb8RowCount() method must be called to find out the update count. |

Table 13-44 Statement Methods

| Method                                    | Description                                                                                                               |
|:------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------|
| addIteration()                            | Adds an iteration for execution.                                                                                          |
| closeResultSet()                          | Immediately releases a result set's database and OCCI resources instead of waiting for automatic release.                 |
| closeStream()                             | Closes the stream specified by the parameter `stream`.                                                                    |
| disableCaching()                          | Disables statement caching.                                                                                               |
| execute()                                 | Runs the SQL statement.                                                                                                   |
| executeArrayUpdate()                      | Runs insert, update, and delete statements that use only the `setDataBuffer()` or stream interface for bind parameters.   |
| executeQuery()                            | Runs a SQL statement that returns a single `ResultSet`.                                                                   |
| executeUpdate()                           | Runs a SQL statement that does not return a `ResultSet`.                                                                  |
| getAutoCommit()                           | Returns the current auto-commit state.                                                                                    |
| getBatchErrorMode()                       | Returns the state of the batch error mode.                                                                                |
| getBDouble()                              | Returns the value of an IEEE754 `DOUBLE` as a `BDouble` object.                                                           |
| getBfile()                                | Returns the value of a `BFILE` as a `Bfile` object.                                                                       |
| getBFloat()                               | Returns the value of a `IEEE754 FLOAT` as a `BFloat` object.                                                              |
| getBlob()                                 | Returns the value of a `BLOB` as a `Blob` object.                                                                         |
| getBytes()                                | Returns the value of a `SQL BINARY` or `VARBINARY` parameter as `Bytes`.                                                  |
| getCharSet()                              | Returns the characterset that is in effect for the specified parameter, as a `string`.                                    |
| getCharSetUString()                       | Returns the characterset that is in effect for the specified parameter, as a `UString`.                                   |
| getClob()                                 | Returns the value of a `CLOB` as a `Clob` object.                                                                         |
| getConnection()                           | Returns the connection from which the `Statement` object was instantiated.                                                |
| getCurrentIteration()                     | Returns the iteration number of the current iteration that is being processed.                                            |
| getCurrentStreamIteration()               | Returns the current iteration for which stream data is to be read or written.                                             |
| getCurrentStreamParam()                   | Returns the parameter index of the current output Stream that must be read or written.                                    |
| getCursor()                               | Returns the `REF CURSOR` value of an OUT parameter as a `ResultSet`.                                                      |
| getDatabaseNCHARParam()                   | Returns whether data is in NCHAR character set.                                                                           |
| getDate()                                 | Returns the value of a parameter as a `Date` object                                                                       |
| getDMLRowCounts()                         | Returns the row counts affected by each iteration of the current DML statement when it executes with multiple iterations. |
| getDouble()                               | Returns the value of a parameter as a C++ double.                                                                         |
| getBFloat()                               | Returns the value of a parameter as an IEEE754 float.                                                                     |
| getFloat()                                | Returns the value of a parameter as a C++ float.                                                                          |
| getInt()                                  | Returns the value of a parameter as a C++ int.                                                                            |
| getIntervalDS()                           | Returns the value of a parameter as a `IntervalDS` object.                                                                |
| getIntervalYM()                           | Returns the value of a parameter as a `IntervalYM` object.                                                                |
| getMaxIterations()                        | Returns the current limit on maximum number of iterations.                                                                |
| getMaxParamSize()                         | Returns the current max parameter size limit.                                                                             |
| getNumber()                               | Returns the value of a parameter as a `Number` object.                                                                    |
| getObject()                               | Returns the value of a parameter as a `PObject`.                                                                          |
| getOCIStatement()                         | Returns the OCI statement handle associated with the `Statement`.                                                         |
| getRef()                                  | Returns the value of a REF parameter as `RefAny`                                                                          |
| getResultSet()                            | Returns the current result as a `ResultSet`.                                                                              |
| getRowCountsOption()                      | Determines if the DML row counts option is enabled.                                                                       |
| getRowid()                                | Returns the row id parameter value as a `Bytes` object.                                                                   |
| getSQL()                                  | Returns the current SQL string associated with the `Statement` object.                                                    |
| getSQLUString()                           | Returns the current SQL string associated with the `Statement` object; globalization enabled.                             |
| getStream()                               | Returns the value of the parameter as a stream.                                                                           |
| getString()                               | Returns the value of the parameter as a string.                                                                           |
| getTimestamp()                            | Returns the value of the parameter as a `Timestamp` object.                                                               |
| getUb8RowCount()                          | Returns the number of rows processed.                                                                                     |
| getUInt()                                 | Returns the value of the parameter as a C++ unsigned integer.                                                             |
| getUpdateCount()                          | Returns the number of rows processed.                                                                                     |
| getUString()                              | Returns the value of a `UString`.                                                                                         |
| getVector()                               | Returns the specified parameter as a vector.                                                                              |
| getVectorOfRefs()                         | Returns the column in the current position as a vector of `REF`s.                                                         |
| isNull()                                  | Checks whether the parameter is `NULL`.                                                                                   |
| isTruncated()                             | Checks whether the value is truncated.                                                                                    |
| preTruncationLength()                     | Returns the actual length of the parameter before truncation.                                                             |
| registerOutParam()                        | Registers the type and max size of the OUT parameter.                                                                     |
| setAutoCommit()                           | Specifies auto commit mode.                                                                                               |
| setBatchErrorMode()                       | Enables or disables the batch error processing mode.                                                                      |
| setBDouble()                              | Sets a parameter to an IEEE double value.                                                                                 |
| setBfile()                                | Sets a parameter to a `Bfile` value.                                                                                      |
| setBFloat()                               | Sets a parameter to an IEEE float value.                                                                                  |
| setBinaryStreamMode()                     | Specifies that a column is to be returned as a binary stream.                                                             |
| setBlob()                                 | Sets a parameter to a `Blob` value.                                                                                       |
| setBytes()                                | Sets a parameter to a `Bytes` array.                                                                                      |
| setCharacterStreamMode()                  | Specifies that a column is to be returned as a character stream.                                                          |
| [setCharSet()](resultset-class.md)        | Specifies the characterset as a `string`.                                                                                 |
| [setCharSetUString()](resultset-class.md) | Specifies the character set as a `UString`.                                                                               |
| setClob()                                 | Sets a parameter to a `Clob` value.                                                                                       |
| setDate()                                 | Sets a parameter to a `Date` value.                                                                                       |
| setDatabaseNCHARParam()                   | Sets to true if the data is to be in the NCHAR character set of the database; set to false to restore the default.        |
| setDataBuffer()                           | Specifies a data buffer where data would be available for reading or writing.                                             |
| setDataBufferArray()                      | Specifies an array of data buffers where data would be available for reading or writing.                                  |
| setDouble()                               | Sets a parameter to a C++ double value.                                                                                   |
| setErrorOnNull()                          | Enables Or Disables exceptions for reading of `NULL` values.                                                              |
| setErrorOnTruncate()                      | Enables Or Disables exception when truncation occurs.                                                                     |
| setFloat()                                | Sets a parameter to a C++ float value.                                                                                    |
| setInt()                                  | Sets a parameter to a C++ int value.                                                                                      |
| setIntervalDS()                           | Sets a parameter to a `IntervalDS` value.                                                                                 |
| setIntervalYM()                           | Sets a parameter to a `IntervalYM` value.                                                                                 |
| setMaxIterations()                        | Sets the maximum number of invocations that area made for the DML statement.                                              |
| setMaxParamSize()                         | Sets the maximum amount of data that can sent or returned from the parameter.                                             |
| setNull()                                 | Sets a parameter to SQL `NULL`.                                                                                           |
| setNumber()                               | Sets a parameter to a `Number` value.                                                                                     |
| setObject()                               | Sets the value of a parameter using an object.                                                                            |
| setPrefetchMemorySize()                   | Sets the amount of memory that is used internally by OCCI to store data fetched during each round trip to the server.     |
| setPrefetchRowCount()                     | Sets the number of rows that are fetched internally by OCCI during each round trip to the server.                         |
| setRef()                                  | Sets the value of a parameter to a reference.                                                                             |
| setRowCountsOption()                      | Set `flag` to `TRUE` to enable return of DML row counts per iteration when invoking getDMLRowCounts().                    |
| setRowid()                                | Sets a row id bytes array for a bind position.                                                                            |
| setSQL()                                  | Associates new SQL string with `Statement` object.                                                                        |
| setSQLUString()                           | Associates new SQL string with `Statement` object; globalization enabled.                                                 |
| setString()                               | Sets a parameter for a specified index.                                                                                   |
| setTimestamp()                            | Sets a parameter to a `Timestamp` value.                                                                                  |
| setUInt()                                 | Sets a parameter to a C++ unsigned int value.                                                                             |
| setUString()                              | Sets a parameter for a specified index; globalization enabled.                                                            |
| setVector()                               | Sets a parameter to a vector of unsigned int.                                                                             |
| setVectorOfRefs()                         | Sets a parameter to a vector; is necessary when the type is a collection of `REF`s.                                       |
| status()                                  | Returns the current status of the statement. This is useful when there is streamed data to be written.                    |

### 13.30.1 addIteration()

After specifying set parameters, an iteration is added for execution.

#### Syntax

    void addIteration();

### 13.30.2 closeResultSet()

Immediately releases the specified `resultSet`'s database and OCCI resources when the result set is not needed.

#### Syntax

    void closeResultSet(
       ResultSet *resultSet);

| Parameter   | Description                                                                                                                                                                                          |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resultSet` | The result set to be closed; may be a result of getResultSet(), executeQuery(), or getCursor() calls on the current statement, or by a getCursor() call of another result set on the same statement. |

### 13.30.3 closeStream()

Closes the stream specified by the parameter `stream`.

#### Syntax

    void closeStream(
       Stream *stream);

| Parameter | Description              |
|:----------|:-------------------------|
| `stream`  | The stream to be closed. |

### 13.30.4 disableCaching()

Disables statement caching. Used if a user wants to destroy a statement instead of caching it. Effective only if statement caching is enabled.

#### Syntax

    void disableCaching();

### 13.30.5 execute()

Executes an SQL statement that may return either a result set or an update count. The statement may have read-able streams which may have to be written, in which case the results of the execution may not be readily available. The returned value `Status` is defined in Table 13-43.

If output streams are used for `OUT` bind variables, they must be completely read in order. The getCurrentStreamParam() method would indicate which stream must be read. Similarly, getCurrentIteration() would indicate the iteration for which data is available.

| Syntax                                           | Description                                        |
|:-------------------------------------------------|:---------------------------------------------------|
| `Status execute(`<br>`   const string &sql="");` | Executes the SQL Statement.                        |
| `Status execute(`<br>`   const UString &sql);`   | Executes the SQL Statement; globalization enabled. |

| Parameter | Description                                                                                                                               |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------|
| `sql`     | The SQL statement to be executed. This can be `NULL` if the executeArrayUpdate() method was used to associate the sql with the statement. |

### 13.30.6 executeArrayUpdate()

Executes insert/update/delete statements which use only the setDataBuffer() or stream interface for bind parameters. The bind parameters must be arrays of size `arrayLength` parameter. The statement may have writable streams which may have to be written. The returned value `Status` is defined in Table 13-43.

If output streams are used for `OUT` bind variables, they must be completely read in order. The getCurrentStreamParam() method would indicate which stream must be read. Similarly, getCurrentIteration() would indicate the iteration for which data is available.

Note that you cannot perform array executes for queries or callable statements.

#### Syntax

    Status executeArrayUpdate(
       unsigned int arrayLength);

| Parameter     | Description                                                       |
|:--------------|:------------------------------------------------------------------|
| `arrayLength` | The number of elements provided in each buffer of bind variables. |

### 13.30.7 executeQuery()

Runs a SQL statement that returns a `ResultSet`. Should not be called for a statement which is not a query, has streamed parameters. Returns a `ResultSet` that contains the data produced by the query.

| Syntax                                                    | Description                                                                   |
|:----------------------------------------------------------|:------------------------------------------------------------------------------|
| `ResultSet* executeQuery(`<br>`   const string &sql="");` | Executes the SQL Statement that returns a `ResultSet`.                        |
| `ResultSet* executeQuery(`<br>`   const UString &sql);`   | Executes the SQL Statement that returns a `ResultSet;` globalization enabled. |

| Parameter | Description                                                                                                                               |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------|
| `sql`     | The SQL statement to be executed. This can be `NULL` if the executeArrayUpdate() method was used to associate the sql with the statement. |

### 13.30.8 executeUpdate()

Executes a non-query statement such as a SQL `INSERT`, `UPDATE`, `DELETE` statement, a DDL statement such as `CREATE`/`ALTER` and so on, or a stored procedure call. Returns either the row count for `INSERT`, `UPDATE` or `DELETE` or `0` for SQL statements that return nothing.

If the number of rows processed as a result of this call exceeds `UB4MAXVAL`, it may throw an exception. In such scenarios, use execute() instead, followed by getUb8RowCount() to obtain the number of rows processed.

| Syntax                                                       | Description                                            |
|:-------------------------------------------------------------|:-------------------------------------------------------|
| `unsigned int executeUpdate(`<br>`   const string &sql="");` | Executes a non-query statement.                        |
| `unsigned int executeUpdate(`<br>`   const UString &sql);`   | Executes a non-query statement; globalization enabled. |

| Parameter | Description                                                                                                                               |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------|
| `sql`     | The SQL statement to be executed. This can be `NULL` if the executeArrayUpdate() method was used to associate the sql with the statement. |

### 13.30.9 getAutoCommit()

Returns the current auto-commit state.

#### Syntax

    bool getAutoCommit() const;

### 13.30.10 getBatchErrorMode()

Returns the state of the batch error mode; `TRUE` if the batch error mode is enabled, `FALSE` otherwise.

#### Syntax

    bool getBatchErrorMode() const;

### 13.30.11 getBDouble()

Returns the value of an IEEE754 `DOUBLE` column, which has been defined as an `OUT` bind. If the value is SQL `NULL`, the result is `0`.

#### Syntax

    BDouble getBDouble(
       unsigned int paramIndex) = 0;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.12 getBfile()

Returns the value of a `BFILE` parameter as a `Bfile` object.

#### Syntax

    Bfile getBfile(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.13 getBFloat()

Gets the value of an IEEE754 `FLOAT` column, which has been defined as an `OUT` bind. If the value is SQL `NULL`, the result is `0`.

#### Syntax

    BFloat getBFloat(
       unsigned int paramIndex) = 0;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.14 getBlob()

Returns the value of a `BLOB` parameter as a `Blob`.

#### Syntax

    Blob getBlob(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.15 getBytes()

Returns the value of n SQL` BINARY` or `VARBINARY` parameter as `Bytes`; if the value is SQL `NULL`, the result is `NULL`.

#### Syntax

    Bytes getBytes(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.16 getCharSet()

Returns the characterset that is in effect for the specified parameter, as a `string`.

#### Syntax

    string getCharSet(
       unsigned int paramIndex) const;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.17 getCharSetUString()

Returns the character set that is in effect for the specified parameter, as a `UString`.

#### Syntax

    UString getCharSetUString(
       unsigned int paramIndex) const;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.18 getClob()

Get the value of a `CLOB` parameter as a `Clob`. Returns the parameter value.

#### Syntax

    Clob getClob(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.19 getConnection()

Returns the connection from which the `Statement` object was instantiated.

#### Syntax

    Connection* getConnection() const;

### 13.30.20 getCurrentIteration()

If the prepared statement has any output `Streams`, this method returns the current iteration of the statement that is being processed by OCCI. If this method is called after all the invocations in the set of iterations has been processed, it returns `0`. Returns the iteration number of the current iteration that is being processed. The first iteration is numbered `1` and so on. If the statement has finished execution, a `0` is returned.

#### Syntax

    unsigned int getCurrentIteration() const;

### 13.30.21 getCurrentStreamIteration()

Returns the current parameter stream for which data is available.

#### Syntax

    unsigned int getCurrentStreamIteration() const;

### 13.30.22 getCurrentStreamParam()

Returns the parameter index of the current output `Stream` parameter that must be written. If the prepared statement has any output `Stream` parameters, this method returns the parameter index of the current output `Stream` that must be written. If no output `Stream` must be written, or there are no output `Stream` parameters in the prepared statement, this method returns `0`.

#### Syntax

    unsigned int getCurrentStreamParam() const;

### 13.30.23 getCursor()

Gets the `REF` `CURSOR` value of an `OUT` parameter as a `ResultSet`. Data can be fetched from this result set. The `OUT` parameter must be registered as `CURSOR` with the registerOutParam() method. Returns a `ResultSet` for the `OUT` parameter value.

Note that if there are multiple `REF` `CURSORs` being returned due to a batched call, data from each cursor must be completely fetched before retrieving the next `REF` `CURSOR` and starting fetch on it.

#### Syntax

    ResultSet * getCursor(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.24 getDatabaseNCHARParam()

Returns whether data is in `NCHAR` character set or not.

#### Syntax

    bool getDatabaseNCHARParam(
       unsigned int paramIndex) const;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.25 getDate()

Get the value of a SQL `DATE` parameter as a `Date` object. Returns the parameter value; if the value is SQL `NULL`, the result is `NULL`.

#### Syntax

    Date getDate(
       unsigned int paramIndex) const;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.26 getDMLRowCounts()

Returns the row counts affected by each iteration of the current DML statement when it executes with multiple iterations.

Use this method in conjunction with getRowCountsOption() and setRowCountsOption().

#### Syntax

    vector<oraub8> getDMLRowCounts();

### 13.30.27 getDouble()

Get the value of a `DOUBLE` parameter as a C++ `double`. Returns the parameter value; if the value is SQL `NULL`, the result is 0.

#### Syntax

    double getDouble(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.28 getFloat()

Get the value of a `FLOAT` parameter as a C++ `float`. Returns the parameter value; if the value is SQL `NULL`, the result is `0`.

#### Syntax

    float getFloat(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.29 getInt()

Get the value of an `INTEGER` parameter as a C++ int. Returns the parameter value; if the value is SQL `NULL`, the result is `0`.

#### Syntax

    unsigned int getInt(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.30 getIntervalDS()

Get the value of a parameter as a `IntervalDS` object.

#### Syntax

    IntervalDS getIntervalDS(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.31 getIntervalYM()

Get the value of a parameter as a `IntervalYM` object.

#### Syntax

    IntervalYM getIntervalYM(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.32 getMaxIterations()

Gets the current limit on maximum number of iterations. Default is `1`. Returns the current maximum number of iterations.

#### Syntax

    unsigned int getMaxIterations() const;

### 13.30.33 getMaxParamSize()

The `maxParamSize` limit (in bytes) is the maximum amount of data sent or returned for any parameter value; it only applies to character and binary types. If the limit is exceeded, the excess data is silently discarded. Returns the current `max` parameter size limit.

#### Syntax

    unsigned int getMaxParamSize(
       unsigned int paramIndex) const;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.34 getNumber()

Gets the value of a `NUMERIC` parameter as a `Number` object. Returns the parameter value; if the value is SQL `NULL`, the result is `NULL`.

#### Syntax

    Number getNumber(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.35 getObject()

Gets the value of a parameter as a `PObject`. This method returns an `PObject` whose type corresponds to the SQL type that was registered for this parameter using registerOutParam(). Returns A `PObject` holding the `OUT` parameter value.

This method may be used to read database-specific, abstract data types.

#### Syntax

    PObject * getObject(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.36 getOCIStatement()

Get the OCI statement handle associated with the `Statement`.

#### Syntax

    OCIStmt * getOCIStatement() const;

### 13.30.37 getRef()

Get the value of a `REF` parameter as `RefAny`. Returns the parameter value.

#### Syntax

    RefAny getRef(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.38 getResultSet()

Returns the current result as a `ResultSet`.

#### Syntax

    ResultSet * getResultSet();

### 13.30.39 getRowCountsOption()

Determines if the DML row counts option is enabled.

If `TRUE`, DML statements can be executed to return the row counts for each iteration using the method getDMLRowCounts().

#### Syntax

    bool getRowCountsOption();

### 13.30.40 getRowid()

Get the `rowid` parameter value as a `Bytes`.

#### Syntax

    Bytes getRowid(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.41 getSQL()

Returns the current SQL string associated with the Statement object.

#### Syntax

    string getSQL() const;

### 13.30.42 getSQLUString()

Returns the current SQL `UString` associated with the Statement object; globalization enabled.

#### Syntax

    UString getSQLUString() const;

### 13.30.43 getStream()

Returns the value of the parameter as a stream.

#### Syntax

    Stream * getStream(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.44 getString()

Get the value of a `CHAR`, `VARCHAR`, or `LONGVARCHAR` parameter as an string. Returns the parameter value; if the value is SQL `NULL`, the result is empty string.

#### Syntax

    string getString(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.45 getTimestamp()

Get the value of a SQL `TIMESTAMP` parameter as a `Timestamp` object. Returns the parameter value; if the value is SQL `NULL`, the result is `NULL`

#### Syntax

    Timestamp getTimestamp(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.46 getUb8RowCount()

Returns the number of rows affected by the execution of a DML statement.

This method enables a return of a large number of rows than was possible before Oracle Database Release 12c.

#### Syntax

    oraub8 getUb8RowCount();

### 13.30.47 getUInt()

Get the value of a `BIGINT` parameter as a C++ unsigned int. Returns the parameter value; if the value is SQL `NULL`, the result is `0`.

#### Syntax

    unsigned int getUInt(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.48 getUpdateCount()

Returns the number of rows affected, if DML statement is executed.

Note: This method has been deprecated. Use `getUb8RowCount()` instead.

#### Syntax

    unsigned int getUpdateCount() const;

### 13.30.49 getUString()

Returns the value as a UString.

This method should be called only if the environment's character set is UTF16, or if `setCharset()` method has been called to explicitly retrieve UTF16 data.

#### Syntax

    UString getUString(
       unsigned int paramIndex);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.50 getVector()

Returns the column in the current position as a vector. The column at the position, specified by index, should be a collection type (`varray` or nested table). The SQL type of the elements in the collection should be compatible with the type of the vector.

| Syntax                                                                                                           | Description                                                                                                                                |
|:-----------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   std::vector<UString> &vect);` | Used for vectors of `UString Class`; globalization enabled.                                                                                |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<BDouble> &vect);`      | Used for `BDouble` vectors.                                                                                                                |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<BFile> &vect);`        | Used for vectors of [Bfile Class](bfile-class.md).                                                                                         |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<BFloat> &vect);`       | Used for `BFloat` vectors.                                                                                                                 |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Blob> &vect);`         | Used for vectors of [Blob Class](blob-class.md).                                                                                           |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Bytes> &vect); `       | Used for vectors of [Bytes Class](bytes-class.md).                                                                                         |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Clob> &vect);`         | Used for `Clob` vectors.                                                                                                                   |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Date> &vect);`         | Used for vectors of [Date Class](date-class.md).                                                                                           |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<double> &vect);`       | Used for vectors of `double Class.`                                                                                                        |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<float> &vect);`        | Used for vectors of `float Class.`                                                                                                         |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<int> &vect);`          | Used for vectors of `int Class.`                                                                                                           |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<IntervalDS> &vect);`   | Used for vectors of [IntervalDS Class](intervalds-class.md).                                                                               |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<IntervalYM> &vect);`   | Used for vectors of [IntervalYM Class](intervalym-class.md).                                                                               |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Number> &vect);`       | Used for vectors of [Number Class](number-class.md).                                                                                       |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<RefAny> &vect);`       | Used for vectors of [RefAny Class](refany-class.md).                                                                                       |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<string> &vect);`       | Used for vectors of `string Class.`                                                                                                        |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<T *> &vect);`          | Intended for use on platforms where partial ordering of function templates is supported.                                                   |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<T> &vect);`            | Intended for use on platforms where partial ordering of function templates is not supported, such as Windows NT and z/OS. For `OUT` binds. |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Timestamp> &vect);`    | Used for vectors of [Timestamp Class](timestamp-class.md).                                                                                 |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<u <Ref<T> > &vect);`   | Available only on platforms where partial ordering of function templates is supported.                                                     |
| `void getVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<unsigned int> &vect);` | Used for on vectors of `unsigned int Class.`                                                                                               |

| Parameter    | Description                                                                          |
|:-------------|:-------------------------------------------------------------------------------------|
| `stmt`       | The statement.                                                                       |
| `paramIndex` | Parameter index.                                                                     |
| `vect`       | Reference to the vector (`OUT` parameter) into which the values should be retrieved. |

### 13.30.51 getVectorOfRefs()

This method returns the column in the current position as a vector of `REF`s. The column should be a collection type (varray or nested table) of `REF`s. Used with `OUT` binds.

#### Syntax

    void getVectorOfRefs(
       Statement *stmt,
       unsigned int colIndex,
       vector< Ref<T> > &vect);

| Parameter  | Description                                                                                                                                                       |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `stmt`     | The statement object.                                                                                                                                             |
| `colIndex` | Column index; first column is 1, second is 2, and so on.                                                                                                          |
| `vect`     | The reference to the vector of `REF`s (`OUT` parameter). It is recommended to use `getVectorOfRefs()` instead of specialized `getVector()` function for `Ref<T>.` |

### 13.30.52 isNull()

An `OUT` parameter may have the value of SQL `NULL`; `isNull()` reports whether the last value read has this special value. Note that you must first call `ge`t`xxx``()` on a parameter to read its value and then call `isNull()` to see if the value was SQL `NULL`. Returns `TRUE` if the last parameter read was SQL `NULL`.

#### Syntax

    bool isNull(
       unsigned int paramIndex ) const;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.53 isTruncated()

This method checks whether the value of the parameter is truncated. If the value of the parameter is truncated, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isTruncated(
       unsigned int paramIndex) const;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.54 preTruncationLength()

Returns the actual length of the parameter before truncation.

#### Syntax

    int preTruncationLength(
       unsigned int paramIndex) const;

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |

### 13.30.55 registerOutParam()

This method registers the `type` of each `out` parameter of a PL/SQL stored procedure. Before executing a PL/SQL stored procedure, you must explicitly call this method to register the `type` of each `out` parameter. This method should be called for `out` parameters only. Use the `set``xxx``()` method for in/out parameters.

- When reading the value of an `out` parameter, you must use the `get``xxx``()` method that corresponds to the parameter's registered SQL type. For example, use `getInt `or `getNumber` when `OCCIINT` or `OCCINumber` is the type specified.

- If a PL/SQL stored procedure has an `out` parameter of `type` `ROWID`, the `type` specified in this method should be `OCCISTRING`. The value of the `out` parameter can then be retrieved by calling the `getString()` method.

- If a PL/SQL stored procedure has an in/out parameter of type `ROWID`, call the methods `setString()` and `getString()` to set the type and retrieve the value of the `IN`/`OUT` parameter.

| Syntax                                                                                                                                                                      | Description                                                                                                             |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| `void registerOutParam(`<br>`   unsigned int paramIndex,`<br>`   Type type,`<br>`   unsigned int maxSize=0,`<br>`   const string &sqltype="");`                             | Registers the `type` of each `out` parameter of a PL/SQL stored procedure.                                              |
| `void registerOutParam(`<br>`   unsigned int paramIndex,`<br>`   Type type,`<br>`   unsigned int maxSize,`<br>`   const string typName,`<br>`   const string &schName);`    | Registers the `type` of each `out` parameter of a PL/SQL stored procedure; `string` support.                            |
| `void registerOutParam(`<br>`   unsigned int paramIndex,`<br>`   Type type,`<br>`   unsigned int maxSize,`<br>`   const UString &typName,`<br>`   const UString &schName);` | Registers the `type` of each `out` parameter of a PL/SQL stored procedure; globalization enabled, or `UString` support. |

| Parameter    | Description                                                                                                                    |
|:-------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on.                                                                 |
| `type`       | SQL type code defined by `type`; only data types corresponding to OCCI data types such as `Date`, `Bytes`, and so on.          |
| `maxSize`    | The maximum size of the retrieved value. For data types of `OCCIBYTES` and `OCCISTRING`, `maxSize `should be greater than `0`. |
| `sqltype`    | The name of the type in the data base (used for types which have been created with `CREATE TYPE`).                             |
| `typName`    | The name of the type.                                                                                                          |
| `schName`    | The schema name.                                                                                                               |

### 13.30.56 setAutoCommit()

A `Statement` can be in auto-commit mode. In this case any statement executed is also automatically committed. By default, the auto-commit mode is turned-off.

#### Syntax

    void setAutoCommit(
       bool autoCommit);

| Parameter    | Description                                               |
|:-------------|:----------------------------------------------------------|
| `autoCommit` | `TRUE` enables auto-commit; `FALSE` disables auto-commit. |

### 13.30.57 setBatchErrorMode()

Enables or disables the batch error processing mode.

#### Syntax

    virtual void setBatchErrorMode(
       bool batchErrorMode);

| Parameter        | Description                                                                     |
|:-----------------|:--------------------------------------------------------------------------------|
| `batchErrorMode` | `TRUE` enables batch error processing; `FALSE` disables batch error processing. |

### 13.30.58 setBDouble()

Sets an IEEE754 double as a bind value to a `Statement` object at the position specified by `paramIndex` attribute.

#### Syntax

    void setBDouble(
       unsigned int paramIndex,
       const BDouble &dval);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `dval`       | The parameter value.                                           |

### 13.30.59 setBfile()

Sets a parameter to a `Bfile` value.

#### Syntax

    void setBfile(
       unsigned int paramIndex,
       const Bfile &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.60 setBFloat()

Sets an IEEE754 float as a bind value to a `Statement` object at the position specified by the `paramIndex` attribute.

#### Syntax

    void setBFloat(
       unsigned int paramIndex,
       const BFloat &fval);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `fval`       | The parameter value.                                           |

### 13.30.61 setBinaryStreamMode()

Defines that a column is to be returned as a binary stream.

| Syntax                                                                                                    | Description                                                                                                   |
|:----------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------|
| `void setBinaryStreamMode(`<br>`   unsigned int colIndex,`<br>`   unsigned int size);`                    | Sets column returned to be a binary stream.                                                                   |
| `void setBinaryStreamMode(`<br>`   unsigned int colIndex,`<br>`   unsigned int size`<br>`   bool inArg);` | Sets column returned to be a binary stream; used with PL/SQL `IN` or `IN/OUT` arguments in the bind position. |

| Parameter  | Description                                                                                             |
|:-----------|:--------------------------------------------------------------------------------------------------------|
| `colIndex` | Column index; first column is 1, second is 2, and so on.                                                |
| `size`     | The amount of data to be read or returned as a binary `Stream`. This is limited to 32KB (32,768 bytes). |
| `inArg`    | Pass `TRUE` if the bind position is a PL/SQL `IN` or `IN/OUT` argument                                  |

### 13.30.62 setBlob()

Sets a parameter to a `Blob` value.

#### Syntax

    void setBlob(
       unsigned int paramIndex,
       const Blob &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.63 setBytes()

Sets a parameter to a `Bytes` array.

#### Syntax

    void setBytes(
       unsigned int paramIndex,
       const Bytes &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.64 setCharacterStreamMode()

Defines that a column is to be returned as a character stream.

| Syntax                                                                                                        | Description                                                                                                      |
|:--------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------|
| `void setCharacterStreamMode(`<br>`   unsigned int colIndex,`<br>`   unsigned int size);`                     | Sets column returned to be a character stream.                                                                   |
| `void setCharacterStreamMode(`<br>`   unsigned int colIndex,`<br>`   unsigned int size,`<br>`   bool inArg);` | Sets column returned to be a character stream; used with PL/SQL `IN` or `IN/OUT` arguments in the bind position. |

| Parameter  | Description                                                            |
|:-----------|:-----------------------------------------------------------------------|
| `colIndex` | Column index; first column is 1, second is 2, and so on.               |
| `size`     | The amount of data to be read or returned as a character `Stream`.     |
| `inArg`    | Pass `TRUE` if the bind position is a PL/SQL `IN` or `IN/OUT` argument |

### 13.30.65 setCharSet()

Overrides the default character set for the specified parameter. Data is assumed to be in the specified character set and is converted to database character set. For `OUT` binds, this specifies the character set to which database characters are converted to.

#### Syntax

    void setCharSet(
       unsigned int paramIndex,
       string &charSet);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `charSet`    | Selected character set, as a string.                           |

### 13.30.66 setCharSetUString()

Overrides the default character set for the specified parameter. Data is assumed to be in the specified character set and is converted to database character set. For `OUT` binds, this specifies the character set to which database characters are converted to.

#### Syntax

    void setCharSetUString(
       unsigned int paramIndex,
       const UString& charSet);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `charSet`    | Selected character set, as a `UString`.                        |

### 13.30.67 setClob()

Sets a parameter to a `Clob` value.

#### Syntax

    void setClob(
       unsigned int paramIndex,
       const Clob &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.68 setDate()

Sets a parameter to a `Date` value.

#### Syntax

    void setDate(
       unsigned int paramIndex,
       const Date &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.69 setDatabaseNCHARParam()

If the parameter is going to be inserted in a column that contains data in the database's `NCHAR` character set, then OCCI must be informed by passing a `TRUE` value. A `FALSE` can be passed to restore the dafault.Returns returns the character set that is in effect for the specified parameter.

#### Syntax

    void setDatabaseNCHARParam(
       unsigned int paramIndex,
       bool isNCHAR);

| Parameter    | Description                                                                                   |
|:-------------|:----------------------------------------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on.                                |
| `isNCHAR`    | `TRUE` if this parameter contains data in Database's `NCHAR` character set; `FALSE` otherwise |

### 13.30.70 setDataBuffer()

Specifies a data buffer where data would be available. Also used for `OUT` bind parameters of callable statements.

The` buffer` parameter is a pointer to a user allocated data buffer. The current length of data must be specified in the `length` parameter. The amount of data should not exceed the `size` parameter. Finally, `type` is the data type of the data.

Note that not all `types` can be supplied in the buffer. For example, all OCCI allocated types (such as `Bytes`, `Date` and so on) cannot be provided by the setDataBuffer() interface. Similarly, C++ Standard Library strings cannot be provided with the setDataBuffer() interface either. The `type` can be any of OCI data types such `VARCHAR2`, `CSTRING`, `CHARZ` and so on.

If setDataBuffer() is used to specify data for iterative or array executes, it should be called only once in the first iteration only. For subsequent iterations, OCCI would assume that data is at `buffer +(i*size)` location where `i` is the iteration number. Similarly the length of the data would be assumed to be at `(length+i).`

For more information on the version of this method that uses 32K `length` parameter, see [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md).

| Syntax                                                                                                                                                                                  | Description                                                                                                                        |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| `void setDataBuffer(`<br>`   unsigned int paramIndex,`<br>`   void *buffer,`<br>`   Type type,`<br>`   sb4 size,`<br>`   ub2 *length,`<br>`   sb2 *ind = NULL,`<br>`   ub2 *rc= NULL);` | Uses `ub2` `length` buffer. This limits `VARCHAR2` and `NVARCHAR2` length to `4,000` bytes, and `RAW` data types to `2,000` bytes. |
| `void setDataBuffer(`<br>`   unsigned int paramIndex,`<br>`   void *buffer,`<br>`   Type type,`<br>`   sb4 size,`<br>`   ub4 *length,`<br>`   sb2 *ind = NULL,`<br>`   ub2 *rc= NULL);` | Uses `ub4` `length` buffer (32K). This increases the length of `VARCHAR2`, `NVARCHAR2` and `RAW` data types.                       |

| Parameter    | Description                                                                                                                                                                                                                                                                                                                                       |
|:-------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on.                                                                                                                                                                                                                                                                                    |
| `buffer`     | Pointer to user-allocated buffer. For iterative or array executes, it should have `numIterations()` size bytes in it. For array fetches, it should have `numRows` \* size bytes in it. For gather or scatter binds and defines, this structure stores the address of `OCIIOVec` and the number of `OCIIOVec` elements that start at that address. |
| `type`       | Type of the data that is provided (or retrieved) in the buffer.                                                                                                                                                                                                                                                                                   |
| `size`       | Size of the data buffer; for iterative and array executes, it is the size of each element of the data items. For gather or scatter binds and defines, it is the size of the `OCIIOVecArray` to which the `buffer` points; the `mode` must be set to `IOVEC`.                                                                                      |
| `length`     | Pointer to the length of data in the buffer; for iterative and array executes, it should be an array of length data for each buffer element; the size of the array should be equal to `arrayLength()`.                                                                                                                                            |
| `ind`        | Indicator. For iterative and array executes, an indicator for every buffer element.                                                                                                                                                                                                                                                               |
| `rc`         | Returns code; for iterative and array executes, a return code for every buffer element.                                                                                                                                                                                                                                                           |

### 13.30.71 setDataBufferArray()

Specifies an array of data buffers where data would be available for reading or writing. Used for `IN`, `OUT`, and` IN/OUT` bind parameters for stored procedures which read/write array parameters.

- A stored procedure can have an array of values for` IN`, `IN/OUT`, or `OUT` parameters. In this case, the parameter must be specified using the setDataBufferArray() method. The array is specified just as for the setDataBuffer() method for iterative or array executes, but the number of elements in the array is determined by `*arrayLength` parameter.

- For `OUT` and` IN/OUT` parameters, the maximum number of elements in the array is specified (and returned) by the `arraySize` parameter. The client must ensure that it has allocated size \*`arraySize` bytes for the `buffer`. For iterative prepared statements, the number of elements in the array is determined by the number of iterations, and for array executes the number of elements in the array is determined by the `arrayLength` parameter of the executeArrayUpdate() method. However, for array parameters of stored procedures, the number of elements in the array must be specified in the `arrayLength `parameter of the setDataBufferArray() method because each parameter may have a different size array.

- This is different from prepared statements where for iterative and array executes, the number of elements in the array for each parameter is the same and is determined by the number of iterations of the statement, but a callable statement is executed only once, and each of its parameter can be a varying length array with possibly a different length.

- For more information on the version of this method that uses 32K `elementLength` parameter, see [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md).

| Syntax                                                                                                                                                                                                                                                       | Description                                                                                                                               |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------|
| `void setDataBufferArray(`<br>`   unsigned int paramIndex,`<br>`   void *buffer,`<br>`   Type type,`<br>`   ub4 arraySize,`<br>`   ub4 *arrayLength,`<br>`   sb4 elementSize,`<br>`   ub2 *elementLength,`<br>`   sb2 *ind = NULL,`<br>`   ub2 *rc = NULL);` | Uses `ub2` `elementLength` buffer. This limits `VARCHAR2` and `NVARCHAR2` length to `4,000` bytes, and `RAW` data types to `2,000` bytes. |
| `void setDataBufferArray(`<br>`  unsigned int paramIndex,`<br>`  void *buffer,`<br>`  Type type,`<br>`  ub4 arraySize,`<br>`  ub4 *arrayLength,`<br>`  sb4 elementSize,`<br>`  ub4 *elementLength,`<br>`  sb2 *ind = NULL,`<br>`  ub2 *rc = NULL);`          | Uses `ub4` `elementLength` buffer (32K). This increases the length of `VARCHAR2`, `NVARCHAR2` and `RAW` data types.                       |

| Parameter       | Description                                                                                                                                                                                                                                           |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `paramIndex`    | Parameter index; first parameter is 1, second is 2, and so on.                                                                                                                                                                                        |
| `buffer`        | Pointer to user-allocated buffer. It should have `size* arraySize` bytes in it. For gather or scatter binds and defines, this structure stores the address of `OCIIOVec` and the number of `OCIIOVec` elements that start at that address.            |
| `type`          | Type of the data that is provided (or retrieved) in the buffer.                                                                                                                                                                                       |
| `arraySize`     | Maximum number of elements in the array.                                                                                                                                                                                                              |
| `arrayLength`   | Pointer to number of current elements in the array.                                                                                                                                                                                                   |
| `elementSize`   | Size of the data buffer for each element. For iterative and array executes, it is the size of each element of the data items. When using gather or scatter binds and defines, it is the size of the `OCIIOVecArray`; the mode must be set to `IOVEC`. |
| `elementLemgth` | Pointer to an array of lengths. `elementLength[i]` has the current length of the `i`th element of the array.                                                                                                                                          |
| `ind`           | Pointer to an array of indicators. An indicator for every buffer element.                                                                                                                                                                             |
| `rcs`           | Pointer to an array of return codes.                                                                                                                                                                                                                  |

### 13.30.72 setDouble()

Sets a parameter to a C++ double value.

#### Syntax

    void setDouble(
       unsigned int paramIndex,
       double val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.73 setErrorOnNull()

Enables/disables exceptions for reading of `NULL` values on paramIndex parameter of the statement. If exceptions are enabled, calling a `get``xxx``()` on` paramIndex` parameter would result in an `SQLException` if the parameter value is `NULL`. This call can also be used to disable exceptions.

#### Syntax

    void setErrorOnNull(
       unsigned int paramIndex,
       bool causeException);

| Parameter        | Description                                                    |
|:-----------------|:---------------------------------------------------------------|
| `paramIndex`     | Parameter index; first parameter is 1, second is 2, and so on. |
| `causeException` | Enable exceptions if `TRUE`. Disable if `FALSE`.               |

### 13.30.74 setErrorOnTruncate()

This method enables/disables exceptions when truncation occurs.

#### Syntax

    void setErrorOnTruncate(
       unsigned int paramIndex,
       bool causeException);

| Parameter        | Description                                                    |
|:-----------------|:---------------------------------------------------------------|
| `paramIndex`     | Parameter index; first parameter is 1, second is 2, and so on. |
| `causeException` | Enable exceptions if `TRUE`. Disable if `FALSE`.               |

### 13.30.75 setFloat()

Sets a parameter to a C++ float value.

#### Syntax

    void setFloat(
       unsigned int paramIndex,
       float val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.76 setInt()

Sets a parameter to a C++ int value.

#### Syntax

    void setInt(
       unsigned int paramIndex,
       int val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.77 setIntervalDS()

Sets a parameter to a `IntervalDS` value.

#### Syntax

    void setIntervalDS(
       unsigned int paramIndex,
       const IntervalDS &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.78 setIntervalYM()

Sets a parameter to a `Interval` value.

#### Syntax

    void setIntervalYM(
       unsigned int paramIndex,
       const IntervalYM &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.79 setMaxIterations()

Sets the maximum number of invocations that are made for the DML statement. This must be called before any parameters are set on the prepared statement. The larger the iterations, the larger the numbers of parameters sent to the server in one round trip. However, a large number causes more memory to be reserved for all the parameters. Note that this is just the maximum limit. Actual number of iterations depends on the number of calls to addIteration().

#### Syntax

    void setMaxIterations(
       unsigned int maxIterations);

| Parameter       | Description                                             |
|:----------------|:--------------------------------------------------------|
| `maxIterations` | Maximum number of iterations allowed on this statement. |

### 13.30.80 setMaxParamSize()

This method sets the maximum amount of data to be sent or received for the specified parameter. It only applies to character and binary data. If the maximum amount is exceeded, the excess data is discarded. This method can be very useful when working with a `LONG` column. It can be used to truncate the `LONG` column by reading or writing it into a string or `Bytes` data type.

If the getSQL() or setBytes() method has been called to bind a value to an `IN`/`OUT` parameter of a PL/SQL procedure, and the size of the `OUT` value is expected to be greater than the size of the `IN` value, then setMaxParamSize() should be called.

#### Syntax

    void setMaxParamSize(
       unsigned int paramIndex,
       unsigned int maxSize);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `maxSize`    | The new maximum parameter size limit; must be \>0.             |

### 13.30.81 setNull()

Sets a parameter to SQL `NULL`. Note that you must specify the parameter's SQL type.

| Syntax                                                                                                                                     | Description                                                                                                                                                                                                 |
|:-------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `void setNull(`<br>`   unsigned int paramIndex,`<br>`   Type type);`                                                                       | Sets the value of a parameter to `NULL` using an object.                                                                                                                                                    |
| `void setNull(`<br>`   unsigned int paramIndex,`<br>`   Type type,`<br>`   const string &typeName,`<br>`   const string &schemaName = "")` | Sets the value of a parameter to `NULL` for object and collection types, `OCCIPOBJECT` and `OCCIVECTOR`. Uses the appropriate schema and type name of the object or collection type. Support for `string`.  |
| `void setNull(`<br>`   unsigned int paramIndex, `<br>`   Type type, `<br>`   UString &typeName, `<br>`   UString &schemaName);`            | Sets the value of a parameter to `NULL` for object and collection types, `OCCIPOBJECT` and `OCCIVECTOR`. Uses the appropriate schema and type name of the object or collection type. Support for `UString`. |

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `type`       | SQL type.                                                      |
| `typeName`   | Type name of the object or collection.                         |
| `schemaName` | Name of the schema where the object or collection is defined.  |

### 13.30.82 setNumber()

Sets a parameter to a `Number` value.

#### Syntax

    void setNumber(
       unsigned int paramIndex,
       const Number &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.83 setObject()

Sets the value of a parameter using an object; use the C++.lang equivalent objects for integral values. The OCCI specification specifies a standard mapping from C++ `Object` types to SQL types. The given parameter C++ object is converted to the corresponding SQL type before being sent to the database.

#### Syntax

    void setObject(
       unsigned int paramIndex,
       PObject* val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The object containing the input parameter value.               |
| `sqltyp`     | The SQL type name of the object to be set.                     |

### 13.30.84 setPrefetchMemorySize()

Sets the amount of memory that is used internally by OCCI to store data fetched during each round trip to the server. A value of `0` means that the amount of data fetched during the round trip is constrained by the `FetchRowCount` parameter. If both parameters are nonzero, the smaller of the two is used.

#### Syntax

    void setPrefetchMemorySize(
       unsigned int bytes);

| Parameter | Description                                                                  |
|:----------|:-----------------------------------------------------------------------------|
| `bytes`   | Number of bytes used for storing data fetched during each server round trip. |

### 13.30.85 setPrefetchRowCount()

Sets the number of rows that are fetched internally by OCCI during each round trip to the server. A value of `0` means that the amount of data fetched during the round trip is constrained by the `FetchMemorySize` parameter. If both parameters are nonzero, the smaller of the two is used. If both of these parameters are zero, row count internally defaults to `1` row and that is the value returned from the `getFetchRowCount()` method.

#### Syntax

    void setPrefetchRowCount(
       unsigned int rowCount);

| Parameter  | Description                                                |
|:-----------|:-----------------------------------------------------------|
| `rowCount` | Number of rows to fetch for each round trip to the server. |

### 13.30.86 setRef()

Sets the value of a parameter to a reference. A `Ref<T>` instance is implicitly converted to a `RefAny` object during this call.

| Syntax                                                                                                                                            | Description                                                                                                                                                                                             |
|:--------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `void setRef(`<br>`   unsigned int paramIndex,`<br>`   const RefAny &refAny); `                                                                   | Sets the value of a parameter to a reference.                                                                                                                                                           |
| `void setRef(`<br>`   unsigned int paramIndex,`<br>`   const RefAny &refAny,`<br>`   const string &typName,`<br>`   const string &schName = "");` | Sets the value of a parameter to a reference. If the `Statement` represents a callable PL/SQL method, pass the schema name and type name of the object represented by the `Ref`. Support for `string`.  |
| `void setRef(`<br>`   unsigned int paramIndex,`<br>`   const RefAny &refAny,`<br>`   const UString &typName,`<br>`   const UString &schName);`    | Sets the value of a parameter to a reference. If the `Statement` represents a callable PL/SQL method, pass the schema name and type name of the object represented by the `Ref`. Support for `UString`. |

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `refAny`     | The reference.                                                 |
| `typName`    | The type of the object \[optional\].                           |
| `schName`    | The schema where the object type is defined \[optional\].      |

### 13.30.87 setRowCountsOption()

Set `flag` to `TRUE` to enable return of DML row counts per iteration when invoking getDMLRowCounts().

This option should be set before the statement executes. By default, the DML row counts per iteration are not returned.

#### Syntax

    void setRowCountsOption(
       bool flag);

| Parameter | Description                                        |
|:----------|:---------------------------------------------------|
| `flag`    | `TRUE` to return DML row counts, `FALSE` otherwise |

### 13.30.88 setRowid()

Sets a `Rowid` bytes array for a bind position.

#### Syntax

    void setRowid(
       unsigned int paramIndex,
       const Bytes &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.89 setSQL()

A new SQL string can be associated with a `Statement` object using this call. Resources associated with the previous SQL statement are freed. In particular, a previously obtained result set is invalidated. If an empty SQL string, `""`, is used when the `Statement` is created, a `setSQL` method with the proper SQL string must be performed first.

#### Syntax

    void setSQL(
       const string &sql);

| Parameter | Description        |
|:----------|:-------------------|
| `sql`     | Any SQL statement. |

### 13.30.90 setSQLUString()

Associate an SQL statement with this object. Unicode support: the client `Environment` should be initialized in OCCIUTIF16 mode.

#### Syntax

    void setSQLUString(
       const UString &sql);

| Parameter | Description                                                                      |
|:----------|:---------------------------------------------------------------------------------|
| `sql`     | A SQL statement in same character set as the connection source of the statement. |

### 13.30.91 setString()

Sets a parameter for a specified index.

#### Syntax

    void setString(
       unsigned int paramIndex,
       const string &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.92 setTimestamp()

Sets a parameter to a `Timestamp` value.

#### Syntax

    void setTimestamp(
       unsigned int paramIndex,
       const Timestamp &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.93 setUInt()

Sets a parameter to a C++ unsigned int value.

#### Syntax

    void setUInt(
       unsigned int paramIndex,
       unsigned int val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.94 setUString()

Sets a parameter for a specified index; globalization enabled.

#### Syntax

    void setUString(
       unsigned int paramIndex,
       const UString &val);

| Parameter    | Description                                                    |
|:-------------|:---------------------------------------------------------------|
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on. |
| `val`        | The parameter value.                                           |

### 13.30.95 setVector()

Sets a parameter to a vector. This method is necessary when the type is a collection type, varrays or nested tables. The SQL Type of the elements in the collection should be compatible with the type of the vector. For example, if the collection is a varray of `VARCHAR2`, use `vector<string>.`

| Syntax                                                                                                                                                                                     | Description                                                                                                                                  |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector< T > &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`            | Intended for use on platforms where partial ordering of function templates is not supported, such as Windows NT and z/OS. Multibyte support. |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<T* > &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`            | Intended for use on platforms where partial ordering of function templates is supported. Multibyte support.                                  |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<BDouble> &vect`<br>`   const string &sqltype);`                                            | Sets a `BDouble` vector.                                                                                                                     |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Bfile> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`          | Sets a `const Bfile` vector; multibyte support.                                                                                              |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Bfile> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`        | Sets a `const BFile` vector; UTF16 support.                                                                                                  |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<BFloat> &vect`<br>`   const string &sqltype);`                                             | Sets a `BFloat `vector.                                                                                                                      |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Blob> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`           | Sets a `const Blob` vector; multibyte support.                                                                                               |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Blob> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`         | Sets a `const Blob` vector; UTF16 support.                                                                                                   |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Bytes> &vect,`<br>`   const string &sqltype); `                                            | Sets a `const Bytes` vector.                                                                                                                 |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Bytes> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`          | Sets a `const Bytes` vector; multibyte support.                                                                                              |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Bytes> &vect,`<br>`   const Ustring &schemaName,`<br>`   const Ustring &typeName); `       | Sets a `const Bytes` vector; UTF16 support.                                                                                                  |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Clob> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`           | Sets a `const Clob` vector; multibyte support.                                                                                               |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Clob> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`         | Sets a `const Clob` vector; UTF16 support.                                                                                                   |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Date> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`           | Sets a `const Date` vector; multibyte support.                                                                                               |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Date> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`         | Sets a `const Date` vector; UTF16 support.                                                                                                   |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<double> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`         | Sets a `const double` vector; multibyte support.                                                                                             |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<double> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`       | Sets a `const double` vector; UTF16 support.                                                                                                 |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<float> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`          | Sets a `const float` vector; multibyte support.                                                                                              |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<float> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`        | Sets a `const float` vector; UTF16 support.                                                                                                  |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<int> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`            | Sets a `const int` vector; multibyte support.                                                                                                |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<int> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`          | Sets a `const int` vector; UTF16 support.                                                                                                    |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<IntervalDS> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`     | Sets a `const IntervalDS` vector; multibyte support.                                                                                         |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<IntervalDS> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`   | Sets a `const IntervalDS` vector; UTF16 support.                                                                                             |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<IntervalYM> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`     | Sets a `const IntervalYM` vector; multibyte support.                                                                                         |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<IntervalYM> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`   | Sets a `const IntervalYM` vector; UTF16 support                                                                                              |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Number> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`         | Sets a `const Number` vector; multibyte support.                                                                                             |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Number> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`       | Sets a `const Number` vector; UTF16 support.                                                                                                 |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<RefAny> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`         | Sets a `const RefAny` vector; multibyte support.                                                                                             |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<RefAny> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`       | Sets a `const RefAny` vector; UTF16 support.                                                                                                 |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<string> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`         | Sets a `const string` vector; multibyte support.                                                                                             |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<string> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`       | Sets a `const string` vector; UTF16 support.                                                                                                 |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Timestamp> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`      | Sets a `const Timestamp` vector; multibyte support.                                                                                          |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Timestamp> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);`    | Sets a `const Timestamp` vector; UTF16 support.                                                                                              |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<unsigned int> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`   | Sets a `const unsigned int` vector; multibyte support.                                                                                       |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<unsigned int> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);` | Sets a `const unsigned int` vector; UTF16 support.                                                                                           |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Bfile> &vect,`<br>`   string &sqltype);`                                                         | Sets a `Bfile` vector.                                                                                                                       |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Blob> &vect,`<br>`   string &sqltype);`                                                          | Sets a `Blob` vector.                                                                                                                        |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Clob> &vect,`<br>`   string &sqltype);`                                                          | Sets a `Clob` vector.                                                                                                                        |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Date> &vect,`<br>`   string &sqltype);`                                                          | Sets a `Date` vector.                                                                                                                        |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<double> &vect,`<br>`   string &sqltype);`                                                        | Sets a `double` vector.                                                                                                                      |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<float> &vect,`<br>`   string &sqltype);`                                                         | Sets a `float` vector.                                                                                                                       |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<int> &vect,`<br>`   string &sqltype);`                                                           | Sets an `int` vector.                                                                                                                        |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<IntervalDS> &vect,`<br>`   string &sqltype);`                                                    | Sets an `IntervalDS` vector.                                                                                                                 |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<IntervalYM> &vect,`<br>`   string &sqltype);`                                                    | Sets an `IntervalYM` vector.                                                                                                                 |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Number> &vect,`<br>`   string &sqltype);`                                                        | Sets a `Number` vector.                                                                                                                      |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<RefAny> &vect,`<br>`   string &sqltype);`                                                        | Sets a `RefAn`y vector.                                                                                                                      |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<string> &vect,`<br>`   string &sqltype);`                                                        | Sets a `string` vector.                                                                                                                      |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Timestamp> &vect,`<br>`   string &sqltype);`                                                     | Sets a `Timestamp` vector.                                                                                                                   |
| `void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<unsigned int> &vect,`<br>`   string &sqltype);`                                                  | Sets an `unsigned int` vector.                                                                                                               |
| `template <class T>`<br>`void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector< T* > &vect,`<br>`   const string &sqltype);`                      | Intended for use on platforms where partial ordering of function templates is not supported.                                                 |
| `template <class T>`<br>`void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<T> &vect,`<br>`   const string &sqltype);`                         | Intended for use on platforms where partial ordering of function templates is supported.                                                     |
| `template <class T>`<br>`void setVector(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   vector<Ref<T>> &vect,`<br>`   string &sqltype);`                                | Available only on platforms where partial ordering of function templates is supported. setVectorOfRefs() can be used instead.                |

| Parameter    | Description                                                                                                                                                                       |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `stmt`       | Statement on which parameter is to be set.                                                                                                                                        |
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on.                                                                                                                    |
| `vect`       | The vector to be set.                                                                                                                                                             |
| `sqltype`    | Sqltype of the collection in the database. For example, `CREATE TYPE num_coll AS VARRAY OF NUMBER`. And the column/parameter type is `num_coll`. The sqltype would be` num_coll`. |
| `schemaName` | Name of the schema used                                                                                                                                                           |
| `typeName`   | Type                                                                                                                                                                              |

### 13.30.96 setVectorOfRefs()

Sets a parameter to a vector; is necessary when the type is a collection of `REF`s or nested tables of `REF`s.

| Syntax                                                                                                                                                                                                        | Description                                                                                                                     |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `template  <class T> void setVectorOfRefs(`<br>`   Statement *stmt, unsigned int paramIndex,`<br>`   const vector<Ref<T> > &vect,`<br>`   const string &sqltype);`                                            | Sets a parameter to a vector; is necessary when the type is a collection of `REF`s are varrays or nested tables of `REF`s.      |
| `template  <class T>  void setVectorOfRefs(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Ref<T> > &vect,`<br>`   const string &sqltype);`                                   | Used for multibyte support.                                                                                                     |
| `template  <class T> void setVectorOfRefs(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Ref<T>> &vect,`<br>`   const string &schemaName,`<br>`   const string &typeName);`  | Used for multibyte support.                                                                                                     |
| `template  <class T> void setVectorOfRefs(`<br>`   Statement *stmt,`<br>`   unsigned int paramIndex,`<br>`   const vector<Ref<T> &vect,`<br>`   const UString &schemaName,`<br>`   const UString &typeName);` | Used for UTF16 support on platforms where partial ordering of function templates is not supported, such as Windows NT and z/OS. |
| `template <class T>  void setVector(`<br>`Statement *stmt,`<br>`unsigned int paramIndex,`<br>`const vector<T* > &vect,`<br>`const UString &schemaName,`<br>`const UString &typeName);`                        | Used for UTF16 support on platforms where partial ordering of function templates is supported.                                  |

| Parameter    | Description                                                                                                         |
|:-------------|:--------------------------------------------------------------------------------------------------------------------|
| `stmt`       | Statement on which parameter is to be set.                                                                          |
| `paramIndex` | Parameter index; first parameter is 1, second is 2, and so on.                                                      |
| `vect`       | Vector to be set.                                                                                                   |
| `sqltype`    | Sqltype of the parameter or column. Use setVectorOfRefs() instead of specialized function setVector() for `Ref<T>`. |
| `schemaName` | Name of the schema used                                                                                             |
| `typeName`   | Type                                                                                                                |

### 13.30.97 status()

Returns the current status of the statement. Useful when there is streamed data to be written (or read). Other methods such as getCurrentStreamParam() and getCurrentIteration() can be called to find out the streamed parameter that must be written and the current iteration number for an iterative or array execute. The [status()](resultset-class.md)method can be called repeatedly to find out the status of the execution.

The returned value, Status, is defined in Table 13-43.

#### Syntax

    Status status() const;
