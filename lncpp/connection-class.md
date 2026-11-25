The `Connection` class represents a connection with a specific database. Inside the connection, SQL statements are executed and results are returned.

Table 13-11 Enumerated Values Used by Connection Class

| Attribute           | Options                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FailOverEventType` | • `FO_BEGIN` indicates that a lost connection has been detected; failover is starting.<br>• `FO_END` indicates that a failover completed successfully; the `Connection` is ready for use.<br>• `FO_ABORT` indicates that the failover was unsuccessful; it is not be attempted again.<br>• `FO_REAUTH` indicates that the user session has been reauthenticated.<br>• `FO_ERROR` indicates that a failover was unsuccessful; the application can handle the error and retry failover. |
| `FailOverType`      | • `FO_NONE` indicates that the user requested no protection for failover.<br>• `FO_SESSION` indicates that the user requested only session failover.<br>• `FO_SELECT` indicates that the use requested select failover.                                                                                                                                                                                                                                                               |
| `ProxyType`         | • `PROXY_DEFAULT `is the database user name.                                                                                                                                                                                                                                                                                                                                                                                                                                          |

Table 13-12 Summary of Connection Methods

| Method                         | Summary                                                                                                                                          |
|:-------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| changePassword()               | Changes the password for the current user.                                                                                                       |
| commit()                       | Commits changes made since the previous commit or rollback and release any database locks held by the session.                                   |
| createStatement()              | Creates a `Statement` object to execute SQL statements.                                                                                          |
| flushCache()                   | Flushes the object cache associated with the connection.                                                                                         |
| getClientCharSet()             | Returns the default client character set.                                                                                                        |
| getClientCharSetUString()      | Returns the globalization enabled client character set in `UString`.                                                                             |
| getClientNCHARCharSet()        | Returns the default client `NCHAR` character set.                                                                                                |
| getClientNCHARCharSetUString() | Returns the globalization enabled client `NCHAR` character set in `UString`.                                                                     |
| getClientVersion()             | Returns the version of the client used.                                                                                                          |
| getLTXID()                     | Returns logical transaction id that may be used in various calls of package `DBMS_APP_CONT`.                                                     |
| getMetaData()                  | Returns the metadata for an object accessible from the connection.                                                                               |
| getOCIServer()                 | Returns the OCI server context associated with the connection.                                                                                   |
| getOCIServiceContext()         | Returns the OCI service context associated with the connection.                                                                                  |
| getOCISession()                | Returns the OCI session context associated with the connection.                                                                                  |
| getServerVersion()             | Returns the version of the Oracle server used, as `string`.                                                                                      |
| getServerVersionUString()      | Returns the version of the Oracle server used, as a `UString`.                                                                                   |
| getStmtCacheSize()             | Retrieves the size of the statement cache.                                                                                                       |
| getTag()                       | Returns the tag associated with the connection.                                                                                                  |
| isCached()                     | Determines if the specified statement is cached.                                                                                                 |
| pinVectorOfRefs()              | Pins an entire vector of `Ref` objects into object cache in a single round trip; pinned objects are available through an `OUT` parameter vector. |
| postToSubscriptions()          | Posts notifications to subscriptions.                                                                                                            |
| readVectorOfBfiles()           | Reads multiple `Bfile`s in a single server round-trip.                                                                                           |
| readVectorOfBlobs()            | Reads multiple `Blob`s in a single server round-trip.                                                                                            |
| readVectorOfClobs()            | Reads multiple `Clob`s in a single server round-trip.                                                                                            |
| registerSubscriptions()        | Registers several `Subscription`s for notification.                                                                                              |
| rollback()                     | Rolls back all changes made since the previous commit or rollback and release any database locks held by the session.                            |
| setStmtCacheSize()             | Enables or disables statement caching.                                                                                                           |
| setTAFNotify()                 | Registers failover callback function on the `Connection` object.                                                                                 |
| terminateStatement()           | Closes a `Statement` object and free all resources associated with it.                                                                           |
| unregisterSubscription()       | Unregisters a `Subscription`, turns off its notifications.                                                                                       |
| writeVectorOfBlobs()           | Writes multiple `Blob`s in a single server round-trip.                                                                                           |
| writeVectorOfClobs()           | Writes multiple `Clob`s in a single server round-trip.                                                                                           |

### 13.10.1 changePassword()

Changes the password of the user currently connected to the database.

| Syntax                                                                                                                         | Description                                                                                                            |
|:-------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|
| `void changePassword(`<br>`   const string &user,`<br>`   const string &oldPassword,`<br>`   const string &newPassword)=0;`    | Changes the password of the user.                                                                                      |
| `void changePassword(`<br>`   const UString &user,`<br>`   const UString &oldPassword,`<br>`   const UString &newPassword)=0;` | Changes the password of the user (Unicode support). The client `Environment` should be initialized in OCCIUTIF16 mode. |

| Parameter     | Description                                   |
|:--------------|:----------------------------------------------|
| `user`        | The user currently connected to the database. |
| `oldPassword` | The current password of the user.             |
| `newPassword` | The new password of the user.                 |

### 13.10.2 commit()

Commits all changes made since the previous commit or rollback, and releases any database locks currently held by the session.

#### Syntax

    void commit()=0;

### 13.10.3 createStatement()

Creates a `Statement` object with the SQL statement specified.

Note that for the caching-enabled version of this method, the cache is initially searched for a statement with a matching `tag`, which is returned. If no match is found, the cache is searched again for a statement that matches the `sql` parameter, which is returned. If no match is found, a new statement with a `NULL` `tag` is created and returned. If the `sql` parameter is empty and the `tag` search fails, this call generates an `ERROR`.

Also note that non-caching versions of this method always create and return a new statement.

| Syntax                                                                                   | Description                                                                                                                                        |
|:-----------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `Statement* createStatement(`<br>`   const string &sql="")=0;`                           | Searches the cache for a specified SQL statement and returns it; if not found, creates a new statement.                                            |
| `Statement* createStatement(`<br>`   const string &sql,`<br>`   const string &tag)=0;`   | Searches the cache for a statement with a matching tag; if not found, creates a new statement with the specified SQL content.                      |
| `Statement* createStatement(`<br>`   const UString &sql)=0;`                             | Searches the cache for a specified SQL statement and returns it; if not found, creates a new statement. Globalization enabled.                     |
| `Statement* createStatement(`<br>`   const Ustring &sql,`<br>`   const Ustring &tag)=0;` | Searches the cache for a matching tag and returns it; if not found, creates a new statement with the specified SQL content. Globalization enabled. |

| Parameter | Description                                                                                                    |
|:----------|:---------------------------------------------------------------------------------------------------------------|
| `sql`     | The SQL string to be associated with the statement object.                                                     |
| `tag`     | The tag whose associated statement must be retrieved from the cache. Ignored if statement caching is disabled. |

### 13.10.4 flushCache()

Flushes the object cache associated with the connection.

#### Syntax

    void flushCache()=0;

### 13.10.5 getClientCharSet()

Returns the session's character set.

#### Syntax

    string getClientCharSet() const=0;

### 13.10.6 getClientCharSetUString()

Returns the globalization enabled client character set in `UString`.

#### Syntax

    UString getClientCharSetUString() const=0;

### 13.10.7 getClientNCHARCharSet()

Returns the session's `NCHAR` character set.

#### Syntax

    string getClientNCHARCharSet() const=0;

### 13.10.8 getClientNCHARCharSetUString()

Returns the globalization enabled client `NCHAR` character set in `UString`.

#### Syntax

    UString getClientNCHARCharSetUString() const=0;

### 13.10.9 getClientVersion()

Returns the version of the client library the application is using at run time.

This is used by applications to determine the version of the OCCI client at run time, and if the application uses several separate code paths that use several different client patchsets.

The values of parameters `majorVersion` and `minorVersion` use macros `OCCI_MAJOR_VERSION` and `OCCI_MINOR_VERSION`, respectively. These macros define the major and minor versions of the OCCI client library. Compares the versions returned.

#### Syntax

    void getClientVersion(
       int &majorVersion,
       int &minorVersion,
       int &updateNum,
       int &patchNumber,
       int &portUpdateNum)

| Parameter          | Description                                                         |
|:-------------------|:--------------------------------------------------------------------|
| `majorVersion`     | The major version of the client library.                            |
| `minorVersion`     | The minor version of the client library.                            |
| `updateNum`        | The update number.                                                  |
| `patchNumber`      | The number of the patch applied to the library.                     |
| `portUpdateNumber` | The number of the port-specific port update applied to the library. |

### 13.10.10 getLTXID()

Returns logical transaction id that may be used in various calls of package `DBMS_APP_CONT`.

#### Syntax

    Bytes getLTXID() const = 0

### 13.10.11 getMetaData()

Returns metadata for an object in the database.

| Syntax                                                                                                                  | Description                                                          |
|:------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------|
| `MetaData getMetaData(`<br>`   const string &object,`<br>`   MetaData::ParamType prmtyp=MetaData::PTYPE_UNK) const=0;`  | Returns metadata for an object in the database.                      |
| `MetaData getMetaData(`<br>`   const UString &object,`<br>`   MetaData::ParamType prmtyp=MetaData::PTYPE_UNK) const=0;` | Returns metadata for a globalization enabled object in the database. |
| `MetaData getMetaData(`<br>`   const RefAny &ref) const=0;`                                                             | Returns metadata for an object in the database through a reference.  |

| Parameter | Description                                                                                                                                     |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| object    | The SQL string to be associated with the statement object.                                                                                      |
| prmtyp    | The type of the schema object being described, as defined by the enumerated `ParamType` of the MetaData class, [Table 13-27](metadata-class.md) |
| ref       | A `REF` to the Type Descriptor Object (TDO) of the type to be described.                                                                        |

### 13.10.12 getOCIServer()

Returns the OCI server context associated with the connection.

#### Syntax

    OCIServer* getOCIServer() const=0;

### 13.10.13 getOCIServiceContext()

Returns the OCI service context associated with the connection.

#### Syntax

    OCISvcCtx* getOCIServiceContext() const=0;

### 13.10.14 getOCISession()

Returns the OCI session context associated with the connection.

#### Syntax

    OCISession* getOCISession() const=0;

### 13.10.15 getServerVersion()

Returns the version of the database server, as a `string`, used by the current `Connection` object. This can be used when an application uses several separate code paths and connects to several different server versions.

#### Syntax

    string getServerVersion() const;

### 13.10.16 getServerVersionUString()

Returns the version of the database server, as a `UString`, used by the current `Connection` object. This can be used when an application uses several separate code paths and connects to several different server versions.

#### Syntax

    UString getServerVersionUString() const;

### 13.10.17 getStmtCacheSize()

Retrieves the size of the statement cache.

#### Syntax

    unsigned int getStmtCacheSize() const=0;

### 13.10.18 getTag()

Returns the tag associated with the connection. Valid only for connections from a stateless connection pool.

#### Syntax

    string getTag() const=0;

### 13.10.19 isCached()

Determines if the specified statement is cached.

| Syntax                                                                       | Description                                                                                                                                                     |
|:-----------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bool isCached(`<br>`   const string &sql,`<br>`   const string &tag="")=0;` | Searches the cache for a statement with a matching tag. If the tag is not specified, the cache is searched for a matching SQL statement.                        |
| `bool isCached(`<br>`   const Ustring &sql,`<br>`   const Ustring &tag)=0;`  | Searches the cache for a statement with a matching tag. If the tag is not specified, the cache is searched for a matching SQL statement. Globalization enabled. |

| Parameter | Description                                                                                                    |
|:----------|:---------------------------------------------------------------------------------------------------------------|
| `sql`     | The SQL string to be associated with the statement object.                                                     |
| `tag`     | The tag whose associated statement must be retrieved from the cache. Ignored if statement caching is disabled. |

### 13.10.20 pinVectorOfRefs()

Pins an entire vector of `Ref` objects into object cache in a single round-trip. Pinned objects are available through an `OUT` parameter vector.

| Syntax                                                                                                                                                                                | Description                                                                                                                                                    |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `template <class T> void pinVectorOfRefs(`<br>`   const Connection *conn,`<br>`   vector <Ref<T>> & vect,`<br>`   vector <T*> &vectObj,`<br>`   LockOptions lockOpt=OCCI_LOCK_NONE);` | Returns the objects.                                                                                                                                           |
| `template <class T> void pinVectorOfRefs(`<br>`   const Connection *conn,`<br>`   vector <Ref<T>> & vect,`<br>`   LockOptions lockOpt=OCCI_LOCK_NONE);`                               | Does not explicitly return the objects; an application must dereference a particular `Ref` object by a `ptr()` call, which returns a previously pinned object. |

| Parameter | Description                                                                                                                                                            |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `conn`    | Connection                                                                                                                                                             |
| `vect`    | Vector of `Ref` objects that are pinned.                                                                                                                               |
| `vectObj` | Vector that contains objects after the pinning operation is complete; an `OUT` parameter.                                                                              |
| `lockOpt` | Lock option used during the pinning of the array, as defined by `LockOptions` in [Table 13-2](common-occi-constants.md). The only supported value is `OCCI_LOCK_NONE`. |

### 13.10.21 postToSubscriptions()

Posts notifications to subscriptions.

The `Subscription` object must have a valid subscription name, and the namespace should be set to `NS_ANONYMOUS`. The payload must be set before invoking this call; otherwise, the payload is assumed to be `NULL` and is not delivered.

The caller has to preserve the payload until the posting call is complete. This call provides a best-effort guarantee; a notification is sent to registered clients at most once.This call is primarily used for light-weight notification and is useful for dealing with several system events. If the application needs more rigid guarantees, it can use the Oracle Database Advanced Queuing functionality.

#### Syntax

    void postToSubscriptions(
       const vector<aq::Subscription>& sub)=0;

| Parameter | Description                                        |
|:----------|:---------------------------------------------------|
| `sub`     | The vector of subscriptions that receive postings. |

### 13.10.22 readVectorOfBfiles()

Reads multiple `Bfile`s in a single server round-trip. All `Bfile`s must be open for reading.

#### Syntax

    void readVectorOfBfiles(
       const Connection *conn,
       vector<Bfile> &vec,
       oraub8 *byteAmts,
       oraub8 *offsets,
       unsigned char *buffers[],
       oraub8 *bufferLengths);

| Parameter       | Description                                                                                                                                 |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `conn`          | Connection.                                                                                                                                 |
| `vec`           | Vector of `Bfile` objects; each `Bfile` must be open for reading.                                                                           |
| `byteAmts`      | Array of amount of bytes to read from the individual `Bfile`s. The actual number of bytes read from each `Bfile` is returned in this array. |
| `offsets`       | Array of offsets, starting position where reading from the `Bfile`s starts.                                                                 |
| `buffers`       | Array of pointers to buffers into which the data is read.                                                                                   |
| `bufferLengths` | Array of sizes of each buffer, in bytes.                                                                                                    |

### 13.10.23 readVectorOfBlobs()

Reads multiple `BLOB`s in a single server round-trip.

#### Syntax

    void readVectorOfBlobs(
       const Connection *conn,
       vector<Blob> &vec,
       oraub8 *byteAmts,
       oraub8 *offsets,
       unsigned char *buffers[],
       oraub8 *bufferLengths);

| Parameter       | Description                                                                                                                               |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------|
| `conn`          | Connection.                                                                                                                               |
| `vec`           | Vector of `Blob` objects.                                                                                                                 |
| `byteAmts`      | Array of amount of bytes to read from the individual `Blob`s. The actual number of bytes read from each `Blob` is returned in this array. |
| `offsets`       | Array of offsets, starting position where reading from the `Blob`s starts.                                                                |
| `buffers`       | Array of pointers to buffers into which the data is read.                                                                                 |
| `bufferLengths` | Array of sizes of each buffer, in bytes.                                                                                                  |

### 13.10.24 readVectorOfClobs()

Reads multiple `Clob`s in a single server round-trip. All `Clob`s should be in the same characterset form and belong to the same characterset ID.

| Syntax                                                                                                                                                                                                                                 | Description                                                                                |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------|
| `void readVectorOfClobs(`<br>`   const Connection *conn,`<br>`   vector<Clob> &vec,`<br>`   oraub8 *byteAmts, `<br>`   araub8 *charAmts,`<br>`   oraub8 *offsets, `<br>`   unsigned char *buffers[], `<br>`   oraub8 *bufferLengths);` | General form of the method.                                                                |
| `void readVectorOfClobs(`<br>`   const Connection *conn,`<br>`   vector<Clob> &vec,`<br>`   oraub8 *byteAmts, `<br>`   araub8 *charAmts,`<br>`   oraub8 *offsets, `<br>`   utext *buffers[], `<br>`   oraub8 *bufferLengths);`         | Form of the method used with `utext` buffers, when data is in UTF16 characterset encoding. |

| Parameter       | Description                                                                                                                                                                         |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `conn`          | Connection.                                                                                                                                                                         |
| `vec`           | Vector of `Clob` objects.                                                                                                                                                           |
| `byteAmts`      | Array of amount of bytes to read from the individual `Clob`s. Only used if the `charAmts` is `NULL`, or `0` for any `Clob` index. Returns the number of bytes read for each `Clob`. |
| `charAmts`      | Array of amount of characters to read from individual `Clob`s. Returns the number of characters read for each `Clob`.                                                               |
| `offsets`       | Array of offsets, starting position where reading from the `Clob`s starts, in characters.                                                                                           |
| `buffers`       | Array of pointers to buffers into which the data is read.                                                                                                                           |
| `bufferLengths` | Array of sizes of each buffer, in bytes.                                                                                                                                            |

### 13.10.25 registerSubscriptions()

Registers `Subscription`s for notification.

New client processes and existing processes that restart after a shut down must register for all subscriptions of interest. If the client stays up during a server shut down and restart, this client continues to receive notifications for `DISCONNECTED` registrations, but not for `CONNECTED` registrations because they are lost during the server down time.

#### Syntax

    void registerSubscriptions(
       const vector<aq::Subscription>& sub)=0;

| Parameter | Description                                                   |
|:----------|:--------------------------------------------------------------|
| `sub`     | Vector of subscriptions that are registered for notification. |

### 13.10.26 rollback()

Drops all changes made since the previous commit or rollback, and releases any database locks currently held by the session.

#### Syntax

    void rollback()=0;

### 13.10.27 setStmtCacheSize()

Enables or disables statement caching. A nonzero value enables statement caching, with a cache of specified size. A zero value disables caching.

#### Syntax

    void setStmtCacheSize(
       unsigned int cacheSize)=0;

| Parameter   | Description                                    |
|:------------|:-----------------------------------------------|
| `cacheSize` | The maximum number of statements in the cache. |

### 13.10.28 setTAFNotify()

Registers the failover callback function on the `Connection` object for which failover is configured and must be detected.

The failover callback should return `OCCI_SUCCESS` to indicate that OCCI can continue with default processing. The failover event, `foEvent`, is defined in Table 13-11. When the `foEvent` is `FO_ERROR`, the callback function may return either `FO_RETRY` to indicate that failover must be attempted again, or `OCCI_SUCCESS` to end failover attempts.

#### Syntax

    void setTAFNotify(
       int (*notifyFn)(
          Environment *env,
          Connection *conn,
          void *ctx,
          FailOverType foType,
          FailOverEventType foEvent),
       void *ctxTAF)

| Parameter  | Description                                                                                                                                                     |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `notifyFn` | The user defined callback function invoked during failover events.                                                                                              |
| `env`      | `Environment` object from which the failing `Connection` was created.                                                                                           |
| `conn`     | The failing `Connection` on which the callback function is registered.                                                                                          |
| `ctx`      | Context supplied by the user when registering the callback.                                                                                                     |
| `foType`   | The configured `FailOverType`, values `FO_SESSION` or `FO_SELECT`, as defined in Table 13-11.                                                                   |
| foEvent    | Failover event type that is triggering the callback; the `FailOverEventType`, values `FO_BEGIN`, `FO_END`, `FO_ABORT` and `FO_ERROR` as defined in Table 13-11. |
| `ctxTAF`   | User context passed back to the callback function at invocation.                                                                                                |

### 13.10.29 terminateStatement()

Closes a `Statement` object.

| Syntax                                                                               | Description                                                                     |
|:-------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------|
| `void terminateStatement(`<br>`   Statement *stmt)=0;`                               | Closes a `Statement` object and frees all resources associated with it.         |
| `void terminateStatement(`<br>`   Statement *stmt,`<br>`   const string &tag)=0;`    | Releases statement back to the cache after adding an optional tag, a `string`.  |
| `void terminateStatement(`<br>`   Statement* stmt,`<br>`   const UString &tag) = 0;` | Releases statement back to the cache after adding an optional tag, a `UString`. |

| Parameter | Description                                                              |
|:----------|:-------------------------------------------------------------------------|
| `stmt`    | The `Statement` to be closed.                                            |
| `tag`     | The tag associated with the statement, either a `string` or a `UString`. |

### 13.10.30 unregisterSubscription()

Unregisters a `Subscription`, turning off its notifications.

#### Syntax

    void unregisterSubscription(
       const aq::Subscription& sub)=0;

| Parameter | Description                                       |
|:----------|:--------------------------------------------------|
| `sub`     | `Subscription` whose notifications is turned off. |

### 13.10.31 writeVectorOfBlobs()

Writes multiple `Blob`s in a single server round-trip.

#### Syntax

    void writeVectorOfBlobs(
       const Connection *conn,
       vector<Blob> &vec,
       oraub8 *byteAmts,
       oraub8 *offsets,
       unsigned char *buffers[],
       oraub8 *bufferLengths);

| Parameter       | Description                                                              |
|:----------------|:-------------------------------------------------------------------------|
| `conn`          | Connection.                                                              |
| `vec`           | Vector of `Blob` objects.                                                |
| `byteAmts`      | Array of amount of bytes to write to the individual `Blob`s.             |
| `offsets`       | Array of offsets, starting position where writing to the `Blob`s starts. |
| `buffers`       | Array of pointers to buffers from which the data is written.             |
| `bufferLengths` | Array of sizes of each buffer, in bytes.                                 |

### 13.10.32 writeVectorOfClobs()

Writes multiple `Clob`s in a single server round-trip. All `Clob`s should be in the same characterset form and belong to the same characterset ID.

| Syntax                                                                                                                                                                                                                                  | Description                                                                                |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------|
| `void writeVectorOfClobs(`<br>`   const Connection *conn,`<br>`   vector<Clob> &vec,`<br>`   oraub8 *byteAmts, `<br>`   araub8 *charAmts,`<br>`   oraub8 *offsets, `<br>`   unsigned char *buffers[], `<br>`   oraub8 *bufferLengths);` | General form of the method.                                                                |
| `void writeVectorOfClobs(`<br>`   const Connection *conn,`<br>`   vector<Clob> &vec,`<br>`   oraub8 *byteAmts, `<br>`   araub8 *charAmts,`<br>`   oraub8 *offsets, `<br>`   utext *buffers[], `<br>`   oraub8 *bufferLengths);`         | Form of the method used with `utext` buffers, when data is in UTF16 characterset encoding. |

| Parameter       | Description                                                                                                                                                                          |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `conn`          | Connection.                                                                                                                                                                          |
| `vec`           | Vector of `Clob` objects.                                                                                                                                                            |
| `byteAmts`      | Array of amount of bytes to write to the individual `Clob`s. Only used if the `charAmts` is `NULL` or `0` for any `Clob` index. Returns the number of bytes written for each `Clob`. |
| `charAmts`      | Array of amount of characters to write to individual `Clob`s. Returns the number of characters read for each `Clob`.                                                                 |
| `offsets`       | Array of offsets, starting position where writing to the `Clob`s starts, in characters.                                                                                              |
| `buffers`       | Array of pointers to buffers from which the data is written.                                                                                                                         |
| `bufferLengths` | Array of sizes of each buffer, in bytes.                                                                                                                                             |
